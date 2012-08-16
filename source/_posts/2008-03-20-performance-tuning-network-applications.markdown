---
author: admin
date: '2008-03-20 23:09:57'
layout: post
slug: performance-tuning-network-applications
status: publish
title: Performance Tuning Network Applications
wordpress_id: '137'
categories:
- C/C++
- Programming
---

Recently at work I spent a few weeks tuning a network service across
three platforms (Solaris, Linux, and AIX) to get within 10% of the
theoretical maximum throughput. In this short article, I'll walk through
the various tools I used to improve the performance of the application.

This application is very specialized in that the two machines are
connected directly through an ethernet switch. This means that the MTU
could easily be determined from each end of the link and the extra work
to determine the maximum segment size for the transit network (see [RFC
1191](http://tools.ietf.org/html/rfc1191)) was unnecessary. This also
made it very easy to watch the traffic between the two hosts as well as
the system calls they were using to transfer and receive the data.

Before I get into the steps I took to tune the service, I'd like to
introduce the tools used:

-   Truss: a tracing utility which displays system calls, dynamically
    loaded user level function calls, received signals, and incurred
    machine faults. This is available for many platforms, but I use it
    most on AIX.
-   DTrace/DTruss: a dynamic tracing compiler and tracing utility. This
    is an amazingly powerful tool from Sun, originally for Solaris but
    slowly spreading to other platforms. See Sun's [How To
    Guide](http://www.sun.com/software/solaris/howtoguides/dtracehowto.jsp).
-   strace: a dynamic tracing utility which displays systems calls and
    received signals under Linux.
-   mpstat: collects and displays performance statistics for all logical
    CPUs in the system.
-   prstat: iteratively examines all active processes on the system and
    reports statistics based on the selected output mode and sort order.
-   tcpdump: a utility for capturing network traffic.
-   Wireshark: a network protocol analyzer. It replaces the venerable
    Ethereal tool and allows you to either capture network traffic on
    demand or load a captured session for analysis. Find out more
    [here](http://www.wireshark.org).
-   gprof: a tool for profiling your code to determine where the
    performance bottle-necks are. See the
    [manual](http://www.gnu.org/software/binutils/manual/gprof-2.9.1/html_mono/gprof.html)
    for more information.
-   c++filt: a tool for demangling C++ method names. It is part of the
    [GNU binutils package](http://directory.fsf.org/project/binutils/).

Since I already had the service up and running, I simply ran the two
components and captured the traffic between them using tcpdump. While
the processes were running, I also used dtruss, truss, or strace
(depending on the platform) to capture the system calls being made.
Since this is a network service, I focused on calls to `select`, `send`,
and `recv`.

    13455/15:   2143177    2994      4 pollsys(0xFFFFFD7EBADDB910, 0x1, 0xFFFFFD7EBADDBA30) = 1 0
    13455/15:   2143180       5      0 pollsys(0xFFFFFD7EBADDB8D0, 0x1, 0xFFFFFD7EBADDB9F0) = 1 0
    13455/15:   2143185       8      4 recvfrom(0x11, 0xB384A0, 0x10000)                    = 1416 0
    13455/15:   2143253       5      0 pollsys(0xFFFFFD7EBADDB8D0, 0x1, 0xFFFFFD7EBADDB9F0) = 0 0
    13455/15:   2143262      12      8 send(0x11, 0xB084D0, 0x14B8)                         = 5304 0
    13455/15:   2143268     365      4 pollsys(0xFFFFFD7EBADDB910, 0x1, 0xFFFFFD7EBADDBA30) = 1 0
    13455/15:   2143270       4      0 pollsys(0xFFFFFD7EBADDB8D0, 0x1, 0xFFFFFD7EBADDB9F0) = 1 0
    13455/15:   2143275       8      4 recvfrom(0x11, 0xB384A0, 0x10000)                    = 1416 0
    13455/15:   2143343       5      0 pollsys(0xFFFFFD7EBADDB8D0, 0x1, 0xFFFFFD7EBADDB9F0) = 0 0
    13455/15:   2143348       9      4 send(0x11, 0xB084D0, 0x14B8)                         = 5304 0
    13455/15:   2143353    1000      4 pollsys(0xFFFFFD7EBADDB910, 0x1, 0xFFFFFD7EBADDBA30) = 1 0

Looking at the results above you can see that `select` (`pollsys`) is
being called each time we need to send or receive data over the network.
Since the socket is non-blocking we can rely on the immediate return
when the outgoing socket buffer is full as well as when there is no data
available to read. By `select`ing at the very top of the receive loop we
can bundle multiple receive calls together, increasing the application's
throughput. Now the output looks like this:

    16712/9:     16202    1560      6 pollsys(0xFFFFFD7EBB9DB940, 0x1, 0xFFFFFD7EBB9DBA30) = 1 0
    16712/9:     16217      10      6 recv(0xB, 0x8A6450, 0x10000)                         = 1416 0
    16712/9:     16246       9      5 send(0xB, 0x876480, 0x540)                           = 1344 0
    16712/9:     16267       7      3 send(0xB, 0x876480, 0x540)                           = 1344 0
    16712/9:     16285       5      1 send(0xB, 0x876480, 0x540)                           = 1344 0
    16712/9:     16680      10      5 recv(0xB, 0x8A6450, 0x10000)                         = 1416 0
    16712/9:     16712      11      7 send(0xB, 0x876480, 0x540)                           = 1344 0
    16712/9:     16733       7      3 send(0xB, 0x876480, 0x540)                           = 1344 0
    16712/9:     16753       6      2 send(0xB, 0x876480, 0x540)                           = 1344 0
    16712/9:     16768       4      0 recv(0xB, 0x8A6450, 0x10000)                         = -1 Err#11

You'll notice that now we are able to process two requests and send out
six responses in the time that it previously took to call select and
receive a single request. When there is nothing left to read, the call
to `recv` returns errno 11 (`EAGAIN`). This change made the single
biggest performance impact on the code. I also changed the calls
`recvfrom` to `recv` since the application did not make use of the
foreign address.

At this point the performance was much better but I noticed that under
heavy load the sending socket would block as the ratio of requests to
responses was 1:3. As this was a UDP application, having the sending
buffers fill up seemed strange as we assumed that additional packets
would simply be dropped on the floor.

On the server, I checked the UDP socket buffer size using `ndd` (this
was under Solaris. For AIX the command is `no` and for Linux the command
is `sysctl`).

The following code was added to the socket initialize (minus the error
handling) to ensure that the socket buffers were large enough.

    unsigned size = 1024 * 1024; // 1MB
    int ret = setsockopt(desc, SOL_SOCKET, SO_SNDBUF, &size, sizeof(size));
        ret = setsockopt(desc, SOL_SOCKET, SO_RCVBUF, &size, sizeof(size));

Now that the application was performing acceptably I decided to run it
under the profiler. This turned up the function which was adding
responses to the in-memory packet. It turned out that as responses were
being added to the packet, the headers were being recalculated each
time. I removed this unnecessary work and only made the calculations
right before the packet was sent. This improved performance a few
percentage points more.

By binding the network interrupts to a particular core and keeping the
sending thread off of that core we were able to eek out additional
performance from the application. To accomplish this, the application
allows the operator to specify which core(s) it should bind to using
`sched_setaffinity` (Linux) and `processor_bind` (Solaris). You can also
accomplish this using `taskset` (Linux) and pbind (Solaris) if you don't
wish to modify your application.

Looking at the network traffic with tcpdump, I saw that I could fit an
additional response in the response bundle packet if I reduced or
removed some of the items in the packet header. At this point the
analysis and tuning had gone on for a few weeks and we had a schedule to
meet. Since the performance was where we needed it, the application was
wrapped up and sent to quality assurance.

The single most important lesson I learned from this exercise was to use
non-blocking sockets to their fullest by continually calling
`recv`/`send` until the call would block and then using `select` to idle
the process until there is work to do.

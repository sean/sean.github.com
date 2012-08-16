---
author: admin
date: '2007-12-05 23:54:04'
layout: post
slug: advanced-ruby-studio
status: publish
title: Advanced Ruby Studio
wordpress_id: '127'
categories:
- Ruby
- Training
---

Back in July I attended the [Advanced Ruby
Studio](http://pragmaticstudio.com/ruby/) in Reston, VA. At the time I
had wanted to blog about it but my life suddenly became extremely busy
and I left my blog to languish for several months. To rectify that, I've
decided to write up this post providing an overview of the studio and my
impressions. The instructors for the three day course were [Dave
Thomas](http://pragdave.blogs.pragprog.com/pragdave/) and [Chad
Fowler](http://www.chadfowler.com/), two elite Ruby programmers (and
excellent teachers). While I wouldn't consider every topic covered
during the course advanced, I will say that there was a good mix of
intermediate and advanced content (and some of the advanced stuff was
really advanced!)

**Day 1**

-   Blocks, Procs, and Closures
-   Ruby Internals
-   Your Own Private Ruby
-   Design in a Dynamic Language
-   Types
-   Performance

**Day 2**

-   Metaprogramming
-   Creating Domain Specific Languages
-   Exotic Control Flow

**Day 3**

-   Library Organization
-   Distributed Programming
-   Debugging and Profiling
-   Ruby Extras

The first day we jumped right into blocks, procs, and closures. At
first, I thought this would be primarily review for me, but Dave and
Chad always provide those few extra tidbits which make it interesting.
From there we delved into the Ruby source code and learned how to
construct Ruby classes in C code and how to find our way around the Ruby
source. "Your Own Private Ruby" covered how to build Ruby (with specific
extensions) and how to manage multiple copies of Ruby on the same
machine. There were so many goodies in the "Design in a Dynamic
Language" portion of the day, I don't want to ruin the experience for
those who haven't attended yet. The second day of the studio was my
favorite, covering metaprogramming, DSLs, and control flow. There was so
much material that it's hard to do it justice in a short blog posting.
The exercises/labs were integral to understanding the material and I'm
glad the slides and source code were provided as they've turned out to
be useful references to refer back to. The third day was the 'choose
your own adventure' day where each of us voted on the topics for the
day. Even though there seemed to be some interest in JRuby on the first
day, that topic didn't make the short list for the final day.
Concurrency also fell by the way-side (though the slides provided
contained more than enough material on Ruby threads). Distributed
programming was largely review for me having played with DRb and the
Rinda tuple space, though the discussion of multicast and the ease of
dealing with binary protocol using pack/unpack was new and useful to me.
The primary message regarding library organization is to follow the
conventions set forth by Rails, though this was the portion of the class
where we packaged our own gem and served it up to classmates. Debugging
and profiling Ruby applications was partially review, having used
benchmark, ruby-debug, and profiler. Yet, I had never thought to debug
my Ruby applications using gdb even though I use it frequently at work
to debug C/C++ applications. [Mike](http://clarkware.com/cgi/blosxom)
and Nicole Clark really brought everything together. Their stewardship
of the event made it truly remarkable (as they seem to do every time).
Their goal is to ensure that every single attendee has a wonderful time
and they appear to be willing to do whatever it takes to make it so.
Next time you're at one of their events be sure to thank them for their
diligence. Overall, I found the course to be of tremendous value as it
got me thinking about even more ways to use Ruby. The insight that Chad
and Dave provided was integral to unlocking the reasoning behind the
design of the language. As is true with all of the [Pragmatic
Studio](http://pragmaticstudio.com/) offerings I've attended, this class
reinvigorated me and left me energized to tackle more projects. For
those who have never been to a Pragmatic Studio event before, one of the
best alumni benefits is the mailing list you're able to join afterwards
-- the signal to noise ratio is extremely high. Now, if only I could
convince my employer to send me four or five times a year.

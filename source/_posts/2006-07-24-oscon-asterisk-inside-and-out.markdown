---
author: admin
date: '2006-07-24 21:26:00'
layout: post
slug: oscon-asterisk-inside-and-out
status: publish
title: 'OSCON: Asterisk Inside and Out'
wordpress_id: '14'
categories:
- Conferences
- OSCON
- Telecom
- VoIP
---

This afternoon I attended [Asterisk Inside and
Out](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8936) by
[Brian Capouch](http://www.saintjoe.edu/faculty/specific/cs.html). His
presentation is available
[here](http://www.network-voice.com/oscon/tutorial.pdf) while all of the
[Asterisk](http://www.asterisk.org/) configuration files can be obtained
[here](http://www.network-voice.com/oscon/). The tutorial was based on
his forthcoming book, *Asterisk Inside and Out: Do-it-yourself Open
Source Telephony*, from Addison-Wesley.

Following the slides, Brian performed several demos which displayed the
power of Asterisk. He started with a simple ‘Hello World’ example where
the caller was played a short message. Next he demonstrated the server
calling you back (and playing a pre-recorded message). Then he called an
inside extension, an outside of the system (on to the PSTN via the FXO),
and called an inside extension from outside (via the PSTN and FXO).
After that he showed a ‘road warrior’ who ran a local instance of
Asterisk on their laptop which registered with the home office and then
called the office number of the ‘road warrior’ and the call was
automatically redirected to the laptop. Following that, he configured
the laptop as a remote office and dialed an extension at the ‘remote
office’ from the ‘local office’, which was properly routed through the
system. Finally, he demonstrated an intra-office transfer of an incoming
POTS call.

Asterisk appears to be an amazing application and there is quite a bit
more that I need to learn about it. It seems like it would be a fun
project to setup at home (if my wife will agree to it – which is
doubtful).

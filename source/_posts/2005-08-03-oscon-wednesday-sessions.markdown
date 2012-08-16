---
author: admin
date: '2005-08-03 17:31:43'
layout: post
slug: oscon-wednesday-sessions
status: publish
title: OSCON Wednesday Sessions
wordpress_id: '50'
categories:
- Conferences
- OSCON
- Programming
---

Here are my notes for the OSCON sessions I attended on Wednesday, except
for "Extracting Rails from Basecamp" where I essentially blogged it
while I was in the room. To save folks the trouble of clicking on the
"more" link if they're not interested, here is the list of talks I
attended (notes below):

-   [The Google Open Source
    Update](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6594)
-   [Yahoo! Web Services and Yahoo! Widgets (aka
    Konfabulator)](http://conferences.oreillynet.com/cs/os2005/view/e_sess/7548)
-   [Switching from CVS to Subversion: Case Studies in Migrating Your
    Team to a New
    Tool](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6750)
-   [How to Serve a Billion Requests a Day with
    Perl](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6647)
-   [Scalable Computing with
    MapReduce](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6614)

## The Google Open Source Update

Chris DiBona from Google (obviously) gave an interesting an amusing talk
on the use of open source software at Google. They used to use Redhat
Linux, now it's their own Frankenstein Linux creation. He talked mostly
about the Summer of Code program and how it's bring college students
into the Open Source community -- over 400 students were approved (419,
I think) and each one will get $4,500 ($500 up front, $4k at the end) if
they complete the project successfully (according to their project
mentor). I think this is a great program and Google should definitely
keep it up (they plan to). Chris believed that at least half of the
students will successfully complete their projects (some are already
ahead/done while others are behind).

## Yahoo! Web Services and Yahoo! Widgets (aka Konfabulator)

Jeffrey McManus from Yahoo (I think it was him, I arrived a couple of
minutes late) gave a great talk about Yahoo!'s web services and the new
Yahoo! widgets. Some of the web services available now are for Yahoo!
Maps, Yahoo! Shopping, Yahoo! Search/RSS, Yahoo! Music, Flickr (of
course) and Yahoo! Widgets (formerly Konfabulator). Some very cool demos
-- it looks like they really require the bare minimum from you to get
you up and running with their web services. See [Yahoo!
Developer](http://developer.yahoo.net) for more info.

## Switching from CVS to Subversion: Case Studies in Migrating Your Team
to a New Tool

Brian W. Fitzpatrick from CollabNet gave a talk on migrating from CVS
(and VSS) to SVN. This was not a technical discussion about SVN, just
some tips/tricks on how to plan the migration and how to be honest with
your users. The first half of the session was tips on how to do the
migration (again not technical, more of "Don't lie to you team and don't
make any lies of omission -- let them know of any features they'll be
losing", etc) while the second half of the session was devoted to case
studies like the Mono project, KDE, Apache, GCC and two secret
commercial companies.

## How to Serve a Billion Requests a Day with Perl

[Kevin Scaldeferri](http://kevin.scaldeferri.com/blog/) from Yahoo
Search Marketing gave an interesting session on writing scalable web
apps which can handle 1B requests/day. I need to copy over the notes
from my notebook, so I'll update this post a bit later (sorry!).

## Scalable Computing with MapReduce

Unfortunately, I had misread this session description and thought that
someone from Google was presenting on their Map/Reduce code. But Doug
Cutting of [Nutch](http://lucene.apache.org/nutch/) did a good job of
explaining the problems of searching/indexing 1B pages and how he
rewrote Nutch to overcome the 100M page limit he ran into.
Unfortunately, Doug's been having some networking issues with the
machines loaned to him by the Internet Archive so he hasn't yet shown
that the rewritten version of Nutch using Map/Reduce does in fact index
1B pages.

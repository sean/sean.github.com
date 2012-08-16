---
author: admin
date: '2005-08-02 07:13:31'
layout: post
slug: oscon-learning-ajax
status: publish
title: OSCON Learning Ajax
wordpress_id: '54'
categories:
- Conferences
- JavaScript
- OSCON
- Programming
---

I'm currently in [Alex
Russell's](http://conferences.oreillynet.com/cs/os2005/view/e_spkr/2179)
**sold out [Learning
Ajax](http://conferences.oreillynet.com/cs/os2005/view/e_sess/7094)**
tutorial at OSCON. He's generously made the latest version of the
[slides](http://dojotoolkit.org/~alex/oscon05.pdf) available online, as
well as all of the [demo
code](http://dojotoolkit.org/~alex/oscon/demos/). Below are my notes
from his excellent session. Since the slides are available online, I
won't go through my notes as thoroughly as I did for the Business for
Geeks tutorial. Instead, I'll simply highlight the items which Alex
stressed in his talk:

-   Only use Ajax when it can make the users' lives better! It may be
    fun to add gee-whiz effects to your web-app, but you must resist the
    temptation! Look at the bad name DHTML got from all of the websites
    which over-used it.
-   Whenever you run into trouble related to browser differences go to
    [Quirks Mode](http://www.quirksmode.org) first.
-   XMLHttp uses one of two available sockets, so if you have expensive
    jobs save them for last otherwise all of your little jobs will be
    blocked while two of the expensive jobs are working (or all of the
    little jobs will have to share a single queue if one socket is
    occupied with an expensive job).
-   Use synchronous XMLHttp requests sparingly -- i.e. only when there
    are dependancies where you must download the required item, for
    example some JavaScript, before doing anything else.
-   Using innerHtml is fast and easy, but not very flexible. Try to use
    XML and the DOM to selectively interact with nodes (don't forget
    that the server must declare it as "text/xml"!
-   Ajax style UIs should call the REST APIs your apps already expose
    (this is what [flickr](http://www.flickr.com) did)
-   What does "Grab the Chicken" mean? It's used at
    [JotSpot](http://www.jotspot.com) to discuss a neat feature the user
    discovers without being told about it. It comes from the Zelda
    Nintendo64 game where you're trying to get over this wall and can't
    figure it out, then you climb some nearby stairs and find a bunch of
    chickens -- by grabbing one and then walking down the stairs you're
    suddenly flying and can easily get over the wall.
-   Unfortunately, time ran out and Alex didn't get to any of his
    application demos or "The Future" slides -- which is a bummer
    because some of these things look really interesting.

TAGS: OSCON OSCON2005 Ajax XMLHttpRequest XMLHttp JavaScript XML DHTML

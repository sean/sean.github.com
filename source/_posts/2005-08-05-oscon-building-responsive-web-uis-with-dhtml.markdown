---
author: admin
date: '2005-08-05 09:37:00'
layout: post
slug: oscon-building-responsive-web-uis-with-dhtml
status: publish
title: OSCON Building Responsive Web UIs with DHTML
wordpress_id: '41'
categories:
- Conferences
- JavaScript
- OSCON
- Programming
---

Alex Russell gave an interesting talk this morning on [Building
Responsive Web UIs with
DHTML](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6985). My
notes are below. Updated Aug 6, 12:38: I fixed the errors in the post
pointed out by Alex Russell. BTW, he's an excelllent speaker, if he ever
gives a talk and you are able to go, I heartily recommend doing so.

## Building Responsive Web UIs with DHTML

[Alex Russell](http://www.dojotoolkit.org) Namespaces

-   you NOT are the only thing in the interpreter. deal
-   do nothing in global namesapce
-   declare the start of a namespace
-   Object.prototype.foo = ""; is EVIL
-   MyObject.prototype.foo = ""; is GOOD

Events: The old way

-   clients treated a dumb renderers
-   iframes make some partial content workable

Events the DHTML way

-   multiple models
-   onclick="foo()"
-   DOM2 style: attachEvent (or addEventListener for IE6)

Events the Dojo way

-   dojo.event.connect()
-   transparently handles multiple listeners
-   makes browser differences go away
-   builds in memory leak protection for IE
-   connects normal functions too, not just DOM nodes
-   dojo.event.connect(fooNode, "onclick", doFoo);
-   dojo.event.topic.subscribe("/foo", bar, "baz");
-   dojo.event.topic.publish("/foo", "arg1", "arg2");

AOP ... Say What?

-   Aspect oriented
-   does name method interception
-   advice types available past the default of after

I/O: the old way

-   full page refreshes
-   iframes provided some partial page refresh capability

I/O the DHTML way

-   XMLHttp requests
    -   sync or async
    -   browser capability detection code
    -   no file upload
    -   usability problems

-   iframes
    -   ugly, gratuitous hacks
    -   plays nice with forms

I/O the Dojo way

-   common interface to multiple "transports", incl. XMLHttp
-   single response and multi response API (ready for LivePage,
    mod\_pubsub, etc).

Packaging the old way

-   tags
-   absolute URLs
-   External CSS files and template systems
-   

Packaging the DHTML way

-   tags
-   no dependency tracking
-   no load ordering
-   no transparent optimization

Packaging the Dojo way

-   built in pkg system:
    -   integrates and is transparent with the build system
    -   yes, we make builds to optimize your code for you

-   dependency satisfaction at runtime or build time
-   partial builds can call source versions of this that aren't baked in
-   just use dojo.require()

Widget Reuse the old way

-   you build modularized PHP or \*SP
-   CSS moved to external files
-   behavioral code always copied
-   JS potentially moved to libraries/external files
-   No re-use previously available for DHTML

Widget Reuse the Dojo way

-   build with HTML and CSS fragements
-   amazingly fast to prototype
-   look and feel can change w/o changing JS class
-   automatic reuse:
    -   previously everything had to have unique IDS that you managed
    -   Dojo does that counting work for you

Demos

-   Corkboard (from JotSpot)
-   Turbo DbAdmin

Functional Testing

-   LiveTest -- testing the deployed application (part of the Neuvaux
    (sp?) project). Only in svn for neuvous (sp?)

Slides available [here](http://dojotoolkit.org/~alex/dhtml_webapps.pdf).

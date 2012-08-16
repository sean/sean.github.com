---
author: admin
date: '2005-08-04 09:23:00'
layout: post
slug: oscon-actionstep-an-oss-component-framework-for-flash
status: publish
title: OSCON ActionStep - An OSS Component Framework for Flash
wordpress_id: '46'
categories:
- Conferences
- OSCON
- Programming
- Ruby
---

Richard Kilmer (from [InfoEther](http://www.infoether.com/), right in my
backyard!) gave an amazing presentation/demo on
[ActionStep](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6713).
He even took the time late last night/ealry this morning to build a demo
with a Ruby on Rails back-end. Here are my notes from the session:

## ActionStep: OSS Component for Flash

Motivations:

-   cross-platform user-experience
-   full widget model
-   small core, plugin arch
-   themable at runtime
-   open source (like)
-   driven remotely by ruby

Why Flash?

-   proprietary but
-   published spec
-   pervasive runtime
-   good technology
    -   stack based
    -   ActionScript programmability
    -   Networking
    -   Animation Engine
    -   MTASC (open source ActionScript compiler)

State of Flash

-   Flash 7 (8 on 8/8/05)
-   ActionScript 2.0: ECMAScript (packages, classes, interfaces)
-   Components 2.0: AS 2.0 based, source w/IDE, remoting, themable
-   Flex (declarative, server oriented tech)

What's in a swf?

-   Library (movies, bitmaps, fonts, sounds, vector graphics). Flash
    IDE/swfmill can be used to build this.
-   Frames/Timeline
-   ActionScript bytecode. Use MTASC to compile it.
-   Components are hybrid -- use both vector graphics and ActionScript

Houston, we have a problem ...

-   In flash everything is a movie clip
-   sub-clips have access to the root's library, but other movie clips
    with their own libraries override the parent library!
-   the ActionScript bytecode is always shared across clips
-   if a plugin contains assets (library) it would override the root
    library (which was planned to contain the theme for the app), so the
    plugins would have to carry along their own copy of the theme.

Build a UI toolkit?

-   many existing examples are out there (MFC, Swing, SWT, WxWigets,
    etc)
-   chose NextStep \> OpenStep \> Cocoa
    -   Why? Because it is a published API (GNUStep open source impl
        available)
    -   Well thought through widget model: Views & Cells, Targets &
        Actions, Responder chain
    -   Multiple impls (Cocoa, GNUStep, etc)
    -   Inheritance has good delegation model
    -   Utilizes dynamic runtime features

Introducing ActionStep

-   ActionScript 2.0 implementation for writing RIA
-   Foundation and AppKit
-   Open Source (BSD license)
-   Direct port of OpenStep AppKit (NS\* classes)
-   Pure ActionScript 2.0 (MTASC compiled)
-   All components are drawn (isolated in theme)
-   Match method naming

ActionStep Status

-   pretty substantial API

Demo

-   many different types of components available (sliders, windows,
    buttons, calendar, textfields, split views, etc).
-   very easy to skin components
-   no bitmaps, everything is vector graphics in demo

Roadmap:

-   1.0 by end of year
    -   End of August for first alpha
    -   End of Oct for beta

-   Web stack integration
    -   Open source Flash-remoting + Ruby on Rails
    -   Dynamic serialized UI descriptors
    -   Target / Action, Delegates -\> controllers

Rails Integration with ActionStep example

-   views build up components
-   button clicks call methods back on controllers with params
-   controller sends data to the ActionStep view to render the data

Demo \#2

-   ActionStep with a Rails back-end (last minute demo hacked up late
    last night/early this morning! No previous experience with Rails,
    amazing)
-   Launches against webrick and a flash window appears with a listbox
    and button.
-   Button click calls back on Rails and prints results to console (not
    back to ActionStep just yet).
-   RIA bound to Rails. Working on bi-directional events

[ActionStep](http://www.actionstep.org) website. Slides will be posted
soon.

---
author: admin
date: '2008-01-15 23:05:57'
layout: post
slug: nscodernight-dc
status: publish
title: NSCoderNight DC
wordpress_id: '135'
categories:
- C/C++
- Programming
tags:
- cocoa programming macosx
---

Tonight I was able to attend [NSCoderNight
DC](http://nscodernight.com/?cat=6) in Tysons Corner, VA and finally met
[Jose Vazquez](http://greenmango.org/) in person. Unfortunately, turn
out is pretty spotty, with Jose being the only continuous attendee.
Despite it being just the two of us, I came away energized and started
playing around with the new APIs we spoke about: [Core
Audio](http://developer.apple.com/documentation/MusicAudio/Conceptual/CoreAudioOverview/Introduction/chapter_1_section_1.html#//apple_ref/doc/uid/TP40003577-CH1-SW1)/[AudioQueues](http://developer.apple.com/documentation/MusicAudio/Conceptual/AudioQueueProgrammingGuide/Introduction/chapter_1_section_1.html#//apple_ref/doc/uid/TP40005343-CH1-SW1)
and [Quartz
Composer](http://developer.apple.com/graphicsimaging/quartzcomposer/).

I was shocked when Jose explained that the Core Audio and AudioQueues
tools are all Carbon (i.e. plain C) instead of Cocoa. Mistakenly, I was
under the impression that Carbon had been officially deprecated by Apple
and that only Cocoa would be supported going forward. The
AudioQueueTools
(/Developer/Examples/CoreAudio/SimpleSDK/AudioQueueTools) example which
comes with the Apple Developer Tools shows how to create command-line
tools for recording and playing back sounds, but trying to integrate
this with you Cocoa application is a different story. Luckily, we found
this post on Mark Darlymple's blog which explains how to use [C
callbacks in
Objective-C](http://borkwarellc.wordpress.com/2007/09/13/c-callbacks-in-objc/).
I'm still playing around with this and also looking at the
[QuickTime](http://developer.apple.com/quicktime/) API support for
recording sound.

Quartz Composer is an amazingly cool app, that appears deceptively
simply to throw something together with. I was blown away by Jose's demo
of it, having never seen it before. The visual programming environment,
[Quartz Composer
Editor](http://developer.apple.com/graphicsimaging/quartz/quartzcomposer.html),
has a fairly straight-forward GUI and allows you to easily 'compose'
multiple processing units (a.k.a. patches) together into composition
while the view window displays what the composition will look like in
real-time. I'm definitely going to spend some time to go through the
examples (/Developer/Examples/Quartz Composer/Applications).

If you are free on a Tuesday night, be sure to stop by the [Tysons
Corner
Panera](http://maps.google.com/maps?f=q&hl=en&geocode=&time=&date=&ttype=&q=8365+Leesburg+Pike,+Vienna,+VA+22182+(Panera+Bread)&sll=38.878131,-77.278595&sspn=0.009689,0.0156&ie=UTF8&om=1&ll=38.931038,-77.230368&spn=0.043267,0.079479&z=14&iwloc=addr&source=embed)
from 7pm-9pm. I'm going to make every effort to attend regularly.

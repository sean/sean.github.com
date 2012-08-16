---
author: admin
date: '2006-05-17 16:39:00'
layout: post
slug: may-novarug-meeting
status: publish
title: May NovaRUG Meeting
wordpress_id: '20'
categories:
- Programming
- Ruby
- Telecom
---

Tonight [Rich Kilmer](http://richkilmer.blogs.com/) presented his
[Alph](http://alph.rubyforge.org/) [Ruby](http://www.ruby-lang.org/) to
[Flash](http://www.adobe.com/products/flashplayer/) bridge. I had
checked out Alph before (version 0.0.3 from 2004) but was unable to get
it working. Rich said that he’d place an updated copy up on
[RubyForge](http://rubyforge.org/projects/alph/) soon. The way to setup
the bridge looks slightly different in his new version:

    conn = Alph::ConnectionManager.new
    flash = Alph::FlashVM.new("id", conn)

Rich also had a demo with multiple bar charts which were dynamically
updated from the Ruby server when the user clicked on the ‘play’ button
in the Flash VM running in the browser. If he posts the code, I’ll add a
link to it. Basically the Flash code creates two movies within the root
movie and adds a text field to each along with a button which calls back
to the Ruby server. This Flash code is compiled with the
[MTASC](http://www.mtasc.org/) compiler to create the SWF which runs in
the Flash player (in the browser). The Ruby code uses the code I
mentioned above (in a separate thread) and then registers itself for
callbacks – when it is called back it injects the progress bar into the
running Flash movies (and twiddles with the text in the text fields,
also in the Flash movies). Alph is currently being used by
[InfoEther](http://www.infoether.com/)’s [indi](http://www.getindi.com/)
platform. In this case both the Flash client and the Ruby server run on
the same machine. After his talk, Rich mentioned the
[haXe](http://haxe.org/) and [Neko](http://nekovm.org/) projects from
Nicolas Cannasse of [Motion-Twin](http://www.motion-twin.com/). They
book look like very interesting projects and there are rumors that Ruby
is being ported to the Neko VM (so now we have Rite/YARV and others
working on a VM for Ruby – why can’t all of these folks work together?)
The next NovaRUG meeting will be at FGM in Reston, VA on June 28 – Xandy
will be presenting on [Rake](http://rake.rubyforge.org/). I’m definitely
looking forward to it.

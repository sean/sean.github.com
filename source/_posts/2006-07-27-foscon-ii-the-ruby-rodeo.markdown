---
author: admin
date: '2006-07-27 01:19:22'
layout: post
slug: foscon-ii-the-ruby-rodeo
status: publish
title: 'FOSCON II: The Ruby Rodeo'
wordpress_id: '10'
categories:
- Conferences
- OSCON
- Programming
- Ruby
---

Tonight I was able to attend [FOSCON II](http://oscamp.org/FOSCON) at
[FreeGeek](http://www.freegeek.org/) (I wish theyâ€™d hold FOSCON at the
OCC so it wasnâ€™t such a hassle to get there and back â€“ but I will
say the volunteers who walked us down there and then drove us back did
make it easier). Follow the link below for brief summaries of the
presentations and links to them. First up was [Lucas
Carlson](http://tech.rufy.com/) who spoke about [distributed processing
using Rinda and DRb](http://rufy.com/distributed-programming/). Lucas
showed how to setup a simple DRb server and run a client against it,
then he showed how to run a Rinda ring server. Once he got through the
basics he setup a server which parceled out ranges of numbers for us to
check for primes within â€“ several folks in the audience were able to
connect up and process jobs handed out by his prime finder server. Next
up was [Topher Cyll](http://cyll.org/blog/tech) who gave a talk entitled
â€œA Ruby/DHTML Turn Based Strategy Gameâ€¦ in 20 Minutesâ€? â€“
unfortunately I donâ€™t see the slides online yet, but hereâ€™s a link
to his [TBS gem with some exposition](http://cyll.org/tbs.shtml). Topher
used his TBS gem to create a simple turn based strategy game in which
you control a cowboy by moving and attacking (there is another
â€˜evilâ€™ cowboy which you must defeat to win the game). Even though
the game is very simplistic it shows the potential of Rails, JSON and
DHTML/Ajax. Seeing this I was reminded of the talk I went to this
morning at OSCON about unroll (llor.nu) â€“ which Iâ€™ll write about
later as Iâ€™m wiped out and want to finish this FOSCON post before bed.
[Ryan Davis](http://blog.zenspider.com/) from seattle.rb spoke about the
ruby2c project. The project appears to have many facets (more than my
tired brain can grok right now) but two key points I took away from
Ryanâ€™s talk were 1) ruby2c is about generating that subset of the Ruby
interpreter which needs to be in C, everything else should be written in
Ruby so that Ruby can bootstrap itself (like Lisp) and 2) as a result of
the work done on ruby2c, it was really easy for the team to create a
Ruby Obfuscator (a commercial product they are selling). [Geoffrey
Grosenbach](http://www.nubyonrails.com/) of the Ruby on Rails podcast
spoke next â€“ it was quite eerie watching and listening to him as I
pictured him totally differently from hearing his podcasts. Geoffrey
discussed several short cuts, scripts, tools and Rake tasks he uses to
make his life easier when developing Ruby and Rails. He promised to post
the slides on his blog soon. Next [Jim Weirich](http://onestepback.org/)
gave an abbreviated version of his OSCON talk, entitled [â€œTest-driven
Development Meets
Design-by-Contractâ€?](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8699).
He mentioned the fact that Eiffel has built-in support for design by
contract and went through an example of a stack with the contracts for
pop and push. This is what makes duck typing work â€“ itâ€™s not just
that the method is there but that the contract is the same for those
methods. Wrapping up FOSCON II was [Amy Hoy](http://www.slash7.com/)
with a talk entitled â€œCommunity Explosionâ€?. She spoke about the
problems that go with massive popularity (not everyone who wants to
being able to attend a particular conference) and in particular focused
on the problems surrounding newbies. See her earlier write-up on [Help
Vampires](http://www.slash7.com/pages/vampires) for more detail about
the problem. But she was asking for help in setting up materials for
newbies so that they could increase their skills and not be such a drain
on the community. Ok, Iâ€™m wiped, I havenâ€™t been getting much sleep
since arriving at OSCON so no more posts until later tomorrow.

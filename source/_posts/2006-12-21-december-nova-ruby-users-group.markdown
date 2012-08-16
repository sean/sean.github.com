---
author: admin
date: '2006-12-21 12:36:34'
layout: post
slug: december-nova-ruby-users-group
status: publish
title: December NoVA Ruby Users Group
wordpress_id: '93'
categories:
- Programming
- Ruby
---

Last night we had excellent turn-out at the [Northern VA Ruby Users
Group](http://www.novarug.org). [Rich
Kilmer](http://richkilmer.blogs.com/ether/ruby/index.html) gave an
enlightening talk on Domain Specific Languages and [Devin
Mullins](http://twifkak.com/) delivered an interesting performance piece
on Rails plugins where he wrote code while singing about it (ensuring
that the code matched his meter and rhyme). Rich's presentation was very
similar to his [previous
presentation](http://seanmountcastle.com/2006/01/25/january-novarug-meeting)
on the DSL he wrote for the [Coronet refueling
missions](http://www.findarticles.com/p/articles/mi_m0IBT/is_3_57/ai_74407415)
for the USAF. He began by giving a [definition of
DSL](http://www.martinfowler.com/bliki/DomainSpecificLanguage.html)
(from [Martin Fowler](http://www.martinfowler.com)) and then speaking
about External and Internal DSLs. Since the focus of his talk was on
internal DSLs written in Ruby he provided a further division between
explicit and implicit DSLs. His example of an explicit DSL was:

    when_shopping do |store| 

      store.buy :popcorn 

      store.buy :soda 

    end

You'll notice in the explicit case the syntax of Ruby is clearly visible
and a store object is created which the buy method is invoked upon. Here
is his example of an implicit DSL:

    when_shopping { 

      buy :popcorn 

      buy :soda 

    }

In this case, the code is more declarative: when shopping buy popcorn
and soda. Rich appeared to prefer the latter form. He did show an issue
with the implicit form when attempting to access member variables like
so:

    extend ShoppingTrip::Behavior 

    @amount = 6  

    when_shopping { 

      buy :popcorn 

      buy :soda, @amount 

    }

This code won't work because the block is invoked in the scope of the
ShoppingTrip instance where there is no @amount variable. The explicit
DSL doesn't have this problem. When Rich makes his slides available,
I'll update this post to point to them. Devin walked through the
creation of a Rails plugin while singing about what he was typing to the
tune of ["Dance of the
Hours"](http://en.wikipedia.org/wiki/Dance_of_the_Hours) by
[Ponchielli](http://en.wikipedia.org/wiki/Amilcare_Ponchielli). He
showed how you can extend your models using plugins and went through
some of the files created when running script/generate plugin. Tonight,
we also had [Chad Fowler](http://chadfowler.com/) as a guest. It was
nice to finally meet him in person, though I didn't get much of a chance
to speak with him as he was quite popular with the other attendees. He
did mention that he's left [Naviance](http://www.naviance.com/) and is
providing training and consulting services. Hopefully when I attend [The
Rails Edge](http://pragmaticstudio.com/therailsedge/) in January I'll be
able to chat with him some more. I also had the pleasure of meeting
[Luis de la Rosa](http://www.luisdelarosa.com/) who took the plunge and
went indie (though he's supporting himself primarily through consulting,
which I don't call 'indie'). But I'm rooting for him and hope he does
well--I tried the contractor route very briefly after my break with
Cisco and I can say I just don't have the stomach for it (plus I'm the
sole provider for my family and the uncertainty was just too much
stress). I'd definitely like to improve my ObjC/Cocoa skills and look
forward to the next
[CocoaDevHouse](http://cocoadevhouse.org/wiki/index.php/Main/CocoaDevHouseWashington)
(that Luis will help organize). Next month at NoVA RUG we'll have
presentations on Rails deployment and Selenium.

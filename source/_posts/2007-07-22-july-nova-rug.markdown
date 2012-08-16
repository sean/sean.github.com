---
author: admin
date: '2007-07-22 17:33:49'
layout: post
slug: july-nova-rug
status: publish
title: July NoVA RUG
wordpress_id: '123'
categories:
- Programming
- Ruby
---

This past Wednesday we held the July Northern VA Ruby Users Group. We
started off with two short talks, first by [Patrick
Reagan](http://www.sneaq.net/) on two mocking libraries for Ruby
([Flexmock](http://onestepback.org/software/flexmock/) and
[Mocha](http://mocha.rubyforge.org/)), the second was on [Haml and
Sass](http://haml.hamptoncatlin.com/) by [Devin
Mullins](http://blog.twifkak.com/). For the final hour of the meeting,
[Matt Scilipoti](http://weblogs.asp.net/mscilipoti/default.aspx) spoke
about using Rails with legacy databases. Patrick's talk, entitled
["Mockfight! Flexmock vs
Mocha"](http://www.slideshare.net/viget/mockfight-flexmock-vs-mocha),
provided a nice overview of both libraries and several examples
comparing the libraries side-by-side. From the title, I thought Patrick
would be able to declare a clear winner but since both libaries try to
maintain feature parity they are essentially equivalent. My main
takeaway from the presentation was the benefit of using a mocking
library in your tests to bypass expensive or dangerous code paths. Devin
eschewed slides in favor of a live coding session where he converted
Rails scaffold generated eRB (rhtml) to haml. Personally, I don't like
haml markup even though it is definitely more concise than XHTML with
eRB. When I develop, I like to be able to view my template files in the
browser, so I'd like to be able to go in the other direction where my
views are completely XHTML, perhaps something closer to Java's
[Tapestry](http://tapestry.apache.org/) (without the XML descriptor
files). Here's an example comparing eRB vs haml:
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------
  <div id='content'\> <div class='left column'\> <h2\>Welcome to our site!</h2\> <p\> <%= print\_information %\> </p\> </div\> <div class="right column"\> <%= render :partial =\> "sidebar" %\> </div\> </div\>   \#content .left.column %h2 Welcome to our site! %p= print\_information .right.column= render :partial =\> "sidebar"
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------

Matt's talk on working with legacy databases was the final presentation
of the evening. He used the [Takahashi
Method](http://presentationzen.blogs.com/presentationzen/2005/09/living_large_ta.html)
of presenting and ripped through his slides quickly. The first part
covered the issues he encountered trying to build a Rails app around his
legacy database and all of the false starts he made trying to override
the opinions of Rails. One of the approaches he discussed which looked
promising but turned out to be too much trouble in the end were database
views. Using views he could overlay his own view on a table and remap it
to conform to the Rails conventions, unfortunately this turned out to be
a very leaky abstraction -- for example he had to maintain the id fields
manually. His finaly solution involved writing a plugin which handles
the transformations between what Rails expects and how the database is
actually implemented. He is planning on releasing this though he hasn't
settled on a name for his plugin yet (some suggestions were:
acts\_as\_rails, acts\_as\_greenfield, etc). He also mentioned that he
doesn't have to deal with composite keys so he doesn't plan on
supporting them out of the gate. Though like all open source projects,
contributions are welcome, so if you need this functionality give Matt a
hand. Next month's meeting will be on August 22 and [Rodney
Degracia](https://elitefrontier.org/elgg/rubyclrdev/weblog/) will be
presenting on the Ruby CLR for .NET.

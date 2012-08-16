---
author: admin
date: '2007-04-18 20:18:03'
layout: post
slug: april-nova-ruby-users-group
status: publish
title: April NoVA Ruby Users Group
wordpress_id: '116'
categories:
- Programming
- Ruby
---

Tonight we held the April meeting of the Northern VA RUG. [Ray
Daly](http://www.cris.com/~raydaly/) presented RSS and novel uses for it
while [Paul Stadig](http://paul.stadig.name) discussed various methods
of screen scraping. Ray provided an overview of RSS, examples of
widespread usage (news feeds, monitoring, podcasts, etc) and then spoke
about how RSS could be used to tie together disparate systems. He
wrapped up with a Rails demo showing how to create RSS feeds and a brief
discussion of the available libraries for creating and consuming
RSS/Atom. Paul's presentation on screen scraping started with a
discussion of why you'd want to gather data in this way (most of the
interesting data lies in the 'deep web' where there is no API/RSS to
extract the data easily). He then gave an overview, with example code,
of N tecniques: POOR (Plain Old
[Open-URI](http://www.ruby-doc.org/core/classes/URI.html) and RegExps),
POOH (Plain Old
[Open-URI](http://www.ruby-doc.org/core/classes/URI.html) and
[Hpricot](http://code.whytheluckystiff.net/hpricot/)),[WWW::Mechanize](http://mechanize.rubyforge.org/),
[scRUBYt](http://scrubyt.org/), [WATIR](http://wtr.rubyforge.org/) and
[FireWatir](http://code.google.com/p/firewatir/), and
[scrAPI](http://blog.labnotes.org/2006/07/11/scraping-with-style-scrapi-toolkit-for-ruby/).
Of the examples shown, Hpricot looks like an excellent HTML parser
(though it does require native code) while scRUBYt and scrAPI seem to
have the most promise for making screen scraping easy to do. His slides
are
[here](http://paul.stadig.name/articles/2007/4/19/screen-scraping-with-ruby).
The May [NoVA RUG](http://www.novarug.org) will be held on May 23 as the
prior week is [RailsConf](http://conferences.oreillynet.com/rails/).

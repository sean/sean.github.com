---
author: admin
date: '2005-08-10 02:08:00'
layout: post
slug: ruby-on-rails-yahoo-widgets
status: publish
title: Ruby on Rails + Yahoo! Widgets
wordpress_id: '37'
categories:
- Programming
- Ruby
---

After attending OSCON session on [Yahoo!
Widgets](http://seanmountcastle.com/?p=35) by Jeffrey McManus, I decided
I would try to write a widget which connected to [Ruby on
Rails](http://www.rubyonrails.org). First, the Yahoo! Widget (aka
Konfabulator) app is located
[here](http://www.konfabulator.com/download) and the developer
documentation is located [here](http://www.konfabulator.com/workshop/).
Second, to save time, I simply modified the Depot code from the
excellent [Agile Web Development with
Rails](http://www.pragmaticprogrammer.com/titles/rails/index.html) (I
hope Dave and David don't mind). You will need to first download the
code for the book and extract the depot\_final project (and setup your
database, etc). Then you can download my code
[here](http://seanmountcastle.com/assets/rails_widget.zip) and clobber
admin\_controller.rb with my version, then add shipping.rxml in the
views/admin subdirectory. Finally, the JavaScript source code for the
widget is located in SimpleDemo.widget/Contents/SimpleDemo.kon file (you
might need to rename SimpleDemo.widget to SimpleDemo.widget.zip to unzip
it and view the source). It should be pretty easy to understand as I've
commented it well.

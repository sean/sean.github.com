---
author: admin
date: '2007-05-01 22:17:51'
layout: post
slug: implementation-of-digg-spy-in-rails
status: publish
title: Implementation of Digg Spy in Rails
wordpress_id: '118'
categories:
- Programming
- Ruby
---

Based on a comment from an alert reader, I found out that the link was
broken in my [Ajax Spy in
Rails](http://seanmountcastle.com/2006/04/14/ajax-spy-in-rails/) post.
Since I couldn't locate the original zip file on my powerbook, I rewrote
it from scratch using Rails 1.2.3 with REST/CRUD and then updated the
link at the end of that post. To save you time, you can download the
source from
[here](http://seanmountcastle.com/wp-content/uploads/2007/05/spy.zip) as
well. This (and the prior) version simply uses a timer to periodically
call back to the server to see if there were any updates, which places
an unnecessarily heavy load on your server. A better approach would be
to use something like [Juggernaut](http://juggernaut.rubyforge.org/) to
push updates out to clients. I'm investigating Juggernaut now for use in
my Ajax Rails game -- I'll post more once I have a demo.

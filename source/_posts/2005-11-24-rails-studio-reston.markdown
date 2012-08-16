---
author: admin
date: '2005-11-24 08:36:00'
layout: post
slug: rails-studio-reston
status: publish
title: Rails Studio Reston
wordpress_id: '32'
categories:
- Programming
- Ruby
- Training
---

Last Friday and Saturday, I attended the very first [Pragmatic Rails
Studio](http://studio.pragprog.com/) in Reston, VA. I highly recommend
attending the studio to anyone interested in
[Rails](http://www.rubyonrails.org) development. Unfortunately, I wasn't
able to take more time off from work and attend the Thursday session on
Ruby (though I already know enough [Ruby](http://www.ruby-lang.org) to
be dangerous). Dave and Mike really know their stuff and have "real
world" examples of what was easy and where they ran into pitfalls in
Rails. And Nicole took care of all of the little details which make a
training session great (Thanks!)

### Day 1

The pace of the first day was a bit slow for me as I'd already been
playing around with Rails for a couple months and had written some small
web-apps. But David and Mike had to lay the ground-work so that everyone
was on the same page. Thankfully, for those of us who had already worked
our way through [Agile Web Development with
Rails](http://www.pragmaticprogrammer.com/titles/rails/index.html), they
had updated the Depot application with some added features (such as
Ajax, email, migrations, additional testing, etc). After getting the
basics out of the way they went into detail about
[migrations](http://wiki.rubyonrails.com/rails/pages/UnderstandingMigrations)
-- I had heard about migrations at OSCON from Lucas Carlson and John
Butler, but at the time I didn't bother investigating since it didn't
sound that useful to me -- boy, was I wrong. Since learning migrations,
I haven't written another bit of SQL DDL -- and I love it! After that
they spoke a bit about scaffolding and models and then demo'ed
[script/console](http://www.robbyonrails.com/articles/2005/08/18/are-you-a-console-master)
(basically irb with Rails loaded inside of it). Using the console, they
showed how to debug your app, fix issues in the DB and simply browse the
DB -- after the training, the console became a bigger part of my
development style and now I test things out before 'coding and
reloading'. After that we discussed model validation, the find method
(and how the find\_by\_ methods are dynamically generated), SQL
injection, rendering, testing and avoiding GETs with side-effects -- all
of this was review for me, but it had to be covered. Dave showed off
some debugging techniques, where the logs were and that many issues can
be resolved by removing or resetting the session. Finally, Dave and Mike
added some Ajax to the Depot 2.0 app to update the cart in the sidebar
without reloading the page and then added the yellow-fade technique so
that the user's attention is drawn to the cart change. There was one
significant issue during the training which affected many folks:
rendering the cart in the sidebar caused an infinite rendering loop so
the page would load completely blank and there was no information about
a stack overflow in the logs. So if you find that you've added a render
call and now the page is completely blank you might have this problem be
sure that the render command has set layout to false.

### Day 2

Dave and Mike decided to change the pace so that instead of everyone
following along coding, our job was to watch, listen and ask questions.
This allowed us to cover ground much more quickly. First we discussed
web forms and the two different ways in which they could be implemented
with Rails: the two action update (two different methods in the
controller are used, the scaffold works this way with edit and update)
and the one action update (a single method in the controller handles
both the GET request and the POST request). They said which one you
choose depends on your circumstances, but with tools like [Google Web
Accelerator](http://www.37signals.com/svn/archives2/google_web_accelerator_hey_not_so_fast_an_alert_for_web_app_designers.php)
it might not be so bad for your actions to prevent GET requests from
updating the application state. Then we talked about has\_many and
belongs\_to and managing complex hierarchies (such as many-to-many
associations and the acts\_as tools). Since I had not messed with HABTM
or the acts\_as stuff, I found this interesting and am looking for ways
to apply it in my next project. Following this Mike explained
ActionMailer: how to configure Rails for sending and receiving email,
how to generate a mailer and render it. Then we moved on to testing.
First, functional testing (i.e. controller testing) was covered along
with common assertions and the test environment, then we spoke about
fixtures and how to embed Ruby code in them for generating many records,
we discussed mock objects briefly and there was some discussion
regarding how these mocks differ from Java's mocks. Dave then talked
about partial templates and their usefulness when rendering collections.
A brief overview of the flash was next. Hooks, both in ActiveRecord and
ActionController, were explained. Since I had never used the hooks in
ActiveRecord, I found this discussion interesting while the overview of
filters in ActionController was all review. The ActiveRecord hooks seem
great for debugging, though I think they would slow down the application
quite a bit if you took advantage of every single one -- I guess if you
need to massage the data going into/coming out of the DB then hooks
could really be useful. Next routes were covered as an intro to web
services. I had played around with routes briefly and found them to be
really powerful. The overview of webservices was quick -- I had already
written a RESTful one and would be perfectly happy to spend the rest of
my life without ever having to write a SOAP/XML-RPC web service, so I
didn't object. Mike then spoke about his experience working on
VitalSource and how important interface design is for your web-app. He
also urged everyone to get the web designer involved as early as
possible in the project. He stressed the importance of creating many
helpers to extract out the view for components. He recommended waiting
to add Ajax until the end of the project and that it is better to use it
subtly than to over do it. Following that we spoke more about SQL
injection, CSS/XSS, not to trust parameters (especially the id),
validate and sanitize uploaded files, don't cache authenticated pages,
use functional tests to seal potential holes (and recommended checking
out [OWASP](http://www.owasp.org)). Deployment was next. First Mike
discussed the architecture of your web-app (share nothing!) and that you
should move to saving sessions in the DB since multiple instances of
your app will be running on different servers. As far as the webserver,
Dave and Mike were split on Apache and Lighty, respectively (Dave
doesn't think Lighty is quite there yet in terms of rock solid stability
and Mike hasn't had any issues with Lighty -- he admits his Apache-fu is
not that great). Mike talked about setting up your application to email
you (or your cell phone) when things go wrong and Dave discussed the
logs some more (and mentioned
[SyslogLogger](http://rails-analyzer.rubyforge.org)). Some techniques
for optimizing your app were discussed (such as preloading child rows,
using find\_by\_sql, etc) and caching. Page caching was discussed first,
followed by action caching and fragement caching -- I had never used
these techniques, but they seem straight-forward enough -- Dave
cautioned that caching only works in production mode, so if you enable
caching and don't see it working check that first. To end the studio,
Mike gave a great demonstration of
[SwitchTower](http://weblog.rubyonrails.com/articles/2005/10/19/introducing-switchtower-distributed-deployment-for-rails)
which showed how easy it is to deploy your app (whether you deploy to a
single machine or a cluster) and how easy it is to rollback if you found
an issue after deployment. Dave and Mike reminded us to roll our log
files (I think there was an issue on
[TextDrive](http://www.textdrive.com) where someone's exceeded their
quota by far with huge log files), purge old sessions and schedule daily
maintenance with cron.

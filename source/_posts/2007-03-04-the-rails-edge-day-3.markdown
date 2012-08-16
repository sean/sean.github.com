---
author: admin
date: '2007-03-04 17:44:42'
layout: post
slug: the-rails-edge-day-3
status: publish
title: The Rails Edge Day 3
wordpress_id: '102'
categories:
- Programming
- Ruby
- Training
---

By the final day of the conference my head was about to explode with the
amount of new information crammed into it. There were some great tips
and tricks on the final day, but overall, I think the conference peaked
on day two. Here's a run down of the sessions for day three:

-   Buried Treasure: Hidden Rails Tips by Dave Thomas
-   The Streamlined Framework by Justin Gehtland
-   Rinda and DRb by Justin Gehtland
-   -   Amazon's S3 Web Services by Marcel Molina, Jr.
-   Rake: Building Up Ruby by Jim Wierich
-   Rails Production Tips and Tricks by James Duncan Davidson

Dave Thomas started out the day with a collection of Rails (and Ruby)
tips and tricks that he's acquired. He gave an overview of with\_scope
which sets default params for ActiveRecord methods. Next were named
routes with\_options and the fact that with\_options works with any
method that takes a hash (such as table creation in migrations). The
returning ... do ... end block format which saves you from having to
explicitly return your object after doing some other work first. The
ampersand-colon trick which Dave calls the Blockinator:

~~~~ {lang="ruby"}
%w{ cat dog }.map(&:upcase)
~~~~

The date and time goodies added by Rails were discussed next (such as
the various to\_s versions, like :db, :short, :long and ActiveSupport's
DATE\_FORMATS hash which you can add your own formats to in
environment.rb). Enumerable extensions such as group\_by, index\_by and
sum. Array extensions like in\_groups\_of and to\_sentence. String
extensions like at, from, to, first, last and each\_char. Subversion
integration in the Rails scripts (--svn option to generate/destroy).
Using your app via the console, reload! in the console, setting a
default object in irb. And several useful TextMate tricks. Next up was
Justin with his talk about Streamlined.
[Streamlined](http://www.streamlinedframework.org/) is a pretty nice
framework for building the back-end of your Rails app (or for an
enterprise web app, possibly the front-end as well). But, frankly, I'm
sick and tired of hearing about it. I've attended at least four
different events where either Stu or Justin presented Streamlined. After
a short break, Justin came back and spoke about Rinda and DRb. Since I'd
attended [Brian Sletten](http://www.bosatsu.net/)'s NoVA RUG
presentation this was all review for me. The ideas behind Rinda and DRb
are very interesting and I would encourage you to read up on them. Next
Marcel gave an overview of his [AWS::S3
library](http://amazon.rubyforge.org) which makes it very easy to use
[Amazon's
S3](http://www.amazon.com/S3-AWS-home-page-Money/b/ref=sc_fe_l_2/102-1786598-6301708?ie=UTF8&node=16427261&no=3435361&me=A36L942TSJ2AJA)
service from your Ruby programs and it even comes with an interactive
shell for working with S3. Following lunch Jim gave an excellent
presentation on Rake and showed how to create a task for generating
graphs in PNG format from digraph models. He started off with a very
simple example and then refactored it to use the various features of
Rake such as dependencies, file tasks, file lists, dynamic tasks, the
CLEAN and CLOBBER lists, rules, pathmapping, library tasks, and finally,
incorporating your own Rake tasks into your Rails projects. The final
presentation of the conference discussed production tips and tricks by
Duncan. He attempted to answer the most common questions regarding going
into production such as:

-   How much hardware do I really need? Two to four machines for
    redundancy: primary and backup web servers and primary and backup
    database servers.
-   How many Mongrel instances should I fire up? Two to four instances
    on a dual core machine, the rule of thumb is \# of CPU's \* 2.
-   What should I do with my logfiles? Logfiles are gold for root cause
    analysis, you should aggregate logs onto a single machine, you may
    wish to use something like the FiveRuns solution or syslog over the
    network and ensure that you always filter out sensitive data.
-   What kind of load balancer should I use? You could try round-robin
    DNS, but Pound/Pen software load balancers are quite good. A
    hardware load balancer is fine if you have the money but is
    overkill.
-   Should I use Amazon's EC2? Consider it, but keep an eye on it.
-   How often should I deploy? Often.
-   Should I deploy into production with edge Rails? You can, there are
    many others that do it, but be prepared for issues. Unless you're
    really comfortable with it, just use Rails 1.2 for now.
-   How do I test with real-world data? Get your production data back to
    the development team.

Overall, I thought this small regional conference was defintely worth
it. Especially since I spent my own money to attend (unfortunely I don't
get to work on Rails at my day job). The single track was great for
keeping everyone on the same page and fostering great inter-session
discussion. If the Rails Edge is headed your way, I would definitely
encourage you to attend.

---
author: admin
date: '2005-08-04 18:46:00'
layout: post
slug: oscon-preventing-crisis-project-estimation-and-tracking-that-works
status: publish
title: 'OSCON Preventing Crisis: Project Estimation and Tracking That Works'
wordpress_id: '42'
categories:
- Conferences
- OSCON
- Programming
---

For the final session of the day I decided to take a lighter one (i.e.
not programming intensive as my mind had been pickled in Ruby code
throughout the day), so I attended Andy Lester's [Preventing Crisis:
Project Estimation and Tracking That
Works](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6826). My
notes are below (along with links to the slides/velocity chart). Andy
was introduced by Damian Conway (who was complimenting him on his
practical sensible advice). Everyone hates crisis, problems and the
stress that goes with them. This is how Andy and his team do project
tracking -- it works for them, it may not work for everyone. Will we
make it? How we doing? 190 hours short in example (10 week project). Is
it a crisis or readjustment -- don't realize that you're screwed until
just before the end. Find out how things are going, early on so they can
be addressed early on. Goals: - accurate schedules (they make customers
happy) - bad news early (surprise makes customers happy) - fun for you
(otherwise, why bother?) Tools & Principles - honesty with everyone -
changes & mistakes happen - tasks are either done or not (no more 90%
done) - nothing is free (get across to customers and self) Assumptions:
- you have version control - backups - bug tracking How to do projects -
Get a project - some sort of written doc (even if you have to write it)
- does it have all of the info you need to do the project? - How
complete? It's up to you (think leaflet, not phone book) - Nothing is
set in stone - "signed off" on means "as best we know now" - changes
will happen, don't pretend they won't - the requirements establish a
baseline from which work can start - Do a swag - silly wild-assed guess
(spend a day coming up with it, not weeks) - fast & cheap - not a
commitment - estimate in days or weeks - figure out confidence - those
responsible for the work OK the swag - Swag Example: 12 weeks - DB set
up - 1 week - User Screen 1 - 3 weeks - User Screen 2 - 1 week - User
Screen 3 - 2 weeks - Reports - 2 weeks - Admin screens - 2 weeks -
Status web page - 1 week - Do a task list/estimate/schedule - start
breaking up swag - outline form is fine, but not necessary - put them in
chronological order - tasks may not be longer than 4 hours (1/2 day)
Four hours??? - you can't estimate accurately above 4 hours -
distributes risk (estimates are usually off by 100% not 10%) - requires
rocks to be turned over - You're doing design as you go, so keep notes -
Those responsible for the work OK the task list/schedule (otherwise the
developers will resent mgmt, also serves as a sanity check/peer review
on the task, in case something was missed) Task Breakdown Example - foo
report - 4 days - bar report - 2 days - etc. Task Breakdown Further -
Foo report - data input - 2 hrs - Foo report - data marshalling - 4 hrs
- Foo report - web detail - 3 hrs - etc. "I might as well write the
thing" - this is not programming! - the developer thinking about the
tasks is more valuable As you write the code - plan for upcoming weeks -
do one task and complete it - do the next task and complete it - don't
jump more than necessary (too much jumping around is bad because you
want chunks of functionality completed in case you need to ship a subset
of the product, i.e. less features, early). Planning for the week -
assign tasks so each person knows what they are doing each day of the
week. - try to assign less than 8 hours of estimated work per person per
day Track progress - keep track of how many hours the task actually took
- don't check it off until it's actually done - keep track of how long
bug resolution takes as well - re-evaluate remaining tasks if completed
tasks were inaccurate (i.e. they took twice as long). - velocity only
counts those tasks which were completed Tracking the weeks - keep track
of total points (hours) of work remaining (the Sophos guys call this
"burn down") - if missing tasks are discovered, it increases the total
amount of work (moving the "finish line" out) and thus the work
remaining won't decrease as much - towards the end more bugs will pop-up
and the team's velocity will be impacted. - all tasks are binary
(done/not done) - track points completed on a velocity chart - no points
for rework (bug fixes and rework are buying on credit) - don't bother
going back and fixing the time estimate for completed tasks, but for
future tasks you should re-evaluate the time estimates (maybe those
tasks need to be broken down into smaller tasks). We want to know about
these types of issues sooner, rather than later. You can't be a "little
pregnant" - a task is done or not done - I'm done with that code, I just
need to clean it up -- you're not done - I'm about 90% done with these
tasks -- you're not done Adjust - reorder tasks if necessary -
re-estimate and break up tasks if you need to Handle requests - Can do
you X? Yes - How long will it take? I need a day to tell you - Can you
just give me a ballpark? Yes, if I can take a day off of the project to
estimate for you. A non-commital swag is ok here. Slides at [Preventing
Crisis: Project Estimation And Tracking That
Works](http://petdance.com/perl/crisis.pdf) Related excel chart:
[Velocity chart for Preventing
Crisis](http://petdance.com/perl/crisis-velocity.xls)

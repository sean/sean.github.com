---
author: admin
date: '2005-08-03 18:09:00'
layout: post
slug: oscon-extracting-rails-from-basecamp
status: publish
title: OSCON Extracting Rails from Basecamp
wordpress_id: '49'
categories:
- Conferences
- OSCON
- Programming
- Ruby
---

Since I took quite a bit of notes at DHH's [Extracting Rails from
Basecamp](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6837)
session, I thought I'd include them below. Note that these are just my
raw notes, primarily for those who were unable to attend (and aren't in
Portland, as apparently David is doing the talk again at
["FOSCON"](http://www.news4neighbors.net/article.pl?sid=05/07/31/1519250&mode=nested&tid=1)
(free-OSCON) for those who couldn't afford to attend). Update Aug 4,
2005: I was misinformed about FOSCON, evidently David gave the Rails
keynote which he is going to do this morning (I'll have a separate post
on this later). Basecamp project management tool existed first. Embraced
constraints: - less people, more power - less money, more value (funded
via consulting) - less resources, better use - less time, better time
Start small and grow only as needed (frugality) Basecamp was 2.5
man/months, 4k lines of code, 2/3 designers, 1/4 programmer (10 hr/week)
Built half a product instead of a half-ass product They had to develop
less software due to these constraints. But, why yet another framework?
Because the options were not appealing. Worked in PHP for 5 years. Had
to step outside the sweet spot. Felt like he was cutting against the
grain. Built almost half of Rails in PHP, but the language was pushing
back -- struggle all the time. Looked for inspiration. In the enterprise
world, there was too much enterprise. Too much focus on 99.999's, not
enough on the 98% -- get something out there early and only once you
have the users invest the time in scalability and reliability. Too much
focus on 100 man shops, not enough on the 1/4 man shops. Platform works
against you when you're not creating massive applications with massive
teams. Liberate the good ideas. Great ideas are not tied to
language/platform. - Change the language - Change the context - Retain
the core insights of patterns/practices Call me shallow: - Aesthetics -
want the code to be beautiful and easy to read/understand - Joy -
happiness, motivation, joy of work - Less - less code, favorite part of
programming is removing lines of code Laying out the framework up front
doesn't work, you must extract it from a working application. There's no
other way. I'll know it when I see it. You have to feel an API to make
it fit. Pleasing to work with API cannot be designed up front. Design
matters more than test in TDD. Guessing the future is for fortune
tellers. Why open source? For entirely selfish reasons: - Make others do
the work - Bask in the glow of being a giver - What's there to loose? It
works! 1,000 patches in 9 months! Extract, pass, reap, rinse, repeat
Getting traction for your open source project -- if no one's looking it
doesn't matter if it's open source or not. Many abandoned projects
because they got no visibility/involvement. Fear obscurity. You need a
network to reap the effects. Get rid of humbleness, take on a normal
appreciation of the value you bring to the table. Passion is infectious
The baseline of excitement needs to be set by you -- you need to be the
most excited person about your project. Self delusions work! A
conversation of success, build on the positive emotion of others. Go
looking for trouble Tout advantages over the known, say that the biggest
thing out there "sucks" "If it bleeds, it leads", everybody loves a good
fight Point at someone else and say, 'you're stupid' trouble is easy to
find and easy to start -- you created this because you were not happy
with the status quo. Prison newbie mentality -- attack the biggest
looking opponent immediately to gain some respect. Dealing with traction
Scaling a culture Early influx can bend you out of shape Release not so
early, then often -- releasing too early can cause an influx which will
overtake your culture. Set a viral example of kindness -- what you do as
project lead influences others. (watch out for the looking for trouble
part as your new members will do the same). Signal that there is already
a course and new members need to be willing to go in that direction.
Don't ever say RTFM! Overcome the sucky feeling of being a newbie. You
need to care from the earliest stages of the project. In a response to
the question, Why Ruby? Why not Python? David responded that ruby makes
it easy to create domain specific languages. Notion of blocks is also
important.

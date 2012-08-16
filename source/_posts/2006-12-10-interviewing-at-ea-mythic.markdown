---
author: admin
date: '2006-12-10 23:11:19'
layout: post
slug: interviewing-at-ea-mythic
status: publish
title: Interviewing at EA Mythic
wordpress_id: '91'
categories:
- C/C++
- Entertainment
- Programming
---

Ever since I started playing video games at an early age, I always
wanted to develop them. I had my first taste of this in grade school
when I figured out how to modify some of my favorite games by editing
the data files in a hex editor. In high school, I bought myself a copy
of Borland Turbo Pascal (and then later Turbo C++) and taught myself how
to program--building rudimentary games. For college, my mother really
wanted me to become a lawyer so I decided that the best way to get there
was to major in political science. While I did well, I just wasn't
really interested in it. So in my junior year I changed my major to
computer science. Of course, I had already chosen my university based on
their reputation for political science and law and as such the computer
science curriculum wasn't the best. Since freshman year I had been
running a [MUD](http://en.wikipedia.org/wiki/MUD) (I had to finagle an
account on the engineering Ultrix machines as I wasn't in the School of
Engineering--we also weren't supposed to be running servers either but I
had some crafty ways to hide my work from the TAs). In my junior year I
built a raycasting engine and a simple FPS (similar to [Wolfenstein
3D](http://en.wikipedia.org/wiki/Wolfenstein_3D)). While I continued to
follow the game industry and read-up on the newest techniques from folks
like Michael Abrash, John Carmack, Andre LaMothe, etc. my foray into
game development was still-born. In my senior year I took an internship
at the Naval Research Lab and was pigeon-holed into telecommunications
from that point on (I believe I've finally escaped, though I'm currently
working on some very interesting and vital Internet infrastructure).
Anyway, you didn't come here to read about me and my failed attempts at
game development, you want to know about interviewing at EA's Mythic
Studio in Fairfax, VA. Home to Dark Age of Camelot (DAoC) and the
upcoming Warhammer Online: Age of Reckoning (WAR). Back in July, I
contacted my friend Scott who works at [Blue Fang
Games](http://www.bluefang.com/) in Waltham, MA to find out if he knew
anyone at [Mythic Entertainment](http://www.mythicentertainment.com/).
Fortunately he did, his friend Ralph, an artist at Mythic, was able to
put me in touch with the CTO, Matt. At this time they were still in
transition due to the acquisition of Mythic by Electronic Arts so Matt's
email address changed and communication was difficult. I continued to
persevere until Matt agreed to bring me in for an interview at the end
of August. It was an all day interview (from 10am until 5pm), which I
was glad for--I really dislike it when companies only speak to you for
an hour or two; it's just not enough time to assess someone. Knowing the
culture at the company I didn't wear a suit and tie to my interview, but
khaki pants and a button-down shirt thinking that I should at least
dress somewhat nicely to the interview (even this elicited a mixed
response, which I'll speak about later). When I arrived at Mythic, Matt
(the CTO) came out to greet me and spoke with me for a short while about
why I wanted to become a game developer, my professional experience and
skills. He then walked me over to speak with Darren who is essentially
the director of operations for Mythic, managing their datacenters and
ensuring that the hardware and network are operating. One of his direct
reports, Andrew, was in his office so they decided to tag-team interview
me--which I didn't mind. Darren explained his role, the machines in
their co-lo out in Ashburn and their pipe to the internet. Andrew
quizzed me about various programming languages and had me explain my
most recent project at Cisco. I brought up Ruby and tried to make a case
for it increasing their productivity in operations through the use of
scripts and custom web apps to help manage and monitor their systems.
Andrew was already using Python and had done some of this already
(though not to the extent I had envisioned) and didn't see the need to
learn yet another programming language. Granted Python and Ruby are
equivalent enough that one or the other is suitable for these type of
scripts/apps. Matt had thought that the best fit for me would be here in
the operations group since I did not have any professional game
development experience. Next I met with Ed who works on the WAR game
server. He explained that one of his biggest problems was NPC
path-finding and that they were evaluating a new library from a company
in Europe (France, I think). But even that wouldn't scale to the number
of NPCs they have in a shard. He showed me the 'tools' they used to
design spells and NPC behavior--basically an Excel spreadsheet that the
game designers fill in that gets imported into the game server. I left
with some ideas on how to improve these tools quite a bit (using a DSL
written in Ruby that would be easy for the designers to write spells and
behaviors in or a Rails app which used Script.aculo.us for drag-and-drop
building of spells/NPC behavior from basic building blocks). Following
my meeting with Ed, the team took me out to lunch where I made a pretty
big mistake--instead of talking about games the whole time, I admitted
that I had to pack-up my PS2 over a year ago because my toddler kept
grabbing at the cords and opening the game cases. One good thing that
did come out of lunch is that I learned about [The Venture
Bros.](http://www.adultswim.com/shows/venturebros/), the best cartoon on
TV. I think it's absolutely hilarious and I've been recommending it to
all of my friends ever since. When I got back to the office, they
introduced me to Brian who also worked on the WAR game server. I had a
great conversation with him and liked him quite a bit. He has been
working at Mythic (or Interworld Productions as it was known at the
time) since their first MUD, Dragon's Gate. What I found interesting
about Brian was that he had been working there since high school and had
no formal computer science background (though he said he was working on
his degree at GMU). An interesting tidbit that I learned from Brian is
that for all of the games Mythic has released, the server-side codebase
is derived from Dragon's Gate--they just keep adding functionality to it
over the years and try to patch over the brittle parts. After speaking
with both Ed and Brian, I was very excited about working on the WAR game
server and thought this was the group I could quickly contribute to.
Next they had me speak to another developer named Matt (not the CTO). At
first, I had mistakenly though he was in the operations group working
with Andrew and Darren. Matt works on the game server for DAoC which
appears to be in a sustaining mode. Following the interview, I was still
not clear on what work needed to be done on DAoC. I think this was one
of my worst interviews at the company as there seemed to be a lack of
understanding between us--the questions he was asking me were not at all
clear (perhaps that was the point), so I tried my best to tease more
information out of him and answer them to the best of my ability. As
sort of an afterthought they had me speak to Marty, another game server
developer on DAoC who said his background was on the client side (3D
Windows application programming). He was the most hostile towards me and
also the most frank. He was appalled by the fact that I had packed up my
PS2 to prevent my children from breaking it--he explained that if he
were in that position he would tell his wife to take the kids away so he
could play (the way he said this made me feel sorry for his family).
According to Marty they are only looking for folks who've worked in the
game industry before or are hard-core gamers (at the expense of all
else, he recounted the personal sacrafices he made to get into
Mythic--essentially commuting up to Northern VA on Monday, staying for
the week and commuting back to his family for the weekend). His
rationale for preferring hard-core gamers was reasonable--he explained
that in design meetings they typically referred to other games and this
shared knowledge of the details of games (through having played them)
allowed the team to come to consensus much sooner. He used [Elder
Scrolls
Oblivion](http://www.elderscrolls.com/games/oblivion_overview.htm) as an
example, but couldn't remember the name of the game (which I had to
remind him of). So while I stay up-to-date on the latest games, actually
having played them helps to build this shared gaming culture. Marty also
thought that I was way over-dressed for the interview (in khaki pants
and a button down shirt), he was wearing a t-shirt and shorts and I
thought I should've worn something more casual. I tried to explain to
him that this was a job interview and that I wanted to make a good
impression but it had the reverse effect on him. Finally I had a sort of
exit interview with Matt (the CTO) who asked for my impression of the
team and the company (which was good) and he gave me a tour of the area
surrounding the art team for WAR. The art on the walls there is simply
amazing and having been a huge fan of Warhammer it was a real treat. At
this time he also explained to me why [Imperator
Online](http://en.wikipedia.org/wiki/Mythic_Entertainment#Presently) was
cancelled--it just wasn't fun for them when they played through it.
MMO's with guns are really hard to balance and after many months of
development the game just wasn't coming together. Matt also confirmed
that WAR would be released on both the PC and the Xbox 360 (the latter
of which he recommended I get, instead of the PS3 or Wii). Matt was most
concerned about my salary at Cisco, constantly assuring me that they
would be unable to me it. I explained that I was willing to take a bit
of a pay cut for the opportunity to work as a game developer on
Warhammer. I left with mixed feelings, not sure whether I would be
offered a position at Mythic. I was quite surprised that I wasn't given
any form of coding test. Following Labor Day weekend, I heard back from
Matt that they decided not to offer me a position, here's the content of
his email:

> After a lot of consideration, we don't think it is a good fit for you
> here at Mythic. You obviously are very talented at what you do, with
> our limited position slots available here; we would like to fill them
> with individuals with game job experience if possible. Take care, we
> wish you the best with your future endeavors.

Having gone through this experience and done quite a bit of research,
I've come up with the following tips for interviewing at EA Mythic, or
any game developer:

-   If you don't have any game industry experience, create your own by
    making your own game. Go through the entire process and complete
    it--don't show off a half finished game.
-   If you're not a rabid gamer, become one. At lunch talk about your
    favorite games, why they are your favorites, what new games you're
    looking forward to, etc. Here they're looking for passion. The
    thought is if your passionate about games, your passion will show in
    your work (and you'll be willing to work 80-100 hours during crunch
    time, the two or so months prior to release).
-   Don't try to push any new technology or programming language during
    your interview. Once you've gotten the job you can then try to
    effect change. Instead show how your skills can work within the
    existing situation to improve it. This is true of basically any
    job--it's naive to think that you know better than they do after
    having worked in the domain for so long. Though the game industry in
    particular appears to be quite insular and has only recently started
    switching to tools, processes and procedures that have been shown to
    work well in software development projects.
-   Provide specific examples of how you can contribute to the team. You
    need to sell yourself to them.
-   Research the company and culture as much as possible prior to the
    interview. I did quite a bit of research about Mythic before
    interviewing and knew a lot about the founders and the products, but
    I didn't know that much about the culture. I should've used Ralph
    (my friend's friend) to find out more prior to my interview.
-   And, of course, they're looking to see that you can communicate with
    them and that you're not a total jack-ass. Remember, we're dealing
    with real people, treat them the way you wish to be treated. Even
    though Marty was rather hostile to me during my interview, I still
    treated him with respect and answered his questions honestly. Having
    hobbies you can talk about in a lunch setting may also be good, but
    the lives of the guys I spoke to seemed to revolve around games and
    television (not really what I'd consider hobbies).

If you have any additional tips/tricks for landing a job as a game
developer, please post them in the comments.

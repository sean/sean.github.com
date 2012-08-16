---
author: admin
date: '2006-07-28 00:53:00'
layout: post
slug: oscon-sessions-day-three
status: publish
title: 'OSCON: Sessions Day Three'
wordpress_id: '7'
categories:
- Conferences
- OSCON
- Programming
---

Below are my notes from the third and final day of sessions here at
[OSCON](http://conferences.oreillynet.com/os2006/). The talks I attended
were:

-   Practical OpenID
-   Highly-technical Management of Software Development

After the morning keynotes, I attended Practical OpenID, presented by
[David Recordon](http://seanmountcastle.com/davidrecordon.com) and
[Brian Ellin](http://brianellin.com). They gave a quick overview of
authentication and then discussed how OpenID works:

-   You obtain an OpenID from someplace like MyOpenID (linked below).
-   You add two lines of HTML to your site header â€“ to prove you own
    that URL.
-   You then go to an OpenID enabled site and enter your URL.
-   The site goes to the URL you entered and determines the OpenID
    server from the information in the page header
-   The web app then redirects you to the login page on the OpenID
    server.
-   Once youâ€™ve authenticated yourself with your password, the browser
    is redirected back to the web app with your credentials.

Then Brian ran the Rails demo and showed how his Rails app was able to
authenticate through [MyOpenID](http://www.myopenid.com) and redirect
back to his Rails app with additional registration information.

David also mentioned that there is a $5,000 bounty for open source apps
which integrate OpenID:
[iwantmyopenid.org](http://iwantmyopenid.org/bounty).

Next up was [Highly-technical Management of Software
Development](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8694)
by [Alex Martelli](http://www.aleax.it) of Google. He started out by
listing the three legs of the software development stool:

-   Right intention =\> strategic leadership
-   Right action =\> excellent developers
-   Right endeavor =\> effective highly-technical management

He then asked a series of questions regarding these three pillars:

-   What is great strategic leadership?
    -   a strong vision of the business model
    -   mutual trust, interaction and respect
    -   courage, integrity, humility, etc

    They do their job well and *let* me to do mine.
-   What makes developers excellent?
    -   great at design, coding, developing, testing, debugging, user
        interface design, etc.
    -   mutual trust, interaction and respect
    -   courage, integrity, humility, etc.

    They do their job well and *enable* me to do mine.\
     Aside: How do you get excellent developers? Luck, choice or grow
    them.
-   What is effective highly-technical management?
    -   start with a manager whoâ€™s a technical peer of the developers
    -   develop mutual trust, interaction and respect with the
        developers
    -   the manager deployes themself as a â€œwildcardâ€? technical
        resource â€“ not for the â€œfunâ€? tasks, for the urgent ones
        needing extra resourcesThere are usually three objections to
        this:
        -   What about Brooksâ€™ Law?
            -   â€œAdding resources to a late project makes it laterâ€?
            -   Yes, but in that case itâ€™s due to the fact that the
                new developer must get up to speed on the project
            -   The highly-technical manager should already be up to
                speed on the project â€“ no extra overhead, so Brooksâ€™
                law doesnâ€™t apply

        -   Where does one find the time?
            -   **NOT** in working long hours (aim for 40 a week).
            -   **NOT** by telecommuting (communication is the most
                critical task and face-to-face communication is best)
            -   Time management works (recommended [Time Management for
                System
                Administrators](http://www.amazon.com/gp/product/0596007833/sr=8-2/qid=1154131620/ref=pd_bbs_2/104-0491953-9680738?ie=UTF8)
                â€“ schedule 50% of your time each week for emergency
                tasks or with filler that can easily be post-poned

        -   Shouldnâ€™t a manager always delegate?
            -   Yes, but delegation doesnâ€™t remove your responsibility
                â€“ you need to stay up to speed on all of your projects
            -   You should trust your people to do whatâ€™s right, but
                you have to enable them to do it
            -   Once they see your technical contributions are useful,
                they will want you involved â€“ as long as youâ€™ll
                **never** steal the credit

At the end of his presentation he mentioned that Joel Spolsky got it
right about scheduling â€“ a spreadsheet is all you need (Gantt/Pert
charts usually donâ€™t work). Use agile methodologies (agile planning,
TDD, refactoring/DRY, 40-hour week, ego-less programming, frequent
releases).

Alexâ€™s final message was to **control your dependencies** or they will
control you!

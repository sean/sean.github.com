---
author: admin
date: '2006-07-27 23:08:00'
layout: post
slug: oscon-sessions-day-two
status: publish
title: 'OSCON: Sessions Day Two'
wordpress_id: '8'
categories:
- Conferences
- OSCON
- Programming
- Ruby
- Smalltalk
---

Below are my notes from the second day of sessions here at
[OSCON](http://conferences.oreillynet.com/os2006/). The talks I attended
were:

-   Subversion Best Practices
-   haXe: A Cross-platform Web Language
-   Building DSLs in Ruby
-   Testing Rails Apps
-   When Interface Design Attacks!
-   Web Heresies: The Seaside Framework

In the morning, I attended [Subversion Best
Practices](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8671)
by Ben Collins-Sussman and Brian Fitzpatrick. I donâ€™t see the slides
up yet at the [Subversion](http://subversion.tigris.org/) site, but they
said that the slides would be posted. Several of the best practices they
covered were:

-   Server Best Practices
    -   svnserve: good for simple setups
    -   svn+ssh: great if you already depend on sshd
    -   Apache: more points of integration, repos web browsing, network
        share, etc.
    -   Always use a single repository when you have shared users,
        shared code, etc; except when you have radically different
        access policies, radically different data types, etc.
    -   Some nice repos browsing tools are:
        [ViewVC](http://www.viewvc.org/) and
        [Trac](http://trac.edgewall.org/)
    -   Hook scripts:
        -   pre-commit: donâ€™t try to modify the transaction, just fail
            it if you need the code to be formatted, for example.
            Mentioned case-insensitive.py.
        -   post-commit: run it in the background so it doesnâ€™t hold
            up the user. Mentioned mailer.py and CIA bot.

    -   Repos Maintenance:
        -   dump: slow, not for backups
        -   hotcopy: does a cp -R, can be used for backups and then you
            can rsync the copy, if needed

-   Client Best Practices
    -   commit often
    -   commit small, discreet chunks (but **donâ€™t** commit individual
        files)
    -   have a consistent log message policy

-   Misc Best Practices
    -   Use branches: you can have task branches, feature branches,
        release branches, etc.
    -   Merge tracking: must be done by humans currently, but in 1.5
        there is real merge tracking.
    -   Autoprops: take advantage of these, some examples are:
        svn:mime-type, svn:eol-style, svn:needs-lock

Thankfully Nicolas Cannasseâ€™s talk entitled [haXe: A cross-platform
web
language](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8600)
was moved earlier (prior to this I had a triple-conflict this
afternoon). Nico appears to be an amazingly smart fellow and
[haXe](http://www.haxe.org) along with the [NekoVM](http://nekovm.org/)
(only 220KB!) look like very interesting technologies. He started with a
simple â€˜Hellow Worldâ€™ example in haXe which was then generated into
JavaScript, Flash and Neko â€“ that is the same source code can be
easily re-targeted to different â€˜platformsâ€™. At the end he showed
off [Dinoparc](http://en.dinoparc.com) and Hammerfell, two Flash games
that were written using haXe. Nico also mentioned that someone is
writing a Ruby compiler which targets the NekoVM.

After lunch I attended [Neal Fordâ€™s](http://www.nealford.com) Building
DSLs in Ruby. He showed off a simple calendaring DSL. His slides are
here and he followed them very closely so I donâ€™t have much
commentary. I guess the only way to get comfortable designing and
implementing DSLs in Ruby is to actually write them â€¦ Iâ€™m going to
have to pick some domain and just start.

Then [Mike Clark](http://www.pragmaticstudio.com/) was up with [Testing
Rails
Apps](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8395) â€“
much of this was review for me, but I was looking forward to his
tips/tricks to make testing easier. Iâ€™m really trying hard to be a
â€œtest-firstâ€? developer but I get so excited writing new features
that I leave the tests for last (of course, this usually means that I
end-up refactoring the code I wrote based on the tests, which is a good
thing). Since his slides arenâ€™t up yet, Iâ€™ll post some of my notes.
Mikeâ€™s keypoint was that tests are insurance â€“ they ensure that
programming your app remains fun, so youâ€™re not scared of making
changes because you have a nice test suite which can quickly find out if
youâ€™ve broken something else with your change. Some of his tips are
below:

    # if the product isn't valid, print out the errors
    assert product.valid?, product.errors.full_messages

    # checking uniqueness
    assert_equal ActiveRecord::Errors.default_error_message[:taken],
    product.errors.on(:title)

    # for integration testing create a user object with method
    # names that are in plain English
    def regular_user
    open_session do |user|
    def goes_to_store
    get :index
    assert_response :success
    end

    def is_viewing_index
    assert_template "index"
    end

    def buys_book
    post :add_to_cart, :item => { :id => 1234 }
    end

    def checks_out
    post :checkout, :payment_info => { ... }
    end
    end
    end

Following the break, I attended [When Interface Design
Attacks!](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8924)
by [Amy Hoy](http://www.slash7.com). Her slides should be up on her
website soon but some of the key points were that interface involves:

-   expectations (baggage)
-   interaction (usability)
-   behavior (your appâ€™s personality)

Some of the principles she mentioned were:

-   usersâ€™ brains are affected by literacy; they scan in predictable
    patterns (reading right to left, top to bottom)
-   users adapt to web design (ignoring headers, sidebars, stuff below
    the fold)
-   if it looks like an ad, itâ€™s ignored (or if itâ€™s a small bit of
    content surrounded by ads, itâ€™s ignored)
-   users â€˜satisficeâ€™ or give up (they pick the closest thing to
    what they were looking for)
-   30-40% of users have low literacy (reading blocks of text is
    difficult for them â€“ the changes you make for these users also pay
    off for those who donâ€™t have literacy issues)
-   There should be twice as many pixels above an object than below it
-   Labels should be above their input and labels should have the same
    name/id as their corresponding input fields

Amy then went through several examples from popular websites.

The last talk of the day was [Web Heresies: The Seaside
Framework](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8942)
by [Avi Bryant](http://smallthought.com/avi/) â€“ basically it was
[WebObjects](http://www.apple.com/webobjects/) meets
[ViaWeb](http://www.paulgraham.com/vwfaq.html) (in
[Smalltalk](http://www.squeak.org/)). The ideas behind
[Seaside](http://www.seaside.st/) are quite cool, but having never used
Smalltalk and hating every IDE Iâ€™ve ever tried it just didnâ€™t appeal
to me. Technically, the continuation usage is incredible â€“ every time
you click a link a continuation is generated (complete call stack) so if
you go back youâ€™re old call stack is still there and you can then have
the function return a different value taking you some place else within
the web app. Avi doesnâ€™t like templates, he wants HTML to be back in
the domain of the developer and it should be generated from within the
web app â€“ the designer only gets to touch the CSS (see [CSS Zen
Garden](http://www.csszengarden.com/) for examples of how this works).
To handle form fields, Seaside simply uses callbacks â€“ you place the
block of code in a callback right where the text field is generated,
this is what the code looks like:

    html form:
    [html text: 'Name: '.
    html textInputWithValue: person name callback: [:val | person name: val].
    html break.
    html submitButton]

---
author: admin
date: '2006-07-25 18:35:16'
layout: post
slug: oscon-rock-solid-web-development-testing-web-apps
status: publish
title: 'OSCON: Rock-solid Web Development: Testing Web Apps'
wordpress_id: '12'
categories:
- Conferences
- OSCON
- Programming
---

[John Paul Ashenfelter](http://www.transitionpoint.com) gave an
interesting tutorial called [Rock-solid Web Development: Testing Web
Apps](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8704). The
slides are available
[here](http://www.transitionpoint.com/downloads/oscon2006.zip). I’d
heard about [Selenium](http://www.openqa.org/selenium/) before this
presentation, but never took the time to investigate it – after seeing
it used here I’ve already installed it and set it up to test my Rails
app. John Paul started out with an overview of software testing, the
hierarchy of testing:

-   None
-   Ad Hoc
-   Unit Testing
-   Throwing Bodies at it
-   Bodies with a Test Plan
-   Automated Test Plan

Then he went into the different types of testing:

-   Low-level Code (Unit testing done by developers)
-   App-level (Done by developers and QA)
-   System level (Load, Performance, Stress)
-   User level (Usability/User acceptance)
-   The rest (security, regression, conformance, failover)

His important points were that your **users do not do testing** and that
you should *always* be testing. The next part of the tutorial covered
[Selenium](http://www.openqa.org/selenium/). He showed how to run
Selenium (the barriers to entry are extremely low – just HTML and
JavaScript) and then how to record your own tests using the [Selenium
IDE](http://www.openqa.org/selenium-ide). Once he recorded a simple
test, which is just an HTML table with three columns, we saw how it
could be easily edited and run. Selenium Remote Control was brought-up
next and code examples in Java, Python and Ruby were shown – here’s the
Ruby example:

      def testHome
    puts selenium.open "http://oscon/"
    puts selenium.clickAndWait "link=Constitution"
    puts selenium.assertTitle "Cat Club - Constitution"
    end

The third part of the tutorial covered Automation and Continuous
Integration which used [Ant](http://ant.apache.org) to run Selenium.
Before Selenium was launched by Ant,
[dbUnit](http://dbunit.sourceforge.net/) was used to get the database
into a known state prior to the Selenium tests being run. Finally, the
[Grinder](http://sourceforge.net/projects/grinder) load testing
framework was discussed. An alternative, [OpenSTA](http://opensta.org/)
was also briefly mentioned – but John Paul focused on Grinder 3. He
showed how you can record a script using the TCPProxy portion of Grinder
and then starting and agent and running from the console which hit his
server with 100 users (5 processes with 20 threads each). His take home
lessions were:

1.  Testing gives you confidence in your code and your application
2.  Users are NOT your testers
3.  Good programmers always write tests
4.  Selenium will save you time
5.  If you repeat it, automate it
6.  Load testing is pretty complicated


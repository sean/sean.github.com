---
author: admin
date: '2007-03-04 16:59:26'
layout: post
slug: the-rails-edge-day-2
status: publish
title: The Rails Edge Day 2
wordpress_id: '101'
categories:
- Programming
- Ruby
- Training
---

The second day of the conference was even better than the first, in my
opinion. There were several more talks which I was eager to hear. Here's
an overview of the second day's presentations:

-   Creating Rails Plugins by Chad Fowler and Bruce Williams
-   The Presenter Pattern by Marcel Molina, Jr.
-   The Deployment Golden Path by James Duncan Davidson
-   Testing Rails Apps by Stu Halloway
-   Red, Green, Refactor by Jim Weirich
-   Building View Frameworks by Bruce Williams
-   Lightning Talks

Read on for my notes. First up were Chad and Bruce who went through
Creating Rails Plugins. Never having created a Rails plugin before, I
was very interested in the process. They started by providing an
overview of the plugin script and then the generate plugin script. Next
they showed how you can provide your own controllers (in the lib subdir)
and views (in the views/'plugin name' subdir), rake tasks (in the tasks
subdir), models (right at the top-level of your plugin) and your own
generators (in the generators/'plugin name' subdir). The remainder of
the talk walked through the creation of their
[acts\_as\_ratable](http://rubyforge.org/projects/ratable/) plugin.
Marcel followed that with his talk on the Presenter Pattern. He was
quick to point out that this is not a design pattern in the style of the
Gang-of-Four book (especially since previous presenters had made
derogatory comments about design patterns and their utility). The
presenter pattern is basically a way to *organize* a chunk of view code.
He started off with a discussion of the problems with helper modules,
how they become a dumping ground for methods (one suggestion was to
break-up your helpers into smaller modules organized around specific
functionality and then include those in your helper). A comparison was
made to the 'method object' in Kent Beck's Smalltalk Best Practice
Patterns (linked at bottom of this post). To finish, Marcel gave a brief
demo of this but it's basically vaporware at this point and didn't have
a date for when it would be released. JDD was up next with his talk on
Deployment. He stressed that it was important to start deploying your
app as soon as possible in the development cycle (he suggested that you
do it at the same time you set up your Subversion repository). This is
necessary to find all of the "interesting" deployment problems up front,
so you can get into the deployment rhythm and so that you can show
others what you're working on for feedback. You just need a machine that
works well enough, he suggested a Mac mini, but some folks in the
audience suggested a virtual machine on the same box -- Duncan said that
while that might work he prefers having another machine to deploy to.
The only deployment solution that he recommends right now is Mongrel
fronted by Apache, Lighty, Pound, Pen or a hardware load balancer. Then
he went on to describe what he calls 'the golden path' using Capistrano,
Subversion and Unix machines. At the end he gave a live demo deploying
his app to an Amazon EC2 machine. After lunch, Stu presented on Testing
Rails Apps. Perhaps I'm insecure about my testing and test coverage
(though Mike Clark's rcov Rake task certainly provides peace-of-mind),
but I always find myself very interested in the testing methodologies of
others. Stu started off by discussion the reasons to write tests (tight
feedback loop, easy refactoring, early warning, cheap measure of success
and that it makes bad code painful). He went through testing models
(ensure your tests are self-documenting, test everything in sight and
then evolve your own style), fixtures (YAML, always use valid data, use
ERB for dynamic data), controllers (check out the scaffold: it tests
responses, redirects, model updates and uses restful verbs), managing
your tests (group and run using rake, manage your fixtures with rake,
put your common tasks in test\_helper.rb). He then went through an
example of testing a space station w/o having access to a rocket, so he
used flexmock to mock one up, like this:

~~~~ {lang="ruby"}
def test_refuel_with_mock_recorder
  rocket = flexmock("rocket")
  rocket.should_expect do |rec|
    rec.dock.ordered
    rec.attach_fuel_hose.ordered
    rec.add_fuel(Integer).returns(50).ordered
    rec.detach_fuel_hose.ordered
    rec.undock.ordered
  end
  @station.refuel(rocket, 50)
  assert_equal 950, @station.fuel
end
~~~~

He then went on to recommend rcov and said that you should have 100% of
your code covered. He ran out of time before he could cover the
[Cerberus](http://www.degrunt.net/articles/2006/08/27/cerberus-continious-integration-for-rails/)
continuous integration tool. Jim Weirich sat down for a live coding
presentation entitled, "Red, Green, Refactor" in which he demonstrated
test/behavior driven development. The steps were:

1.  Write a new test and watch it fail
2.  Write just enough code for the test to pass
3.  remove duplication, clean up, etc. and repeat

He spoke in terms of dividing your perspective into two parts a Dr.
Jekyll who writes a test that forces you to write the code you need and
a Mr. Hyde who deliberately writes the minimal amount of code that
passes the tests. His demo seemed pedantic at first, but because you
have this extremely lazy Mr. Hyde you really have to think about your
tests and write them such that you force the implementation to be
correct. Bruce Williams spoke about Building View Frameworks and made
the example code available at his
[site](http://codefluency.com/examples/ui_frameworks.tar.gz). I was
really looking forward to this talk and Bruce didn't disappoint. He
started off discussion the traditional methods of DRYing up your views:
Helpers, Block Helpers and Partials then he went into REST DRYing with
the simply\_helpful plugin. Next he went into some new territory for me,
DRY interactions by creating a controller DSL, controller plugins and
"big frameworks" as he called them. He gave examples of this from his
work at Naviance: folder\_for (which created a tabbed view for the
different folders), paginated\_index which was a controller DSL,
roster\_for (which was very similar to paginated\_index) and a calendar
which was a controller plugin. Bruce suggested using plugins and writing
your own and contributing them back to the community as well as testing
your views with Watir or Selenium. Following the presentations, were the
lightning talks. I was unable to stay for all of them but some of the
more notable ones were: Aaron from [Revolution
Health](https://www.revolutionhealth.com/preview?code=gJ3AyxODNg)
demo'ed their huge web app (or more accurately collection of integrated
web apps) and spoke about their PluGems solution which has been document
on their [blog](http://revolutiononrails.blogspot.com/). It looks like
they're really doing some interesting work and having a lot of fun doing
it (plus I'm jealous of their development environment -- I wish my
employer gave each of us MacBook Pros instead of Lenovo ThinkPads); Next
[Jared Richardon](http://jaredrichardson.net/), author of [Ship
It](http://www.pragmaticprogrammer.com/titles/prj/), spoke about his
consulting work on a new search engine site called
[ChaCha](http://www.chacha.com/) and how they scaled Rails by removing
ActiveRecord in production. They use Rails as normal during development
and then extract out all of the SQL queries and tune them for
production; [Mark Cornick](http://mcornick.org/) gave a quick run-down
on the service manager framework in Solaris and [how he used it to
launch his Rails app when the machine
boots](http://mcornick.org/stories/91-mongrel-meet-smf-smf-meet-mongrel).
Since we use a fair amount of Solaris at work and I'm not that familiar
with this feature, I found his talk quite enlightening. The presenters
have really been pimping Kent Beck's book, [Smalltalk Best Practice
Patterns](http://www.amazon.com/Smalltalk-Best-Practice-Patterns-Kent/dp/013476904X/ref=sr_1_1/102-1786598-6301708?ie=UTF8&s=books&qid=1173043516&sr=1-1)
-- so of course, I picked up a copy.

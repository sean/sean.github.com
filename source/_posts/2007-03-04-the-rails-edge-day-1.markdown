---
author: admin
date: '2007-03-04 16:02:54'
layout: post
slug: the-rails-edge-day-1
status: publish
title: The Rails Edge Day 1
wordpress_id: '100'
categories:
- Programming
- Ruby
- Training
---

[![image](http://seanmountcastle.com/wp-content/uploads/2007/02/railsedgewhite.jpg)](http://www.pragmaticstudio.com/therailsedge/index.html)

Recently, I attended [The Rails
Edge](http://www.pragmaticstudio.com/therailsedge/index.html) conference
run by [The Pragmatic Studio](http://www.pragmaticstudio.com/). It was a
single track event with some of the best and brightest folks in the
Rails and Ruby community. The speaker line-up was as follows:

-   [Dave Thomas](http://pragdave.pragprog.com/pragdave/)
-   [Mike Clark](http://clarkware.com/cgi/blosxom)
-   [James Duncan Davidson](http://blog.duncandavidson.com/)
-   [Chad Fowler](http://chadfowler.com/)
-   [Justin Gehtland](http://www.relevancellc.com/)
-   [Stuart Halloway](http://www.relevancellc.com/)
-   [Marcel Molina, Jr.](http://www.vernix.org/marcel/)
-   [Jim Weirich](http://www.onestepback.org/)
-   [Bruce Williams](http://codefluency.com/)

Read on for a description of the first day's sessions. After a brief
welcome from Mike Clark, Dave Thomas launched the conference with his
first session entitled "Metaprogramming Ruby: Extending Ruby for Fun and
Profit." He showed how classes were open by re-opening the String class
and adding a method to encrypt the contents of the string and then he
reimplemented the Rails modifications to Fixnum (so that
3.days.from\_now works). He showed how code could be executed in the
context of a class as that class was loaded (i.e. we could conditionally
include/exclude methods in the class). Adding *macros* to Rails
controllers was achieved using the **Module.included** method to detect
when the Module was included in a controller and then perform some
actions on that controller (such as adding methods to it). Next the
power of **eval** and **instance\_eval** was displayed--though he
cautioned that eval'ing user input could be very dangerous. Finally, he
showed how **define\_method** could be used to create new methods on a
controller like so:

~~~~ {lang="ruby"}
class ApplicationController < ActionController::Base
  def self.search_action_for(table_name)
    model = table_name.to_s.classify.constantize
    define_method("search_for_#{table_name}") do
      @title = "Your #{Inflector.humanize(table_name)}"
      @results = model.find(:all, :conditions => ["name like ?", "%#{params[:term]}%"])
      render :template => '/shared/search_results'
    end
  end
end
~~~~

and you would use it like this:

~~~~ {lang="ruby"}
class UsersController < ApplicationController
  search_action_for :users
end
~~~~

Following a short break, Mike Clark gave an overview of what's new in
Rails 1.2. Mike started off by listing the various virtual machines that
are under development for Ruby, such as
[YARV](http://www.atdot.net/yarv/),
[JRuby](http://jruby.codehaus.org/Home),
[Rubinius](http://blog.fallingsnow.net/rubinius/),
[RubyCLR](http://www.rubyclr.com/),
[Cardinal](http://cardinal2.rubyforge.org/), and
[smalltalk.rb](http://smallthought.com/avi/?p=19). Then he went on to
discuss migrations, plugins, rich models, parameter filtering,
deprecations, integration test (a testing DSL), running Rails in
headless mode (via the console), form\_for, RJS, serialization,
respond\_to, named routes, CRUD/REST, syndication, ActiveResource,
Mongrel, Capistrano, full-featured scaffold, Amazon S3, and Rinda/DRB.
Next Stu gave his talk on Ruby Idioms for Rails Programmers. He covered
the explicit API (which was Java code) and the implict API of today and
how the implict API is implemented as many small modules included into
big classes. Personalized Object Models (POM) were next, this is done by
augmenting other people's code, implementing DSLs with method-on-demand,
using method\_missing sparingly, and being domain specific. His
presentation is available at [CodeCite](http://www.codecite.com). Chad
was up next with his talk on The Meaning of CRUD. This presentation went
into the meaning of CRUD (Create, Read, Update, Destroy), RESTful routes
and the SimplyHelpful plugin. This topic has been discussed at length
elsewhere so I won't go into the details. But Chad is always a great
speaker and I enjoyed his presentation immensely. Following lunch there
was a switch to the schedule as Jim Weirich hadn't arrived yet. So
Justin stepped up and gave his talk on Rails and Ajax. This presentation
is also available online at [CodeCite](http://www.codecite.com). Justin
started off with a discussion of the
[Prototype](http://www.prototypejs.org/) JavaScript library with some
simple examples, then launched into the various effects possible with
[Script.aculo.us](http://script.aculo.us/). To wrap up, RJS was
described along with JSON. This led nicely into Marcel's talk on Reusing
RJS. He started off by showing some duplicated RJS code into two actions
within the same controller. For the first pass he tried extracting out a
new private method with the duplicate code, but unfortunately it didn't
work since it was in the wrong scope. So he extracted it out to a helper
and ensured that it could be passed the page object. This worked, but
calling the new method looked really ugly (Marcel called this Pythonic).
His next approach was to monkey patch JavaScriptGenerator right in Rails
-- invoking the new methods looked great, but he decided it wasn't worth
it to abuse method\_missing plus it became a maintenance headache. So
Marcel went back to the origins of RJS and explained some of the design
choices that he and Sam made and reminded us that << just adds raw
JavaScript to the stream. So he decided just to wrap update\_page in the
helper and then reuse the code with << like so:

~~~~ {lang="ruby"}
module ArticlesHelper
  def replace_article(article)
    update_page do |page|
      page[article].replace :partial => article
      page.replace_html :controls, :partial => 'shared/controls'
    end
  end
~~~~

and then he reused it:

~~~~ {lang="ruby"}
  def show
    render :update do |page|
      page << replace_article(@article)
    end
  end
  def update
    @article.update_attributes(params[:article])
    render :update do |page|
      page << replace_article(@article)
      page.visual_effect :highlight, dom_id(@article)
    end
  end
~~~~

The great thing about this is that you can also reuse that JavaScript in
your views as well:

~~~~ {lang="html"}
Edit Article
<% article_form(article) do |form| %>
  <%= render :partial => 'articles/form', : object => form %>
  <%= submit_tag 'Save changes' %> or
  <%= link_to_function 'Cancel', replace_article(article) %>
<% end %>
~~~~

After a short break, several conference attendees came up and demo'ed
their apps. Some of the presenters were: [Erik
Hatcher](http://www.ehatchersolutions.com/) who presented on his Solr.rb
project (the acts\_as\_solr.rb plugin) and his work at UVA categorizing
literature; [Ryan Garver](http://rgarver.blogspot.com/) spoke about the
[AWS Console](http://info.aws-console.com/) which makes it really easy
to setup your server on Amazon Web Services EC2; [Ken
Collins](http://www.metaskills.net/blog/colophon/who-is-to-blame-for-this)
spoke about [Homemarks](http://www.homemarks.com/), simple project-based
bookmarking, which he is open sourcing; Finally, someone from the
[FiveRuns](http://fiveruns.com) team demo'ed their hosted systems
management solution. While it certainly looks nice, I know my employer
would never use it as it requires installing their software on your
systems so it can report back to them. After dinner, Dave Thomas gave
the opening keynote, entitled Fear of Flying. It was very good and I
believe it was the same as the EuroRailsConf keynote that he gave, which
is available
[online](http://video.google.com/videoplay?docid=-7327520943909344563).
Overall, the first day of The Rails Edge went very well and got me
re-energized to work on my projects with several new ideas and a fresh
perspective. I don't think you can put a price on that.

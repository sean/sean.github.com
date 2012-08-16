---
author: admin
date: '2007-03-04 18:09:13'
layout: post
slug: february-nova-ruby-users-group
status: publish
title: February NoVA Ruby Users Group
wordpress_id: '103'
categories:
- Programming
- Ruby
---

This month we had [Chad Fowler](http://www.chadfowler.com/) as a guest
speaker at NoVA RUG. His talk was entitled "Quick and Clean Rails
Development." Here's the abstract for his talk:

> Rails is all about speed. It has been said that Rails programmers can
> develop software ten times faster than those programming in
> technologies such as .NET or J2EE. Rails itself is evolving at the
> speed of light. But, to paraphrase Martin Fowler's RailsConf 2006
> keynote, with Rails we don't have to choose between Quick and Dirty
> and Slow and Clean. With Ruby, and therefore Rails, we can have both
> speed and maintainability. With Rails, the speed comes naturally. As
> it turns out, the cleanliness often doesn't. This talk will focus on
> how to make your application development both quick \_and\_ clean.

Read on for a summary of Chad's talk. **Update**: I found a video of
this talk which Chad gave at Rails eXchange in London
[here](http://video.google.com/videoplay?docid=-5067787434087643104&hl=en-GB).
This presentation was a grab-bag of techniques to clean-up your Rails
code, making it easier to maintain. Stick with CRUD. If you find
yourself deviating from the create, show, update and destroy methods in
your controller you need to rethink your design/schema so that you can
map it to CRUD. Chad said that placing this constraint on his controller
design led to much cleaner and easier to maintain code. *Over Do MVC*

-   No SQL in your controllers (or views). Basically if you're calling
    find with multiple arguments in your controller, you're violating
    this principle. Here's some before and after code:

~~~~ {lang="ruby"}
class PostsController < ApplicationController
def index
@recent_articles = Post.find(:all, : order => "created_at DESC", :limit => 5)
@recent_visits = @user.visits.find(:all, : order => "created_at DESC", :limit => 5)
end
end
~~~~

    and after:

~~~~ {lang="ruby"}
class Post < ActiveRecord::Base
def self.recent(limit = 5)
self.find(:all, : order => "created_at DESC", :limit => limit)
end
end
class User < ActiveRecord::Base
has_many :visits do
def recent(limit = 5)
self.find(:all, : order => "created_at DESC", :limit => 5)
end
end
end
class PostsController < ApplicationController
def index
@recent_articles = Post.recent
@recent_visits = @user.visits.recent
end
end
~~~~

-   No more than four lines per action in the controller
-   No code in your view. This means putting your code in the helpers
    (or modules included by your helpers) to keep the view clean. Chad
    also recommended investigating other templating libraries like
    Amrita.

I really hope that Chad will make this presentation available online as
there were some great examples in his slides. Next month I'll be
presenting at NoVA RUG on RESTful Rails (CRUD, REST and, if I can fit it
in, ActiveResource).

---
author: admin
date: '2006-06-05 17:25:00'
layout: post
slug: a-look-at-rails-engines
status: publish
title: A Look at Rails Engines
wordpress_id: '19'
categories:
- Programming
- Ruby
- Telecom
---

A few months ago I heard about the
’[controversy](http://weblog.rubyonrails.org/articles/2005/11/11/why-engines-and-components-are-not-evil-but-distracting)’
surrounding [Rails Engines](http://www.railsengines.org/) and meant to
check them out, though work/life intervened and I never got around to it
until now. So last week I setup a [RubyForge](http://www.rubyforge.org)
project (thanks [Rich](http://richkilmer.blogs.com/) and
[Tom](http://tomcopeland.blogs.com/)!) called
[BlogEngine](http://rubyforge.org/projects/blogengine/) to learn the ins
and outs of creating a Rails Engine. At first blush, Rails Engines seem
to be plugins on steroids, incredibly powerful but somewhat dangerous.
For those who haven’t yet visited the Rails Engines website:

> Engines are a way of dropping in whole chunks of functionality into
> your existing application without affecting any of your existing code.
> Engines are like a slice of an application from top (views/helpers) to
> bottom (models) which can be dropped into an existing application and
> appear as if they always existed in the normal /app directory.
> Developers can selectively override parts of Engines as they need to
> handle their application (such as changing the user/home view to
> display a silly name, without affecting the rest of the Engine).
> Engines can be as lightweight as the simplest plugin, or as
> full-featured as your your (*sic*) imagination can conceive.

[James Adam](http://www.railsengines.org/wiki/pages/James+Adam) has done
an excellent job documenting the Rails Engine plugin and the Wiki with
how to create your own Rails Engines. That said, while I found the
development of my BlogEngine to be relatively painless (as it was
developed like any other Rails apps), once it was converted to a Rails
Engine it was difficult to integrate into another project and get the
interaction with the
[LoginEngine](http://www.railsengines.org/login_engine) working
smoothly. The Rails Engines plugin does make it dead simple to add a lot
of functionality into your application with very little work. But due to
the wholesale inclusion of models, views and controllers it does take a
bit of work to get the engine tweaked to your liking (at least so that
it integrates into your existing Rails app nicely). To create your own
Rails Engine you would create a new Rails project, write your tests and
app code as normal and then perform the following steps:

1.  Install the Rails Engine plugin:

        ./script/plugin install engines

2.  Generate the directory structure for your new engine and choose a
    license:

        ./script/generate engine MyNewEngine

3.  Move your engine files from the main app directory into the
    vendor/plugins/my\_new\_engine directory:

        mv app/models/my_model.rb vendor/plugins/my_new_engine/app/models/
        mv db/migrate/001_initial.rb vendor/plugins/my_new_engine/db/migrate/
        mv app/controllers/my_controller.rb vendor/plugins/my_new_engine/app/controllers/
        mv app/views/my vendor/plugins/my_new_engine/app/views/

4.  Modify config/environment.rb to start your engine:

        Engines.start :my_new_engine

5.  Include your new engine in ApplicationController/Helper:

        class ApplicationController < ActionController::Base
        include MyNewEngine
        end
        module ApplicationHelper
        include UploadEngine
        end

6.  Modify vendor/plugins/my\_new\_engine/lib/my\_new\_engine.rb with
    any configuration options you require and add any modules you need
    to vendor/plugins/my\_new\_engine/lib/my\_new\_engine/
7.  Read and then update the README in vendor/plugins/my\_new\_engine so
    that you and others can figure out how to use your new engine.

Some of the issues I had with Rails Engines were:

-   **Model handling**. For the BlogEngine, I relied upon the
    LoginEngine, unfortunately I had to enhance the User model with
    relationships to blogs, articles, etc – thankfully the LoginEngine
    was designed such that I could simply include the
    LoginEngine::AuthenticatedUser module. Thus you must take great care
    when developing an engine so that the models are setup properly.
-   **Migration handling**. Migrations with engines can be very
    dangerous as you must trust the source of the engine (though this is
    true for all code you incorporate into your application). That said,
    it would be nice if running

        rake migrate

    also ran the migrations for each of the installed engines. Note that
    the order in which the migrations is run is very important if the
    engines have dependencies on on another. Which brings me to the next
    item …

-   **Engine dependencies**. The init\_engine.rb should allow you to
    require any pre-requisite engines. Then Engine.start wouldn’t care
    in which order the engines were started since they would be
    self-ordering.
-   **Referencing image assets**. The engines plugin provides support
    for accessing your CSS stylesheets and Javascript files via

        <%= engine_stylesheet "" %>

    and

        <%= engine_javascript "" %>

-   **Referencing CSS and Javascript**. In the above case you had to use
    the engine name as your .css and .js filenames or provide the
    additional filenames on the same line after the engine name. Since
    the engine should know where the view file came from it should look
    in that engine’s public directory for the stylesheet/Javascript
    files.
-   **Testing Engines with fixtures**. As long as you don’t allow the
    users of your engine to change your table names the fixtures you’ve
    written for your tests will work fine. Unfortunately, once the table
    names have changed it is up to the user to rename the fixture files.

In theory, Rails Engines appear to be quite nice, but in my limited
amount of time using them I prefer to reuse plugins, write my own code
from scratch or reuse other classes in lib.

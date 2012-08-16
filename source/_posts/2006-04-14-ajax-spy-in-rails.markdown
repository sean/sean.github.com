---
author: admin
date: '2006-04-14 16:03:00'
layout: post
slug: ajax-spy-in-rails
status: publish
title: Ajax Spy in Rails
wordpress_id: '21'
categories:
- JavaScript
- Programming
- Ruby
- Telecom
---

I was playing around with [Digg](http://www.digg.com) this morning and
noticed [Digg Spy](http://www.digg.com/spy). At first I thought it was
really cool and wondered how they did that. Then I realized it’s just a
bit of Ajax and, as anyone who’s read [Pragmatic
Ajax](http://pragmaticprogrammer.com/titles/ajax/index.html) knows, Ajax
is easy! So read on for how I implemented an Ajax spy in
[Rails](http://www.rubyonrails.org) and to download the code. The first
thing I did was generate a controller and model using [Rich White’s
excellent](http://www.height1percent.com/)[AjaxScaffold
Generator](http://ajaxscaffold.height1percent.com/), called
EntriesController and Entry, respectively. This gave me a nice way to
create new entries easily. After that I added some basic login/signup
support so that the entries could be associated with users. So far,
nothing out of the ordinary. Next I created a new controller called
SpyController, this is where all of the action happens. I added a basic
list method which just returns all of the entries in the DB (sorry, no
pagination), this is what we initially call when displaying the page.
Then I added an update method which will be called periodically to
retrieve new entries, it looks like this:

~~~~ {lang="ruby"}
def update
  last_update = Time.parse(params[:timestamp])
  # locate all of the entries created since the last update
  @entries = Entry.find(:all, :order => 'created_at ASC', :conditions => [ 'created_at > ?', last_update.to_s(:db) ]);
  if !@entries.empty?
    render :update do |page|
      for entry in @entries
        page.insert_html(:top, 'spy-list', :partial => 'entry', :object => entry)
        page.visual_effect :highlight, "spy-item-#{entry.id}"
      end
    end
  end
end
~~~~

At this point I needed some JavaScript to call the update method, so put
the following code in application.js:

~~~~ {lang="ruby"}
var updateInterval = 5000; // update every 5 seconds
var timestamp = new Date().toUTCString();
var timer;

function go() {
  timer = setInterval('update()', updateInterval);
}

function update() {
  url = "/spy/update";
  new Ajax.Request(url, {
               asynchronous: true,
               method: "get",
               parameters: "timestamp=" + timestamp,
               onSuccess: function(request) {
                 timestamp = new Date().toUTCString();
               }
  });
}
~~~~

The JavaScript update method calls the SpyController’s update method and
passes a timestamp as a parameter (this is the time when the page was
loaded, initially, and later the timestamp is updated as new entries are
retrieved). To bring it all together I had to add on onload to the
list.rhtml view for the SpyController, like this:

~~~~ {lang="html"}
This page updates automatically!



  <% if !@entries.empty? %>
    <%= render :partial => 'entry', :collection => @entries, :locals => { :hidden => false } %>
  <% end %>
~~~~

That’s all there is to it. See, I told you it’s easy! You can download
the code from
[here](http://seanmountcastle.com/wp-content/uploads/2007/05/spy.zip)
**(Updated for Rails 1.2.3)**.

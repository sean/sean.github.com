---
author: admin
date: '2008-02-23 21:41:08'
layout: post
slug: advanced-rails-recipes
status: publish
title: Advanced Rails Recipes
wordpress_id: '136'
categories:
- Miscellaneous
---

Almost a year ago, I submitted three recipes to [Advanced Rails
Recipes](http://pragprog.com/titles/fr_arr). Unfortunately, one which
was originally selected back in June has been dropped from the book as
it's not really advanced. So I thought I'd post it here for everyone to
enjoy.

### Using AJAX with REST

#### Problem:

You have finally mastered REST (Representational State Transfer) and
wish to enhance your application with JavaScript but don't know which of
the resource URLs to call.

#### Ingredients:

This recipe requires Rails 1.2 or later as it relies on RJS for the Ajax
portion and REST for the controller design.

#### Solution:

In this example we need users to be able to register (and unregister)
for meetings so that we can properly report attendance. So we have three
models: User, Meeting and Registration.

Since Registrations are associated with a specific meeting, we've
created them as a nested resource, like so:

~~~~ {lang="ruby"}
  map.resources :meetings do |meetings|
    meetings.resources :registrations
  end
~~~~

To register for a meeting we want to create a new Registration instance
tied to the Meeting and User. Unregistering from a meeting should
destroy the Registration object. So our RegistrationsController looks
like this:

~~~~ {lang="ruby"}
  # POST /registrations
  def create
    @meeting = Meeting.find(params[:meeting_id])
    current_user.register_for(@meeting)
    respond_to do |format| 
      format.html { redirect_to meetings_url }
      format.js   # create.rjs
      format.xml  { head :ok }
    end
  end

  # DELETE /registrations/1
  def destroy
    @registration = Registration.find(params[:id])
    @registration.destroy
    respond_to do |format|
      format.html { redirect_to meetings_url }
      format.js   # destroy.rjs
      format.xml  { head :ok }
    end
  end
~~~~

In the view we want to use Ajax to allow the user to modify their
registration, so we need to use link\_to\_remote:

~~~~ {lang="ruby"}
  <% if !current_user.registered_for(meeting) -%>
    <%= link_to_remote "Register!", :url => registrations_path(meeting), 
                                  :meeting_id => meeting.id, :method => :post %>
  <% else -%>
    <%= link_to_remote "Unregister", 
                                  :url => registration_path(meeting, 
                                             current_user.registration_for(meeting)),  
                                  :confirm => 'Are you sure?', :method => :delete %>
  <% end -%>
~~~~

The RJS to update the page looks like this:

~~~~ {lang="ruby"}
page[" meeting_#{@meeting.id}".to_sym].replace_html 
       :partial => 'shared/meeting', :object => @meeting
page[" meeting_#{@meeting.id}".to_sym].visual_effect :highlight, :duration => 5
~~~~

#### Discussion:

The resource URLs provided by Rails are extremely useful, but they can
be confusing. Tools like [FireBug](http://www.getfirebug.com/) make it
easy to see what is going on behind the scenes. When developing Rails
applications, it is usually easier to develop without Ajax and then go
back and add Ajax to those portions of the application where it would
make sense. With this approach, you can gracefully degrade your service
back to the original mode for those who don't have or don't enable
JavaScript. It also allows you to click through your application with
FireBug enabled and watch which URLs are hit and with which methods
(GET, POST, PUT, or DELETE).

The table below outlines which resource URLs to use with your remote
helpers:

  Intent                           Action    Resource URL                                                                  Method
  -------------------------------- --------- ----------------------------------------------------------------------------- --------
  Creating a new instance          create    plural form of model name (i.e. registrations\_path)                          POST
  Retrieving an instance           show      singular form of model name with id (i.e. registration\_path(registration)    GET
  Retrieving all instances         index     plural form of model name (i.e. registrations\_path)                          GET
  Modifying an existing instance   update    singular form of model name with id (i.e. registration\_path(registration))   PUT
  Deleting an existing instance    destroy   singular form of model name with id (i.e. registration\_path(registration))   DELETE

Once you are comfortable with the resource URLs, adding Ajax to your
RESTful is much easier.

#### Further Reading:

If you are unfamiliar with REST, read Chapter 20 of [Agile Web
Development with Rails, 2nd Edition](http://pragprog.com/titles/rails2)
by Dave Thomas and David Heinemeier Hansson (Pragmatic Programmers,
2006). There is also a nice screencast on the subject from
[PeepCode](http://peepcode.com/articles/2006/10/08/restful-rails).

For more on Ajax in Rails, you can check out [Ajax on
Rails](http://www.oreilly.com/catalog/9780596527440/index.html) by Scott
Raymond (O'Reilly & Associates, 2007).

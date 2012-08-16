---
author: admin
date: '2005-10-21 01:37:00'
layout: post
slug: ajax-autocompletion-with-rails
status: publish
title: Ajax Autocompletion with Rails
wordpress_id: '36'
categories:
- Programming
- Ruby
---

First, I'd like to apologize for the long delay in posting to my blog.
My wife and I had our second child at the end of September and things
have been hectic since then. I was playing around with the [ajax
autocompletion](http://script.aculo.us/demos/ajax/autocompleter) code
from script.aculo.us but couldn't get it working in my own code. It
turns out that in addition to prototype.js in your layout RHTML, you
also need to include effects.js and controls.js, so the code looks as
follows:

      <%= javascript_include_tag :defaults %>

In the controller, I wrote my own autocomplete\_for\_XXX method since I
wanted to search several different fields in my database. Note that
there is probably a much better way to achieve the following without
making three different calls to find and without making calls using LIKE
%foo% ...

      def auto_complete_for_resource_name
    @search_term = params[:resource][:name].strip.downcase
    @resources = Resource.find(:all,
    :conditions => [ 'LOWER(name) LIKE ?',
    '%' + @search_term + '%' ],
    :order => 'name ASC',
    :limit => 10)
    @resources.concat(Location.find(:all,
    :conditions => [ 'LOWER(name) LIKE ?',
    '%' + @search_term + '%' ],
    :order => 'name ASC',
    :limit => 10))
    @resources.concat(EqType.find(:all,
    :conditions => [ 'LOWER(name) LIKE ?',
    '%' + @search_term + '%' ],
    :order => 'name ASC',
    :limit => 10))
    @resources.uniq!
    render :partial => 'resources'
    end

You'll need a partial \_resources.html such as this:

    <ul class="resources">
    <% for resource in @resources do -%>
    <li class="resource">
    <div class="name"><%=h resource.name %></div>
    </li>
    <% end -%>
    </ul>

Finally, in the RHTML where you want the autocompletion to appear you
need to add a text\_field\_with\_autocomplete, but since I'm using this
in a search field (similar to Google's usage), I needed to place it
within a form:

    <%= start_form_tag :action => 'search' %>
    <label for="reservation_resource">Search</label>
    <%= text_field_with_auto_complete :resource, :name %>
    <%= submit_tag 'Search' %>
    <%= end_form_tag %>

That's all there is to it. Hope that helps -- all of the other
documentation I've seen only has you include prototype.js and that's
where I ran into difficulty.

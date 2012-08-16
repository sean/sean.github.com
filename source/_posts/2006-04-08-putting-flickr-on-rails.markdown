---
author: admin
date: '2006-04-08 20:35:00'
layout: post
slug: putting-flickr-on-rails
status: publish
title: Putting Flickr on Rails
wordpress_id: '23'
categories:
- JavaScript
- Programming
- Ruby
---

You know that really cool screencast at the [Ruby on
Rails](http://www.rubyonrails.com) website where Rails is used to create
a [Flickr interface in 5
minutes](http://media.rubyonrails.org/video/flickr-rails-ajax.mov)?
Well, I followed the screencast and built my own copy and then I
enhanced it with some additional JavaScript (Lightbox style preview of
the images and a blind-up on subsequent searches). Note that in the
course of making my changes I found out the proper ordering of the
JavaScript callbacks (see
[this](http://api.rubyonrails.com/classes/ActionView/Helpers/PrototypeHelper.html#M000412))
– even though you would think that :before would be called prior to a
:complete, it doesn’t always happen that way (so sometimes the new
results are blinded-up and not shown).

I’ve been meaning to upload this for awhile, but just haven’t gotten
around to it. So today I updated it to work with Rails 1.1.1 (though
didn’t switch the Ajax-y goodness over to RJS). Hopefully other folks
can benefit from the code. To run it all you have to do is first install
the flickr ruby gem, like so:

    sudo gem install flickr

and unzip and run this [Rails
app](http://seanmountcastle.com/wp-content/uploads/2007/02/flickr.zip).
Enjoy!

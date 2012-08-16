---
author: admin
date: '2005-10-30 07:18:00'
layout: post
slug: creating-printable-documents-with-ruby
status: publish
title: Creating Printable Documents with Ruby
wordpress_id: '35'
categories:
- Programming
- Ruby
---

Austin Ziegler has a great introduction to [Creating Printable Documents
with Ruby](http://www.artima.com/rubycs/articles/pdf_writer.html) over
at [Artima](http://www.artima.com/index.jsp). His article is part of the
new [Ruby Code & Style](http://www.artima.com/rubycs/index.html) online
journal. Austin covers all of the basics in his article and, though I
had to recompile ruby for Mac OS X, I was able to get through all of the
examples. One thing that disappointed me about PDF::Writer was that it
only supports JPG and PNG images (and for PNG only 8-bits images are
supported). For my usage, I found the section on [partial document
generation](http://www.artima.com/rubycs/articles/pdf_writer4.html) the
most useful since I have to generate bills from Ruby on Rails by
modifying a standard boiler-plate letter. If you're interested in using
FPDF instead,
[Robby](http://www.robbyonrails.com/articles/2005/06/04/rendering-a-erb-template-stored-in-the-database-to-a-pdf)
has a good overview on generating PDF documents from an ERb template.

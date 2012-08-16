---
author: admin
date: '2006-06-28 21:12:28'
layout: post
slug: june-novarug-meeting
status: publish
title: June NovaRUG Meeting
wordpress_id: '18'
categories:
- C/C++
- Programming
- Ruby
- Telecom
---

Tonight at [NovaRUG](http://www.novarug.org/) we had two presenters:
[Tom Copeland](http://tomcopeland.blogs.com/) and Xandy Johnson. Tom
spoke about extending Ruby with C extensions and Xandy spoke about
[Rake](http://rake.rubyforge.org/). Tom walked through the ‘evolution’
of his [Revolution](http://revolution.rubyforge.org/) Ruby library which
provides Ruby bindings for the [GNOME Evolution
PIM](http://www.gnome.org/projects/evolution/) (via the e-book library).
His first example was the straight-forward way of extending Ruby with C
(the code example looked very similar to those in Chapter 21 of the
[Pick Axe](http://pragmaticprogrammer.com/titles/ruby/index.html)).
There’s also an
[article](http://www.onlamp.com/pub/a/onlamp/2004/11/18/extending_ruby.html)
at OnLamp about extending Ruby with C. His second example was more
interesting, for me at least – he showed how to use [Ruby
DL2](http://rubyforge.org/projects/ruby-dl2/) to export C functions into
a Ruby module using pure Ruby code! It’s as easy as this:

    require 'dl/import'

    module Foo
    extend Importer

    dlload 'libc'

    extern "size_t strlen(const char *)"
    end

    s = "Hello, World!"
    puts "#{s} is #{Foo.strlen(s)} characters long."

After that, Tom spoke briefly about [SWIG](http://www.swig.org/) for
[Ruby](http://www.goto.info.waseda.ac.jp/~fukusima/ruby/swig-e.html).
Unfortunately, he had difficulty getting it to work and no one else
present had been successful with it (or was willing to speak about it).
Xandy was up next with an excellent overview of [Jim
Weirich’s](http://onestepback.org/)
[Rake](http://onestepback.org/articles/buildingwithrake/). He started
off with a nice poem entitled ‘Ode to Rake’ which I will not republish
as he was going to send it over to Jim and I don’t want to ruin that
(there were suggestions that [\_why](http://www.whytheluckystiff.net/)
should turn it into a song). Xandy provided an overview of other popular
build tools like [Make](http://www.gnu.org/software/make/) and
[Ant](http://ant.apache.org/) (and we all had a good time [complaining
about Ant](http://www.jroller.com/page/obie?entry=ant_was_a_one_day)).
Next he delved into the Rakefile sytax (after reminding us that Rake is
all Ruby; so anything you can do in Ruby you can do in Rake) and
discussed tasks, file tasks, directory tasks, rules, FileLists, sh (for
calling out to the shell), ruby (for invoking another Ruby interpreter),
package, rdoc and gem. Near the end of his presentation, he winged his
way through namespaces, dependency import and
[multitask](http://rake.rubyforge.org/classes/Rake/MultiTask.html).
Overall it was an excellent introduction to Rake which whetted our
appetites for a deeper dive into Rake. Next month I’ll be presenting on
[Rails RJS
Templates](http://www.codyfauser.com/articles/2005/11/20/rails-rjs-templates),
on July 19th.

---
author: admin
date: '2005-08-04 10:16:00'
layout: post
slug: oscon-metaprogramming-ruby
status: publish
title: OSCON Metaprogramming Ruby
wordpress_id: '45'
categories:
- Conferences
- OSCON
- Programming
- Ruby
---

Glenn Vanderburg presented on [Metaprogramming
Ruby](http://conferences.oreillynet.com/cs/os2005/view/e_sess/6816). I
thought it was quite interesting as I had only done this previously in
ANSI Common Lisp. My notes from the talk are below.

## Metaprogramming (MP)

-   programming your programming
-   change the way you program in your programming lang
-   transform your general-purpose lang
-   make it domain specific
-   program ing a lang designed for the problem you're solving

Lisp

-   origination of metaprog

Ruby

-   MP is rediscovered
-   style and idioms are changing and adapting
-   rails leverages mp heavily (to great effect)
-   ruby is a natural for MP

Why?

-   Dynamic and reflective
-   everything is open to change
-   blocks allow writing new control structs (add continuations to get
    fancy)
-   Most declarations are executable statements
-   only slightly less malleable than Lisp (no macros)
-   a fantastic syntax
    -   neutral and unobtrusive
    -   enough to distinguish different kinds of constructs
    -   not enough to complicate straightforward statements

Built-in Examples

-   declaring object properties: attr\_reader :id, :age attr\_writer
    :name attr\_accessor :color
-   These are just methods from Module (not syntax)
-   How are they written? Unfortunately, in C. Still instructive but
    doesn't tell you how to do it in Ruby.

Mathieu Bouchard's X11 Library

-   Wrote a DSL which defined the X11 Protocol Spec in a way similar to
    the way in which the spec itself was written.

Styles Have Changed

-   A DSL was created in similar fashion for the Java Debug Wire
    Protocol.
-   executable protocol spec which could be printed from source

Dave Thomas's Summer Project

-   RubyConf 2002 "How I spent my summer vacation"
-   Created a DSL which would build objects based on the contents of a
    DB or generate the DDL for the database or generate the graph code
    for an ER diagram.

How to think about metaprogramming

-   Def new constructs for your programming lang
-   Ok, but constructs to do what?
-   Whatever your DSL needs to do.

Another way to think about it

-   a new bag of tricks for eliminating duplication (and other smells)
    from your code
-   two ways to go about it: write your app and extract (Rails), layout
    design first (ActionStep).

Conventional Constructs

-   DSLs need: types, literals, declaration, expressions, operators,
    statements, control structs

Most DSLs also deal with things you don't usually find in gp langs

-   context-dependence
-   commands and sentences
-   units (unit conversion)
-   large vocabularies ( sometimes unbounded)
-   hierarchy

Contexts

-   Establish a context for a set of statements:
    -   constrain those statements to the context
    -   multiple, concise operations on the context

-   What's a context? A scope.

Commands & Sentences

-   multipart, complex statements or declarations

field(autoinc, :reg\_id, pk)

-   It's just a method call (optional parens are handy for sentences
-   First param is a method call: restricts the arguments to predefined
    alternatives (prevent errors)
-   Second param is a symbol: restrict syntax to goo name-like strings
-   Additional params are method calls:
    -   options, constraints
    -   methods return objects that encode constraints

Units

-   general purpose langs deal with scalars
-   most DSLs deal with quantities

Impl Units

-   Classes representing quantities
    -   don't forget to support math
    -   user operator overloading if it makes sense
    -   may require mixed-based arithmetic (time certainly does)

-   Next: natural expression

Large Vocab

-   Roman numerals (Roman.CCXX, Roman.XLII)
-   Jim Weirich's XmlMarkup class (used in Rails):

How do you impl large vocabularies?

-   override method\_missing
-   Be careful! Bugs lurk here. Sometimes method missing intercepts
    something that really is a name in an outer scope -- it's also hard
    to find bugs if you misspell a real method name.

Hierarchy

-   XmlMarkup again (see slides)

How to implement?

-   call from method\_missing:

You could use instance\_eval to avoid typing xm. before every call. But
don't. If you make a method call within the block and use
instance\_eval, the method is looked up in the wrong context and get a
no such method error. Slides are available
[here](http://www.vanderburg.org/Speaking/Stuff/oscon05.pdf).

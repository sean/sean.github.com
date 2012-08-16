---
author: admin
date: '2006-07-27 20:34:00'
layout: post
slug: oscon-sessions-day-one
status: publish
title: 'OSCON: Sessions Day One'
wordpress_id: '9'
categories:
- Conferences
- OSCON
- Programming
- Python
- Ruby
- Software
---

Below are my notes from the first day of sessions here at
[OSCON](http://conferences.oreillynet.com/os2006/). The talks I attended
were:

-   Using Ruby on Rails to Build a Massive Multiplayer Game
-   Easy AI with Python
-   Driving Rails Deep into the Back Office
-   Streamlined
-   Ruby for Java Programmers
-   Coding Wizard, Savvy Trader

In the morning, I attended [Michael
Buffingtonâ€™s](http://www.michaelbuffington.com/) talk on [â€œUsing
Ruby on Rails to Build a Massive Multiplayer
Gameâ€?](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8390).
He gave a nice overview of the development of [unroll](http://llor.nu)
discussing isometric art, game design and briefly mentioning
Ajax/JavaScript/script.aculo.us. Hopefully his slides will be available
online shortly. The code for unroll can be downloaded
[here](http://dev.llor.nu). At 11:35am, I was torn between [Mike
Clarkâ€™s](http://clarkware.com/cgi/blosxom) [Deploying Rails Apps with
Capistrano](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8396)
and Raymond Hettingerâ€™s [Easy AI with
Python](http://conferences.oreillynet.com/cs/os2006/view/e_sess/9577).
Since Iâ€™ve already deployed a couple of Rails apps using Capistrano, I
decided to sneak into the Python camp (I ended up sitting right in front
of Guido). I found the presentation quite interesting and will be
looking into similar libraries for Ruby. Raymond covered the following
topics: neural networks for datamining, solving the mastermind game,
solving sudoku, a Bayesian classifer and, finally, a generic puzzle
solver. Though the slides do not appear to be online yet, the Python
code is available
[here](http://aspn.activestate.com/ASPN/Cookbook/Python?author=178123).
After lunch I attended [Obie
Fernandezâ€™s](http://www.jroller.com/page/obie) [Driving Rails Deep
into the Back
Office](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8674).
Obie discussed the PCS project for Barclays Bank in Willmington, DE that
Thoughtworks was involved in. He discussed the various ways in which to
get new technology into the very conservative back office of companies,
such as: Trojan horse (sneaking it in), the race (two parallel
development teams using different technologies), the pilot project, the
rescue (for a failed/failing project) and finally undercutting (but he
cautioned that this de-values the work youâ€™re doing). The three key
points of his talk were:

1.  Optimize and raise your level of abstraction (by creating custom
    DSLs and capturing the requirements in Ruby)
2.  Rails really breathes life into extreme programming (they had one
    week iterations on their project)
3.  Donâ€™t sweat performance and scaling (they had their custom DSL
    generate SQL directly instead of Ruby to keep the performance up â€“
    so you canâ€™t completely ignore performance issues, but theyâ€™re
    usually not as bad as you think)

[Stuart Halloway](http://www.relevancellc.com) demoed the
[Streamlined](http://conferences.oreillynet.com/cs/os2006/view/e_sess/9535)
generator for Ruby on Rails â€˜backendâ€™ admin interfaces. Stuart
described Streamlined as:

1.  Product ready backend scaffolding
2.  Generic enterprise CRUD
3.  The simplicity of ActiveRecord brought to views and controllers

Heâ€™s not going to put the material present online since it is all
basically available via the [Streamlined
blog](http://www.streamlinedframework.org/). Ugo Cei gave a talk
entitled [Ruby for Java
Programmers](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8636)
â€“ which confused many folks who thought it was an introduction to Ruby
for those coming from a Java programming background â€“ instead it
covered how to call Ruby from Java and how to call Java from Ruby. All
of the material is covered in his slides, which are available
[here](http://www.sourcesense.com/transfer/ruby_for_java_programmers.pdf).
At the end of his talk he demoâ€™ed Rails running inside of JRuby which
was pretty neat (though very slow and a bit buggy â€“ sometimes
controllers wouldnâ€™t respond). Since Iâ€™ve already written a C
extension for Ruby, I decided to attend a different kind of talk,
[Coding Wizard, Savvy
Trader](http://conferences.oreillynet.com/cs/os2006/view/e_sess/8755) by
Kartik Subbarao of HP. It was a whirlwind talk covering stocks and
options trading and how to get access to financial information as well
as how to process it using Perl, GreaseMonkey, etc. When the slides are
posted, Iâ€™ll link back to them but here are several of the sites which
were recommended:

-   [Yahoo! Finance](http://finance.yahoo.com)
-   [StockCharts Learning Center](http://www.stockcharts.com/education)
-   [Chicago Board of Exchange Learning
    Center](http://www.cboe.com/LearnCenter)
-   [OptionsXpress](http://www.optionsxpress.com)
-   [WealthLab](http://www.wealthlab.com)
-   [EliteTrader](http://www.elitetrader.com)
-   [OpenTick](http://www.opentick.com)
-   [StockTickr](http://www.stocktickr.com)
-   [SocialPicks](http://www.socialpicks.com)
-   [Marketocracy](http://www.marketocracy.com)


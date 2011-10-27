--- 
title:      Updates on Inspec - Javascript BDD Framework
created_at: 2009-04-24 22:37:01.702107 +08:00
blog_post:  true
filter:
  - textile
tags:
  - javascript
  - BDD
  - inspec
--- 

For the past two weeks, a lot of improvements has been done for "Inspec":http://github.com/aq1018/inspec, here is the list:

* Better scoping / sandboxing
* Support for "Rhino":http://www.mozilla.org/rhino/, "SpiderMonkey":http://www.mozilla.org/js/spidermonkey/, "Johnson":http://github.com/jbarnette/johnson/tree/master/ and "WSCript":http://en.wikipedia.org/wiki/Windows_Script_Host
* Tested to work with IE7, Firefox 3, Chrome and Safari 3
* Added a lot more specs to test "Inspec":http://github.com/aq1018/inspec
* Fixed a bug where cascading before / after blocks not getting the correct scoping / sandboxing
* Changed BDD syntax a bit to be compatible with "Screw.Unit":http://github.com/nkallen/screw-unit/tree/master
* Shamelessly stole all matchers from "Screw.Unit":http://github.com/nkallen/screw-unit/tree/master
* Added the following matchers:
** beA  - instanceof test
** throwError - takes an function, and see if it throws an error
** respondTo - test if an object has a function
** have - see if an object or array contains something

I'm working on some **advanced features** that requires some pretty big structural changes right now. They are:

* Support for multiple definition of same behaviors.
* Support for multiple definition of before / after blocks.
* Redo shared example groups ( Allows for sharing local scope variables inside shared example groups)

I plan to finish this feature while I'm taking a business trip to Boston this coming Sunday.

For future, the plan follows:

* Spec, spec spec, 100% coverage require!
* Extract and improve rendering logic from HTMLReporter to HTMLReporter.FlatFormatter
* Implement HTMLReporter.NestedFormater
* Implement HTMLReporter.CompactFormater
* Implement ConsoleReporter.FlatFormatter
* Implement ConsoleReporter.NestedFormater
* Implement ConsoleReporter.CompactFormater
* Implement options for choose formatters, need to consider extending
* Add statistics functionality to Reporter Class
* Test on different browsers
* Selective Behavior Execution support
* Prioritize object printing with toString() if object has customized toString
* Documentation
* Make a wiki

That's a lot of stuff to complete! If anyone interested please "fork Inspec":http://github.com/aq1018/inspec
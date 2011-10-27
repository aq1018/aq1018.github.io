---
layout:     post
title:      Updates on Inspec - Javascript BDD Framework
date:       2009-04-24 22:37
comments:   true
tags:
  - javascript
  - BDD
  - inspec
---

*Update: Due to lack of interest and time, Inspec is no longer maintained.
[jSpec][jspec] has become more complete since this post,
and I would recommend using [jSpec][jspec] instead.*


For the past two weeks, a lot of improvements has been done for
[Inspec][inspec], here is the list:

* Better scoping / sandboxing
* Support for [Rhino][rhino], [SpiderMonkey][spidermonkey], [Johnson][johnson] and [WSCript][wscript]
* Tested to work with IE7, Firefox 3, Chrome and Safari 3
* Added a lot more specs to test [Inspec][inspec]
* Fixed a bug where cascading before / after blocks not getting the correct scoping / sandboxing
* Changed BDD syntax a bit to be compatible with [Screw.Unit][screw-unit]
* Shamelessly stole all matchers from [Screw.Unit][screw-unit]
* Added the following matchers:
  * `beA`  - instanceof test
  * `throwError` - takes an function, and see if it throws an error
  * `respondTo` - test if an object has a function
  * `have` - see if an object or array contains something

I'm working on some **advanced features** that requires some pretty big structural
changes right now. They are:

* Support for multiple definition of same behaviors.
* Support for multiple definition of before / after blocks.
* Redo shared example groups ( Allows for sharing local scope variables inside shared example groups)

I plan to finish this feature while I'm taking a business trip to Boston this coming Sunday.

For future, the plan follows:

* Spec, spec spec, 100% coverage require!
* Extract and improve rendering logic from HTMLReporter to HTMLReporter.FlatFormatter
* Implement `HTMLReporter.NestedFormater`
* Implement `HTMLReporter.CompactFormater`
* Implement `ConsoleReporter.FlatFormatter`
* Implement `ConsoleReporter.NestedFormater`
* Implement `ConsoleReporter.CompactFormater`
* Implement options for choose formatters, need to consider extending
* Add statistics functionality to Reporter Class
* Test on different browsers
* Selective Behavior Execution support
* Prioritize object printing with `toString()` if object has customized toString
* Documentation
* Make a wiki

That's a lot of stuff to complete!
If anyone interested please [fork Inspec][inspec]

[inspec]:http://github.com/aq1018/inspec/
[rhino]:http://www.mozilla.org/rhino/
[jquery]:http://jquery.com/
[prototype]:http://www.prototypejs.org/
[mootools]:http://mootools.net/
[yui]:http://developer.yahoo.com/yui/
[extjs]:http://extjs.com/
[johnson]:http://ajaxian.com/archives/johnson-wrapping-javascript-in-a-loving-ruby-embrace-and-arax
[serversidejs]:http://en.wikipedia.org/wiki/Server-side_JavaScript
[rspec]:http://rsepc.info
[inspec]:http://github.com/aq1018/inspec
[comparing]:/blog/2009/04/12/javascript-bdd-test-frameworks-compared
[screw-unit]:http://github.com/nkallen/screw-unit/tree/master
[jspec]:http://visionmedia.github.com/jspec/
[jsspec]:http://jania.pe.kr/aw/moin.cgi/JSSpec
[spidermonkey]:http://www.mozilla.org/js/spidermonkey/
[wscript]:http://en.wikipedia.org/wiki/Windows_Script_Host

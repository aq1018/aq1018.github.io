---
layout:     post
title:      Javascript BDD Test Frameworks Compared
date:       2009-04-12 21:58
comments:   true
tags:
  - javascript
  - BDD
---

Lately, I've been trying to find a good JavaScript BDD style test framework,
and I have come across a few of them such as [Screw.Unit][screw-unit],
[jSpec][jspec], and [JSSepc][jsspec]. They all have their own unique set of features,
and are all very innovative. But I couldn't find a exact fit for my requirements.
While they are all unique in their own ways, and provide some rather innovative
approach to the BDD problem domain, they all have some drawbacks that
I find either not acceptable or not easy to use.

Let's have a little analysis on the strength and weakness of each
frameworks listed above. Ok, you must note that the strength and weakness
I describe is obviously a subjective opinion of my own,
that entirely pertains to my own need. You may find the weakness
I mentioned to be a strength in your case. Don't flame me about it!

##Screw.Unit

Screw.Unit is the one I found to be the closest to my needs,
and I believe it is the most popular BDD JavaScript test framework
at the momenent of this writing.

###Things I like about Screw.Unit

A key feature of Screw.Unit is the support for nested `describes` and
the cascading `before` (and @after@) behavior. For presentation,
it has a good HTML runner that generates good looking HTML pages
to present the test results. You can also create custom matchers
in a easy and declaritive manner to extend Screw.Unit.
Because adding member functions to `Object` is consider a bad practice,
the use of `foo.should be_true` cannot be done easily without polluting the
Object prototype. However they came up with an alternative DSL that
looks like this: `expect(foo).to(equal, true)`


###Things I don't like about Screw.Unit

However, there is a few things I don't like about it.

* No support for shared specs. (aka `it_should_behave_like` in [RSpec][rspec])
* Does not support commandline (due to dependcy on jQuery, DOM, and [concrete Javascript][concrete-javascript]
* Does not support server-side javascript (Same reason above)


##jSpec

jSpec is probably the most innovative JavaScript BDD,
and sometimes I feel that it might be a bit too innovative...

###Things I like about jSpec

In jSpec, you don't write true JavaScript, but a higher level DSL,
which later being parsed and converted to JavaScript and executed.
It also supports nested `describes` and `before`, `after` blocks.
It has a wealth of matchers, and has formatters that supports DOM,
console, and terminal. The size of the script is very small as well.

It is definitely worth checking out.

###Things I don't like about jSpec

*Update: jSpec now supports writing with plain JS and shared behaviors now.*

First, doesn't support shared behaviors.

The DSL looks nice at first sight. In fact I almost mistook it as
RSpec test suits. But after careful analysis, I have a few doubts
about jSpec's DSL. First, from the source code, the DSL to JavaScript
transformation is done using a few lines of Regex only. I'm afraid that
it might not work on edge cases. Next, I looked at the tests for the
Regex transformation, and I found that the tests are not very strict either.
Also, I think this makes error tracking rather difficult,
since the DSL is transformed, it is hard to figure out where the error is if
you run into some edge cases. I'd rather write JavaScript and be at ease,
instead of write poorly supported FrankensteinScript, and have no clue where went wrong.

Another part I don't like about jSpec is the source code is rather cryptic.
I have to say the author of jSpec is a very smart person.
To me, his code is 50% recursive functional rocket science and 50% regex dark magic.
It took me a long time to decrypt how the code is working under the hood,
and I can't say I understood it 100%. This makes contributing and extending
very difficult for most busy programmers (including me) that just want to get the things done.

##JSSpec

JSSepc is probably the oldest Framework that started to tackle the
BDD domain in JavaScript. The initial release is dated July 16, 2007.
Its features are relatively simple compare to above two frameworks.

###Things I like about jSpec

JSSepc's source code is simple and clean, and relatively easy to extend.
It has very original syntax as well, Instead of using `expect(foo).to(equal, true)`,
its format is `value_of(foo).should().be_true()`, a bit less sweet...
However, it is the first (I think) to tackle BDD in JavaScript,
it is nice that they first invented this approach,and paved way for
newer frameworks to learn from. The HTML report is very nice too.
You can selectively run a set of suit right in the browser.

###Things I don't like about jSpec

* It doesn't support nested `describe` blocks.
* It doesn't support shared behaviors.
* Not in active development. (Last commit was Dec. 2008)

[concrete-javascript]:http://http://github.com/nkallen/effen/tree/master
[rspec]:http://rspec.info
[screw-unit]:http://github.com/nkallen/screw-unit/tree/master
[jspec]:http://visionmedia.github.com/jspec/
[jsspec]:http://jania.pe.kr/aw/moin.cgi/JSSpec

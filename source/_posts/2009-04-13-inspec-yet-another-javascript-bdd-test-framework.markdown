--- 
title:      Inspec - Yet Another Javascript BDD Test Framework
created_at: 2009-04-13 21:14:45.382074 +08:00
blog_post:  true
filter:
  - erb
  - textile
tags:
  - BDD
  - javascript
  - inspec
--- 

h3. The "Why" Question

Why? You ask, we already have BDD Frameworks such as "Screw.Unit":screw-unit, "jSpec":jspec, and "JSSepc":jsspec, you want to make _another_ Javascript BDD Test Framework? 

To answer your question, you can take a look at my previous article "comparing strengthes and weaknesses":comparing of the above frameworks. So, please "read it":comparing if you haven't done so.

Now, if you are still with me after finish reading my article, allow me to introduce you a new BDD Test Framework that doesn't suck.

h3. Introducing **"Inspec":inspec**

While coding up "Inspec":inspec, I was trying to fulfill the following features:

* Nested behaviors
* Shared behaviors (aka. @it_should_behave_like@ in "RSepc":rspec)
* Framework agnostic ( You can use it with "jQuery":jquery, "Prototype":prototype, "Mootools":mootools, "YUI":yui, or "ExtJS":extjs. it's your choice. )
* An elegent DSL
* No namespace pollution
* Able to run in browser, "command-line":johnson, and "server side":serversidejs
* A cystal clear API that is easy to understand and extend

Sound awesome! But how does it work?

Here is a small example:

<% uv( :lang => "javascript", :theme => 'blackboard', :line_numbers => false ) do -%>
describe("Inspec", function(){

  it("should work", function(){
    expect(true).toBeTrue();
  })

  it("should fail", function(){
    expect(true).not().toBeTrue();
  })

  it("should be pending")

  describe("with a nested example group", function(){    
    it("should work as a nested example group", function(){
      expect(false).toBe(false);
    })
  })

  // W00t?? It's nesting a shared example group
  itShouldBehaveLike("a shared example group");
})

sharedExamplesFor("a shared example group", function(){
  it("should work as shared example", function(){
    expect(true).toBeTrue();
  })

  // Yes! Shared nested Example Groups!
  describe("with nested example groups in shared", function(){
    it("should work as a nested example group in shared", function(){
      expect(true).toBeTrue();
    })
  })
})
<% end -%>

Here is another example that uses more matchers:

<% uv( :lang => "javascript", :theme => 'blackboard', :line_numbers => false ) do -%>
describe("Matchers", function(){
  describe("TypeMatcher", function(){
    it("should work with String", function(){
      var aString = "abc";
      expect(aString).toBeType("string");
    })
    
    it("should work with Number", function(){
      var aNumber = 123;
      expect(aNumber).toBeType("number");
    })
    
    it("should work with Object", function(){
      var anObject = {};
      expect(anObject).toBeType("object");
    })
 
    it("should work with Boolean", function(){
      var aBoolean = false;
      expect(aBoolean).toBeType("boolean");
    })
    
    it("should work with undefined", function(){
      var undefinedValue;
      expect(undefinedValue).toBeType("undefined");
    })
 
    it("should work with function", function(){
      var aFunction = function(){};
      expect(aFunction).toBeType("function");
    })
  })
  
  describe("InstanceMatcher", function(){
    it("should work with String", function(){
      var aString = new String("abc");
      expect(aString).toBeA(String);
    })
    
    it("should work with Number", function(){
      var aNumber = new Number(123);
      expect(aNumber).toBeA(Number);
    })
    
    it("should work with a class", function(){
      var Foo = function(){};
      var foo = new Foo();
      expect(foo).toBeA(Foo);
    })
 
    it("should work with a sub-class", function(){
      var Foo = Inspec.Class.extend({});
      var foo = new Foo();
      expect(foo).toBeA(Foo);
      expect(foo).toBeA(Inspec.Class);
      expect(foo).toBeA(Object);
    })
  })
  
  describe("ComparisonMatcher", function(){
    it("should work with toBeAtLeast", function(){
      expect(5).toBeAtLeast(5);
      expect(6).toBeAtLeast(5);
    })
    
    it("should work with toBeAtMost", function(){
      expect(4).toBeAtMost(5);
      expect(5).toBeAtMost(5);
    })
    
    it("should work with toBeGreaterThan", function(){
      expect(6).toBeGreaterThan(5);
      expect(5).not().toBeGreaterThan(5);
    })
    
    it("should work with toBeLessThan", function(){
      expect(4).toBeLessThan(5);
      expect(5).not().toBeLessThan(5);
    })
  })
  
  describe("RegexMatcher", function(){
    it("should match correct string", function(){
      var emailRegex = /^([0-9a-zA-Z]([-.\w]*[0-9a-zA-Z])*@([0-9a-zA-Z][-\w]*[0-9a-zA-Z]\.)+[a-zA-Z]{2,9})$/;
      var email = "abc@efg.com";
      expect(email).toMatch(emailRegex);
    })
    
    it("should not match incorrect string", function(){
      var emailRegex = /^([0-9a-zA-Z]([-.\w]*[0-9a-zA-Z])*@([0-9a-zA-Z][-\w]*[0-9a-zA-Z]\.)+[a-zA-Z]{2,9})$/;
      var email = "abc_efg.com";
      expect(email).not().toMatch(emailRegex);
    })
  })
})
<% end -%>

h3. What's working so far

As this is still an early release (Let's see, It is about 3 weeks old so far. Let's call it version 0.0.1??), most of the core features are already working. Here is the list:

* Basic Matchers
* Nested describes
* Shared describes
* Sandboxed Example Scope
* Tested to work in FireFox
* Basic HTML Reporter
* Works with "Rhino":rhino and "Johnson":johnson
* Basic Console Reporter for "Rhino":rhino and "Johnson":johnson

h3. In The Near Future...

While "Inspec":inspec is now working with basic matchers, here are a few things I'd like to add:

* Better syntax and organization of matchers for easier extensions. (Tempted to steal from "Screw.Unit":screw-unit)
* More Matchers. (Makes everyone happy.)
* Work on WScript environment.
* Make sure compatibility with all major browsers. (Helps appricated)
* Allow selective execution of Example groups / Examples.
* Make a better HTML Reporter, that hooks into selective executions.
* Better Documentations. (Helps appricated)
* Better Error messages on Failure and Exception.
* Package and maybe minify(why not?).
* A LOT more rigid and concrete tests to reach 100% coverage. (Also serve as uage examples, helps appricated)

h3. For Developers

I have been very busy with my date job lately, and never have enough time to work on my own projects. Any help is very much appricated. So if you are interested in developing "Inspec":inspec together, just "fork me":inspec, make some improvements, rebase, push, and shoot me a pull request. If you are a regular contributor, your name will be in the co-author's list as well.

h3. Suggestions? Comments?

While I primarily developed this for my own need. I hope this will benefit everyone who has similiar needs. So your suggestions and critics are very welcome. Tell me what you like about it, what you don't like about it, and how "Inspec":inspec can be improved. Sorry that there is nothing like google group or irc or mailing list setup yet. You can leave a comment here, and I will be notified automatically through email. If this project grows bigger, I will setup a google group and an irc channel. But for now, you can either leave a comment, or scroll down to the bottom of the page, and my contact information is on the lower right.

[inspec]http://github.com/aq1018/inspec/
[rhino]http://www.mozilla.org/rhino/
[jquery]http://jquery.com/
[prototype]http://www.prototypejs.org/
[mootools]http://mootools.net/
[yui]http://developer.yahoo.com/yui/
[extjs]http://extjs.com/
[johnson]http://ajaxian.com/archives/johnson-wrapping-javascript-in-a-loving-ruby-embrace-and-arax
[serversidejs]http://en.wikipedia.org/wiki/Server-side_JavaScript
[rspec]http://rsepc.info
[inspec]http://github.com/aq1018/inspec
[comparing]/articles/2009/04/12/javascript-bdd-test-frameworks-compared.html
[screw-unit]http://github.com/nkallen/screw-unit/tree/master
[jspec]http://visionmedia.github.com/jspec/
[jsspec]http://jania.pe.kr/aw/moin.cgi/JSSpec

---
layout: post
title: "Detecting Backone.View Memory Leaks"
date: 2014-05-11 22:09:38 -0700
comments: true
categories:
---

Do you think you write good Backbone.js code? Are you sure your view is not
leaking memory? Are you confident that you properly disposed all your views
by calling `view.remove()`? Are you sure didn't even miss one of them?

No worries, I've got your back. : )

Just include `leaky-registry.js` before you load and initialize your Backbone app. It
will monitor the life cycle of every `Backbone.View` and report any possible
leaky views periodically to your browser console screen.

{% gist bca960d6124a76db63d0 leaky-registry.js %}

Look Ma, No leaks!

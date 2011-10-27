---
layout:     post
title:      Redcloth Ate My notextile Tag
date:       2009-04-07 00:43
comments:   true
categories:
  - ruby
---

While playing with textile and UltraViolet in Webby,
I found textile is re-rendering my UltraViolet generated HTML contents
disregarding \<notextile\> tags.The problem is with UltraVilet versions
4.1.1 to 4.1.9 has ignored this tag somehow.There is even a
[bug ticket](http://jgarber.lighthouseapp.com/projects/13054/tickets/119-notextile-blocks-included-in-following-paragrap) about it.

The solution?

{%codeblock console %}
sudo gem uninstall RedCloth -a
sudo gem install RedCloth -v=4.1.0
{%endcodeblock%}

This installs RedCloth version 4.1.0 which doesn't eat
your `<notextile>` tags and behave correctly for me.
Next I just did a `webby rebuild` and everything worked out for me!

Cheers!

---
title: Plugins for PhoneGap + Windows Phone Mango
date: 2011-11-14 21:24:10 Z
categories:
- app
tags:
- Plugin
- Windows Phone
author: Colene Chow
status: publish
type: post
format: html
---

In early September, we announced PhoneGap for Windows Phone Mango. Since then, we've still been hard at work and [Jesse MacFadyen](http://twitter.com/purplecabbage), a core developer for PhoneGap, recently blogged about adding plugin support to WP7 PhoneGap apps:

> "We recently added plugin support to WP7 PhoneGap apps. I will outline here what you need to do to start extending the functionality for WP7 PhoneGap projects.

All WP7 PhoneGap plugins must derive from the PhoneGap base command. More specifically, the WP7GapClassLib.PhoneGap.Commands.BaseCommand class. Plugin commands are dealt with generically throughout the framework, and base command provides the base interface for you to pass data back to JavaScript. This approach also prevents JavaScript code from calling arbitrary native code."
[Read more on Jesse's blog.](http://www.risingj.com/?p=92)

[See what features WP7 supports](httpshttps://phonegap.com/about/features)

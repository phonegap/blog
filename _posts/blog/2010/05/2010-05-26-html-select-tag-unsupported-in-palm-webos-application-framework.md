---
title: HTML Select tag unsupported in Palm WebOS application framework
date: 2010-05-26 00:10:19 Z
categories:
- app
author: Ryan Willoughby
link: http://blogs.nitobi.com/ryan/index.php/2010/05/25/html-select-tag-unsupported-in-palm-webos-application-framework/
status: publish
type: post
format: html
---

A recent blog post by [Steve Nay](http://globalconstant.scnay.com/) revealed that HTML Select elements were not working in PhoneGap Palm … and after a quick test it appears that they're not supported by WebOS at all. I scoured the internets trying to find this documented or discussed, and all I found was someone else [mentioning it in the Palm Developer Center](http://developer.palm.com/distribution/viewtopic.php?f=11&t=1819&p=6496). This is quite surprising and a bit frustrating to know that such a basic HTML element is unsupported, and really messes with the cross-platform support of PhoneGap. It also gets me wondering what other HTML tags are unsupported.

The select element is rendered (though it is ugly, supporting the theory that this element is unsupported by webOS), but cannot be interacted with. I'm guessing that the custom Tap events used by Mojo are unimplemented on it.

Ideal world solution: Palm fixes this and gets it out in an upcoming release.

Real world solution: I start experimenting with ways to fix this. Would love to hear from the community on suggestions … but really the solution that comes to mind is that PhoneGap, during initialization, finds all the html select elements and replaces them with Mojo List Selector elements. Even at first thought, I see some hurdles:

* we will have to copy over all of the style and class attributes … but these may have an unexpected effect on the look of the widget, since the Mojo List Selector consists of html elements with internal Mojo css classes.

* we will have to implement the standard javascript events, if they are not already available, such as onchange, onfocus, etc.

So I hope to get some time to experiment with this soon, and see if I can sort it out. And hopefully not find out that there is a list of html tags unsupported by webOS.

PS -- Suggestions appreciated!

[› Visit the original post](http://blogs.nitobi.com/ryan/index.php/2010/05/25/html-select-tag-unsupported-in-palm-webos-application-framework/)

---
title: Mobile Spec is here
date: 2009-11-04 18:29:54 Z
categories:
- app
author: Fil
link: http://blogs.nitobi.com/fil/2009/11/04/mobile-spec-is-here/
status: publish
type: post
format: html
---

The big thing around the office for the past year or so now has been [PhoneGap](http://www.phonegap.com). It's gaining in popularity every day, and recently we've had applications starting to trickle into application stores other than the iPhone one! We now have one application out in the Nokia Ovi store, and one on the BlackBerry App World. I'm pretty excited to see PhoneGap getting a lot of mention all over the place, but this also puts more pressure on the PhoneGap team to have a solid framework that works consistently across all of the platforms that we support currently: iPhone, Android, BlackBerry and (some) Nokia models.

![Mobile Spec running on a BlackBerry simulator](http://www.nitobi.com/fil/mobilespec_blackberry.jpg)

Mobile Spec running on a BlackBerry simulator

With PhoneGap being an open-source project, it is sometimes difficult to devote a lot of time to it all at once, and development coming in from user contribution is huge. One thing that is certain about open-source projects, especially ones where there are many contributors and an open development philosophy is used, is that having a set of tests is fairly essential. If developers wants to hop in and help out, in any way that that may be, they need to be sure that the changes they make don't break the entire application. This becomes even more important as a project gets bigger.

So after that long-winded introduction, I want to point people's attention to the new Mobile Spec that we have started to work on. You can find it on [GitHub](http://github.com/phonegap/mobile-spec). [Joe](http://blogs.nitobi.com/joe), our main PhoneGap Android developer, has [his own fork of it](http://github.com/bowserj/mobile-spec) that he's started to fill up with tests, so we've made and are currently making progress on it. Yes! I love automatic regression testing - call me a geek, but I can't help but have a warm fuzzy feeling inside knowing that test cases for something I'm working on are constantly trickling in ![:)](http://blogs.nitobi.com/fil/wp-includes/images/smilies/icon_smile.gif) . Obviously, the spec is in its infancy stages, but it's a big win. The more we put into it, the easier it will be to develop for it down the road, and the more it solidifies the stability of PhoneGap overall.

Since day 1, PhoneGap's goal has been for PhoneGap to cease to exist. That is, if all of the big players in the mobile space suddenly decided to work together and unify their third-party application development process, then PhoneGap wouldn't need to exist as a project. Related to this, the PhoneGap JavaScript API is mostly based off of the HTML 5 specification - open standards are good and healthy for the developer community. What I'm getting at is that the Mobile Spec we're putting together - _maybe / potentially / hopefully_ - may end up being a decent test suite for the HTML 5 spec, or at least the mobile portion of the spec. Or maybe I'm just too optimistic ![;)](http://blogs.nitobi.com/fil/wp-includes/images/smilies/icon_wink.gif)

We've opened this thing up to the community and we want to hear what you guys think. Have a beef with the API? Fork the mobile spec on GitHub, change it to what you think it should be, and then send us a pull request. We'll definitely have a look.

Here's to many forks! Cheers!

[› Visit the original post](http://blogs.nitobi.com/fil/2009/11/04/mobile-spec-is-here/)

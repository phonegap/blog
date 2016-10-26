---
title: WinMoDevCamp and PhoneGap WinMo
date: 2009-08-21 22:11:57 Z
categories:
- app
author: Fil
link: http://blogs.nitobi.com/fil/2009/08/21/winmodevcamp-and-phonegap-winmo/
status: publish
type: post
format: html
---

Earlier this week [Shaz](http://blogs.nitobi.com/shazron/) and I had the chance to attend the WinMoDevCamp in the heart of Microsoft-land in Redmond, WA. The conference / camp was nice and small, fairly well organized and lots of fun. I got to meet a ton of interesting and smart people with some great ideas.

An express goal that was given to us by Nitobi 'upper management' was to go there, network with the Windows Mobile people, and see what we can do with getting a working branch of [PhoneGap](http://www.phonegap.com) running on a Windows Mobile device. [Shaz had done some previous research into this work](http://blogs.nitobi.com/shazron/2009/06/02/the-state-of-phonegap-with-windows-mobile/), but we didn't have more than basic scaffolding source code and a general idea on how to do it. Long story short, we've got proof-of-concept code running and available! Check out [my PhoneGap repository](http://github.com/filmaj/phonegap/tree/master) on [GitHub](http://www.github.com) to see the source (the WinMo code is in the winmo directory). We don't have a large feature set working at this time, but we're on the right track. I'll be putting more work into it in the upcoming weeks/months and our goal is to eventually get the PhoneGap framework running on WinMo. If you're interested in helping out, sign up for an account on GitHub if you don't already have one, fork the repository and hack away! Feel free to post comments if you have questions as well.

Of course, we've got a ways to go. First of all, at least in WinMo version 6, the native browser is based off Internet Explorer 4 (insert snarky comment here), so JavaScript support is… different, to say the least, from what your everyday modern web developer expects. Apparently 6.5+ will solve this problem, but I guess we'll see. Our goal as developers of PhoneGap is to handle all of these little nuances for our PhoneGap users; whether it is the differences between platform and device code or if it's all on the JavaScript side, we should be able to abstract / wrap the details away from our end-user. That's the idea, anyways ![;)](http://blogs.nitobi.com/fil/wp-includes/images/smilies/icon_wink.gif)

Thanks to all the wonderful people at WinMoDevCamp in Redmond, you're all part of the reason this was possible. Special thanks to Ran, whom I met at the camp itself and who was integral in providing insight into the WinMo platform to get the proof-of-concept demo running and offering suggestions on how to improve the code. A chunk of the code in the repository is basically all his - you rock, Ran! Also thanks to Giovanni and Jennifer for organizing the event, I'm looking forward to future events!

To conclude, here's a screenshot of the PhoneGap demo app running on a WinMo device. Cheers!

![PhoneGap on Windows Mobile device](http://www.nitobi.com/fil/winmo.jpg)

[› Visit the original post](http://blogs.nitobi.com/fil/2009/08/21/winmodevcamp-and-phonegap-winmo/)

---
title: Update on PhoneGap Symbian & PhoneGap Palm
date: 2010-05-21 19:11:47 Z
categories:
- app
author: Ryan Willoughby
link: http://blogs.nitobi.com/ryan/index.php/2010/05/21/update-on-phonegap-symbian-phonegap-palm/
status: publish
type: post
format: html
---

I've been a bit inactive on PhoneGap recently, as we've had some client projects on the go. Need those $$ to keep the open-source projects rollin. But since its been a while, I wanted to give at least a status update on the PhoneGap platforms that I maintain.

There have been some updates to the PhoneGap Mobile Spec, so I've re-run them on WebOS and Symbian (see below).

[![PhoneGap mobile spec results on Palm Pre](http://blogs.nitobi.com/ryan/wp-content/uploads/2010/05/mobspec-palm.png)](http://blogs.nitobi.com/ryan/index.php/2010/05/21/update-on-phonegap-symbian-phonegap-palm/mobspec-palm/) [![PhoneGap mobile spec results on Nokia 5800 XpressMusic](http://blogs.nitobi.com/ryan/wp-content/uploads/2010/05/mobspec-symbian.png)](http://blogs.nitobi.com/ryan/index.php/2010/05/21/update-on-phonegap-symbian-phonegap-palm/mobspec-symbian/)

96 / 100 on Palm:

Contacts fails, as a full device contacts api is not available to us in WebOS (discussed in an earlier post); some of the device info tests fail, as we can only provide device properties that are provided to us by the device (not much we can do here); Network.isReachable fails, I believe because this spec has been updated to return a network status 'code', rather than the previous return value of just 'true' or 'false'. I'm going to fix up the Network api, hopefully today … but we're looking pretty good on Palm. And Palm devices are really nice, and very quick and easy to deploy to. I highly recommend trying it out, even in their emulator (also really nice).

81 / 98 on Symbian Web Runtime:

HTML 5 Storage fails: not available in WRT, and can't really implement SQLite in javascript ![:P](http://blogs.nitobi.com/ryan/wp-includes/images/smilies/icon_razz.gif) ; Network reachability fails, as WRT provides no API for this (however I'm going to revisit this as I figure their should be a way to do this); File I/O fails, as WRT does not provide access to the file system. Basically after running these tests (and having them crash regularly, I think due to running out of memory), I'm thinking more and more that PhoneGap Symbian using Qt for Symbian is the way to go. WRT is a great tool, for lightweight apps, but its performance is not good. Javascript animation simply can't be handled, and extensive sensor interaction will crash the application. Initial tests on PhoneGap using Qt for Symbian were much better. Not to say we should drop the WRT implementation overall, as it does meet certain needs.

[› Visit the original post](http://blogs.nitobi.com/ryan/index.php/2010/05/21/update-on-phonegap-symbian-phonegap-palm/)

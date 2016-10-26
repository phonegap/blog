---
title: Running jQTouch in PhoneGap
date: 2009-10-28 14:54:25 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2009/10/28/running-jqtouch-in-phonegap/
status: publish
type: post
format: html
---

Last week there were some discussions about the poor performance of jQTouch in PhoneGap apps, so I dug into it.

First I had to verify that this was something we were doing in PhoneGap and not a difference between Mobile-Safari and the UIWebView control which we use in PhoneGap.

I created a PhoneGap project and dropped the jQTouch sample code into the www folder, and immediately noticed the sluggish performance.

I then created a bare bones iPhone Windowed application with a UIWebView in it, and dropped the same www folder contents into the project root.

```objc
NSURL *appURL  = [NSURL fileURLWithPath:[[NSBundle mainBundle] pathForResource:@"index" ofType:@"html" inDirectory:@"www"]];
NSURLRequest *appReq = [NSURLRequest requestWithURL:appURL cachePolicy:NSURLRequestUseProtocolCachePolicy timeoutInterval:20.0];
[webView loadRequest:appReq];
```

After running both builds on the device it was obvious that the PhoneGap version was in fact sluggish compared to the bare-bones version. Verified!

So, thinking about what could be causing this, I looked into the PhoneGapDelegate code, and immediately saw the Accelerometer handling code the a potential culprit. The PhoneGapDelegate class asks the sharedAccelerometer for updates 40x per second. According to the Applei Phone dev docs, this interval is "Suitable for games and other applications that use the accelerometers for real-time user input." Which is cool, but probably way more than this application needs considering it isn't even being used. Every time that the sharedAccelerometer calls back with an update, the javascript is written into the webView's DOM. Commenting out the accelerometer code that sets up the interval indeed fixes the majority of the sluggishness. Verified! _Pretty smooth, eh?_

Okay, so commenting it out isn't really a solution, so here is the plan:

I am working to re-implement the Accelerometer portion as a command, that can be used more elegantly. Javascript code inside the www folder should have the ability to set how frequently it wants be updated, and have the ability to start + stop monitoring the accelerometer, which should also remove the overhead.

Note:

If your application does not use the accelerometer, instead of commenting out the code like I did, you can simply set "EnableAcceleration" to false in PhoneGap.plist.

I will post an update here when I have checked in anything of significance.

[› Visit the original post](http://blogs.nitobi.com/jesse/2009/10/28/running-jqtouch-in-phonegap/)

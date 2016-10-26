---
title: Shame doesn’t work in Open Source
date: 2011-04-19 00:25:50 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2011/04/18/shame-doesnt-work-in-open-source/
status: publish
type: post
format: html
---

There was a fair amount of news about Android 3.0 coming out. There was tons of hype regarding the new Honeycomb release, and how it would be designed for tablets, how there is 3D Acceleration, and how the User Interface would be changed. Well, even though it's rumoured that at Google IO, we're all going to get tablets, we decided to go and get the Motorola Xoom so that we can have solid answers to our clients about Honeycomb tablets.

Unfortunately, we have answers, and they're not very good with respect to Google.

First of all, the Honeycomb Emulator is so horrifically slow, we had to buy a device. The device we bought was the Motorola Xoom Wi-Fi Only model. After booting up the model, we put PhoneGap on it and ran tests. Most of the tests worked fine, however we did notice that the Native Storage (SQLite) does not work anymore and throws a security error. This is a serious problem for many PhoneGap applications that use this, and I plan on investigating the storage situation, and seeing what storage is used on the device.

Secondly, when we ran our mobile-spec test suite and ran it with no try/catch, this actually causes the browser to close. The browser shouldn't close when a Javascript Error is thrown. The fact that you can force someone out of the browser by throwing an exception should be an indicator that this should not have been released,

Finally, this device is rumored to have 3D Acceleration, including in the browser with 3D Transforms. First, we tested the browser with the [standard WebKit test here](http://www.webkit.org/blog-files/3d-transforms/poster-circle.html). When you test it in the actual Android Browser activity, you get the following:

[![](http://blogs.nitobi.com/joe/wp-content/uploads/2011/04/correct.png)](http://blogs.nitobi.com/joe/wp-content/uploads/2011/04/correct.png)

Then, when you take the poster-circle.html file (which is nice and self-contained) and stick it in PhoneGap (which at this point is just an Android Webview), you get the following here:

[![](http://blogs.nitobi.com/joe/wp-content/uploads/2011/04/broken_transform.png)](http://blogs.nitobi.com/joe/wp-content/uploads/2011/04/broken_transform.png)

Now, since we don't have the source code, we have no idea why Android Webview has broken 3D CSS Transforms, but Android's browser does. It's clear that Android WebKit didn't go through any sort of rigorous QA process, and was once again cobbled together. The thing that I don't like about this situation is that I can't see what they did to fix it on their browser. Many people would love to see 3D CSS Transforms on Android, Tablet OR Phone, but we don't have either right now.

The thing that I don't understand is this. If Google as a company isn't proud enough to release this source code, then why were the proud enough to release a half-baked product? As many people know, I have been developing Android applications both with WebKit and with straight-up Java ever since I heard that the T-Mobile G1 was going to be released. I put up with flaky APIs, with WebKit bridges that would crash, and with the mess that the Android 2.0 release was. The fact that Google hasn't learned from their mistakes with Android 2.0 was disappointing. It wasn't too bad in 2009 when they did this, because not too many people were using Android yet, but now that we're in 2011, and Android is on a ton of devices, and Android is in the tablet space, I'd expect there to be a little bit of consistency between the Android Browser and the WebView with respect to what is supported in WebKit.

That being said, I'd forgive flakiness in a x.0 version of Android if it came with the source code. Mainly because the community could fix the bugs and help create something kick-ass like the awesomness that Android 2.1+ was (Android 2.1 was the first solid Android version, everything else before it people liked because we were rooting for the underdog). However, today, as it stands, there's two different versions of WebKit on the SAME DEVICE that operate differently. I think that this is a serious regression, and it's unfortunate.

Update: I'm an idiot! The reason you don't get 3D CSS Transforms is the fact that you have to enable 3D Acceleration for the app in the Android Manifest. A quick Google Search [turned this up](http://is.gd/0jvPpb), and now I have it working. I still think the bug with the storage, and the fact that when you hit the back button you end up back at the First Use screen are still big reasons that Honeycomb is not ready for primetime, but WebKit has many problems, but 3D CSS Transforms aren't one of them.

[› Visit the original post](http://blogs.nitobi.com/joe/2011/04/18/shame-doesnt-work-in-open-source/)

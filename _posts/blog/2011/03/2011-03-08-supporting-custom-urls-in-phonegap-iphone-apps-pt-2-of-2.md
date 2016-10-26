---
title: Supporting Custom URLs in PhoneGap-iPhone apps pt 2 of 2
date: 2011-03-08 02:52:46 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2011/03/07/supporting-custom-urls-in-phonegap-iphone-apps-pt-2-of-2/
status: publish
type: post
format: html
---

My previous post explained how to get custom launch params so you can respond to different calling conditions, including a call from another app, or Mobile Safari. There is also a very good chance that your app may already be running, so what then?

## Handle Open URL

With multitasking, this actually becomes quite likely, because users no longer kill your app, they simply move away from it. Your app is essentially suspended, so you should probably handle the non-launch option as well.

The ApplicationDelegate class defines a method just for this use, all you have to do is override it and hook it into your webView.

Copy the following to your AppDelegate.m and add the function to your js code:

Also, note that you can name your javascript function whatever you want, as long it is the same name that your AppDelegate passes into the webView. I chose to simply keep things clear and called the function "handleOpenURL(urlStr)", but it could just as easily be "appController.handleUrl(urlStr)". As in the previous post, this url is UrlEncoded, so you may need to decode it, depending on your needs.

One cool thing about the handleOpenURL function is that it is easily testable. You can put a link right inside your html to make the call using your protocol and it will be processed by the OS and passed right back to your app. This may not seem useful, but I can foresee situations where it might make sense, like passing info from a [ChildBrowser](https://github.com/purplecabbage/phonegap-plugins/tree/master/iPhone/ChildBrowser) control back to your main app, or completely decoupling your view from your app-controller. … Any other ideas?

I welcome your comments, questions, and suggestions. _buy my single => ![:)](http://blogs.nitobi.com/jesse/wp-includes/images/smilies/icon_smile.gif) _

[› Visit the original post](http://blogs.nitobi.com/jesse/2011/03/07/supporting-custom-urls-in-phonegap-iphone-apps-pt-2-of-2/)

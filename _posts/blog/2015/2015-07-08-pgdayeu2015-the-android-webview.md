---
title: 'PhoneGap Day EU 2015: The Android WebView'
date: 2015-07-08 12:00:03 Z
tags:
- PhoneGap Day
- Event
- Community
author: Jen Gray
format: html
---

A big thanks to everyone who was able to make it to PhoneGap Day EU 2015 in Amsterdam. We'll be posting more videos from the conference so check back on our [blog](https://phonegap.com/blog/tag/phonegap-day/) and [Youtube channel](https://www.youtube.com/user/PhoneGap).

Next up, [Niels Leenheer](https://twitter.com/html5test) talks about the Android Webview.

The Android WebView is a system level component that handles HTML, CSS and JavaScript, and can be used by other applications. One of the applications that uses the WebView is the default Android browser, but your own PhoneGap apps are also using it. In fact, PhoneGap is just a wrapper that extends the WebView. Unfortunately there is not just one WebView. The WebView changes between versions of Android. Sometimes these changes are just bug fixes, and sometimes they include new features. What’s even worse: device manufactures apparently also like to make their own modifications to the WebView. Recently Google tried to solve this mess and created a new backwards compatible WebView for Android 4.4 and higher. The new WebView is no longer based on WebKit, but uses Chromium instead. What are the differences and how does this impact your applications? Is the new WebView really backwards compatible? Which web platform features should you avoid in your PhoneGap app and which are safe to use? How do you deal with creating apps for a multitude of WebViews that all behave slightly different? Which devices do you need to properly test your app? And finally, are there other solutions to these problems?

Slides available [here](https://speakerdeck.com/nielsleenheer/the-android-webview-at-phonegap-day)

{% include video.html id="mP6rhbDT0ZQ" %}

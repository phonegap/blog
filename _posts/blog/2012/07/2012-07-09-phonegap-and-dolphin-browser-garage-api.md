---
title: Introducing Dolphin Garage's APIs for PhoneGap
date: 2012-07-09 22:03:00 Z
categories:
- News
- Tweet
author: eyeung
status: publish
type: post
format: html
tas:
- News
- App
---

Great news, PhoneGap and Dolphin Browser are teaming up!

![Dolphin PhoneGap API](http://dev.dolphin-browser.com/wp-content/uploads/2012/06/web-app-overview-image.png)

Dolphin Browser is one of the most popular browsers on the Android (voted CNET's #2 most popular Android app). It is also the world’s first Gesture and voice enabled (Dolphin Sonar) mobile browser. You can speak to Dolphin and tell it to search, share and navigate the mobile web, all without typing a word. When you say ‘Facebook André Charland’, instead of showing results in google search, it will go directly to Facebook and return all the profiles with the name ‘André Charland’.

Dolphin is also the most capable HTML5 browser on the market.  The new Dolphin Engine (beta) makes for the fastest browsing experience around, rendering HTML5 up to 5-10 times faster than the default browser on Android, scoring more than [450 points](http://dolphin-browser.com/2012/06/dolphin-browser-is-the-fastest-html5-mobile-browser-try-out-our-dolphin-engine-in-beta/) on HTML5test.com.

The Dolphin team was able to achieve this remarkable accomplishment through extensive canvas improvements, with particular attention given to canvas element, 2D context. In addition, Dolphin Engine made significant GPU accelerated canvas rendering and optimized CPU/GPU parallel computing.

“We’ve done a lot of tuning in Dolphin for HTML5, and we are very excited to partner up with the PhoneGap team and want to support the developers with an even stronger foundation,” said Dolphin marketing head Edith Yeung.

With the new Dolphin PhoneGap APIs and Add-on, you can easily create web app from scratch or from existing Android Apps. Users simply navigate to a web site that, like a conventional package, makes full use of local features such as camera, GPS, and accelerometer. The Dolphin PhoneGap Add-on enables JavaScript on a webpage to access local device features.

How does it work?

1. All you need to do is to place a copy of cordova.dolphin.js on the web server, in the root folder or other web-accessible location.
1. Create a webpage and include cordova.dolphin.js which listens for the `deviceready` event and signals that the PhoneGap API is available on the device. You can then use the API features such as camera, GPS, and accelerometer.

This is super cool that a mobile browser can finally implement PhoneGap APIs. Having these PhoneGap optimized on mobile browser has been a goal of PhoneGap team for a while. It is really awesome that Dolphin became the first browser that supports this.

Check out the Wikipedia web app right in [Dolphin](https://play.google.com/store/apps/details?id=mobi.mgeek.TunnyBrowser&hl=en) and our video:

{% include video.html id="iGxusIgR48M" %}

Learn more about how to create a web app compatible with PhoneGap on [Dolphin Garage Developer Portal](http://dev.dolphin-browser.com/web-app-guide/).

_Edith Yeung is the head of marketing for Dolphin browser. You can follow her on Twitter at [@edithyeung](https://twitter.com/edithyeung)._

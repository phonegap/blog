---
title: 'PhoneGap: It’s Like AIR for the IPhone'
date: 2008-09-18 16:57:28 Z
categories:
- app
author: Dave Johnson
status: publish
type: post
format: html
tags_old:
- ios
redirect_from:
- "/2008/09/18/phonegap-ite28099s-like-air-for-the-iphone/"
---

![](http://farm2.static.flickr.com/1413/1490570992_3ed3f29633_m.jpg) A few weeks back Brock and Rob from here at Nitobi built an amazing IPhone framework down at [IPhoneDevCamp](http://www.iphonedevcamp.org/) that we have named [PhoneGap](https://phonegap.com). While I have attributed the injustice of us not winning any of the competition categories of IPhoneDevCamp to the completely jaw dropping achievement of our team, in just two days of development (with most of the competition winners having developed their apps weeks or months before IPhoneDevCamp) it does not take away from the excitement I have for our PhoneGap framework. And there is lots of excitement around PhoneGap with [some](http://iphonemicrosites.com/news/phonegap-converts-webapps-to-native-apps/) [blogs](http://britg.com/2008/08/21/phonegap-native-iphone-apps-running-your-html-css-javascript-code/) [about it](http://appleiphoneapps.org/2008/08/22/phonegap-native-iphone-apps-running-your-html-css-javascript-code/), lots of activity over at [GitHub](http://github.com/sintaxi/gap), and 60 people signed up to the [PhoneGap Google Group](http://groups.google.com/group/phonegap) in just a few short weeks!

While some may not have realized the impact of PhoneGap (including the judges at IPhoneDevCamp), we here at Nitobi think that PhoneGap is _the Adobe AIR of the IPhone_ (not to mention Blackberry, Android, Symbian and Windows Mobile). Just like Adobe AIR enables web developers to build Windows and OS X applications using the HTML and CSS skills that they know and love, PhoneGap allows web developers to build applications for the IPhone with web technologies while taking advantage of the native IPhone APIs like GPS, the camera, SQLite, contacts and more!

Using PhoneGap, a developer need not write any Objective-C code and yet they can still have a proper app installed on an IPhone that is essentially a slightly customized PhoneGap application that sports a custom icon and a certain URL where application lives online (very much like AIR). When a user starts PhoneGap it essentially creates a headless (ie no address bar) browser on the IPhone and navigates to the specified URL where the author of the web page can access IPhone APIs through JavaScript like this:

```js
getLocation();
//GAP will invoke this function once it has the location
function gotLocation(lat,lon){
  $('lat').innerHTML = "latitude: " + lat;
  $('lon').innerHTML = "longitude: " + lon;
}
```

Or access the accelerometer data like this:

```js
function updateAccel(){
  $('accel').innerHTML = "accel:"+accelX + " "+accelY+" "+accelZ;
  setTimeout(updateAccel,100);
}
```

Someone has even tried to get a PhoneGap on the App Store - however, [has had little success so far](http://britg.com/2008/09/08/apple-too-stupid-to-understand-utility-of-outside-the-box-apps/).

The aim of PhoneGap is to bring mobile phone development to web developers just as AIR has brought desktop application development to the web community. One of the next steps will be packaging _all_ the HTML, JavaScript and CSS into the application that goes on the IPhone so that the application can even run offline much like AIR does.

There is still lots to be done!

Image by [http://flickr.com/photos/nielsvaneck](http://flickr.com/photos/nielsvaneck)

[› Visit the original post](http://blogs.nitobi.com/dave/2008/09/18/phonegap-air-for-the-iphone/)

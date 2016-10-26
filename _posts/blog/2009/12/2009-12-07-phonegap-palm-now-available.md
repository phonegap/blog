---
title: PhoneGap Palm now available
date: 2009-12-07 20:47:39 Z
categories:
- app
author: Ryan Willoughby
link: http://blogs.nitobi.com/ryan/index.php/2009/12/07/phonegap-palm-now-availableg/
status: publish
type: post
format: html
---

![palm](http://blogs.nitobi.com/ryan/wp-content/uploads/2009/12/palm.png)

I just pushed my latest work on PhoneGap Palm to [my github repo](http://github.com/wildabeast/), and it should be pulled over to the main phonegap repo shortly.

PhoneGap API's available to Palm devices include geolocation, accelerometer, notification, orientation, sms, telephony, network, file (read only), and a limited selection of device properties (see the PhoneGap Mobile Spec running on the Palm Emulator to the left).

Unfortunately the contacts API won't be available for a while, due to the fact that the Mojo API limits data access (including contacts data) to that which was created by the app in context (see [this discussion](http://developer.palm.com/distribution/viewtopic.php?sid=61f5023a5bf3941c441586a1405f215d&lastaction=login&f=9&t=3323&p=12427&hilit=get+contacts)). Hopefully this will change.

For those who don't know, Palm's webOs is completely based on web technologies. We've got a couple of Palm Pre's here for testing, and they're sick. And the edit/deploy/test cycle is very smooth. You can test on device and write to a debug console which you can monitor on your SDK console.

Like we did for Symbian WRT, we simply had to write a javascript shim to map the Mojo API (webOs' mobile js API) to the PhoneGap API. I also had to do a bit of messing around with the stage/scene system which they use for changing application views. But its ready for use with the device APIs listed above.

I'll be continuing to work on this and expand the API, and I also hope to get some time to continue my work on PhoneGap Symbian/Qt.

[› Visit the original post](http://blogs.nitobi.com/ryan/index.php/2009/12/07/phonegap-palm-now-availableg/)

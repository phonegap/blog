---
title: 'PhoneGap for Symbian: Qt'
date: 2009-11-18 21:45:53 Z
categories:
- app
author: Ryan Willoughby
link: http://blogs.nitobi.com/ryan/index.php/2009/11/18/phonegap-for-symbian-qt/
status: publish
type: post
format: html
---

During the initial stages of working on [PhoneGap](http://www.phonegap.com/) for [Symbian](http://www.symbian.org/) using [Web Runtime](http://www.forum.nokia.com/Technology_Topics/Web_Technologies/Web_Runtime/), some limitations were brought to light due to the fact that Nokia's WRT is closed source: we are limited to the device functionality and platform support which Nokia has exposed. Nonetheless its a great technology and porting PhoneGap to WRT was a relatively quick win (taking in to account my having to re-learn javascript after 1 year of flailing abroad).

But over the last few weeks, while maintaining the latter, I've been researching/experimenting (don't even want to go far as say developing, as very little has been implemented) with [Qt for Symbian](http://qt.nokia.com/developer/qt-4.6-rc-for-symbian-developers). The crew at Nokia just released the [Qt 4.6 release candidate](http://qt.nokia.com/developer/qt-4.6-rc-for-symbian-developers) on Nov 17th, and it includes a port of Webkit to Qt (QtWebkit), along with support for the Symbian/S60 platform, which is just the combination phonegap needs.

![note my amazing javascript console, firebug is crap](http://blogs.nitobi.com/ryan/wp-content/uploads/2009/11/symbianpg.jpg)

note my amazing javascript console, firebug is crap

So anyways I've got a PhoneGap Symbian Qt build (piggybacking off of the webkit demos included with Qt) which can open a local resource in a webview, and expose Qt Objects (and thus device functinoality) to javascript (via webframe->addtojavascriptwindowobject). I've implemented the most important API first, rather than the easiest: vibration. Ok it was actually the easiest.

Anyways there's other problems to tackle before implementation of more PhoneGap APIs:

* XHRs seem to be getting blocked. I'm thinking its blocking what it considers a cross-domain XHR: a local html file to a remote server. I believe the support of this depends on the Webkit implementation(?)
* I can't remember what else.

So if this looks interesting, help out the mobile developer community. Contribute. Its open source. Check out my very basic [Getting Started doc](https://phonegap.pbworks.com/PhoneGap-Symbian-%28Qt%29), and get the code from my [PhoneGap repo on Github (Symbian Qt branch)](http://github.com/wildabeast/phonegap/tree/symbian.qt). The .sis installer file is in there as well, so you could also just put it on your device to see a PhoneGap app that vibrates and thats about it. Really useful. I think you might need to install Qt libraries to your phone since I haven't packaged them in the app yet.

[› Visit the original post](http://blogs.nitobi.com/ryan/index.php/2009/11/18/phonegap-for-symbian-qt/)

---
title: 'PhoneGap Symbian: Qt 4.6 for Symbian officially released'
date: 2009-12-01 21:36:06 Z
categories:
- app
author: Ryan Willoughby
link: http://blogs.nitobi.com/ryan/index.php/2009/12/01/phonegap-symbian-qt-4-6-for-symbian-officially-released/
status: publish
type: post
format: html
---

So after starting off with Qt 4.6 tower, then upgrading to colossus ), then a beta release candidate, the official Qt 4.6 RAMBO release is here! Well its not called Rambo but it should be. Its got solid Qt Support, though I haven't upgraded my PhoneGap Symbian fork yet, but will shortly. I was hoping we might have the [Qt Mobility](http://blog.qt.nokia.com/2009/12/01/technology-preview-new-qt-apis-from-mobility-project/) packages built into the release but I guess there's still some work to be done on them. For now I'll have to continue to include the different libraries via source code, which isn't a big deal.

Brian fowarded me a twitter post of someone who was confused how Qt gets installed on the device … its a sis installer file, just like most other tools and apps (save WRT Widgets). Sis installers can encapsulate other sis installers, so I was thinking Qt could be packaged with PhoneGap apps for deployment. Maybe if developers really start making apps using PhoneGap Symbian with Qt, Symbian will ship with Qt …

There may be some confusion as to how PhoneGap Symbian Qt will be built and deployed, so here's a bit of a step by step of what's required ([detailed version](https://phonegap.pbworks.com/PhoneGap-Symbian-%28Qt%29)):

1. Install the [S60 (Symbian) SDK](http://www.forum.nokia.com/info/sw.nokia.com/id/ec866fab-4b76-49f6-b5a5-af0631419e9c/S60_All_in_One_SDKs.html), [Qt 4.6 for Symbian](http://qt.nokia.com/products/platform/symbian) (SDK first, Qt patches it), and their various associated prerequisites.
1. Download the [PhoneGap Symbian source code](http://github.com/wildabeast/phonegap/tree/symbian.qt), which which will include the required [Qt Mobility APIs](http://blog.qt.nokia.com/2009/12/01/technology-preview-new-qt-apis-from-mobility-project/).
1. Build your webapp using html/js/css and the symbian phonegap.js, and place it in the phonegap/symbian.qt/framework/www/ folder.
1. Build and in the emulator, if desired.
1. Qt 4.6 includes qt.sis. This installs qt to your symbian phone. Do it.
1. Build your application, which will give you your application.sis (self-signed). This will be your distributable. Voila.

Outstanding issues:

* cannot send xhr's from our local resources (priority)
* many API's still to be implemented
* Symbian Signing

Feel free to post comments if you have any questions.

[› Visit the original post](http://blogs.nitobi.com/ryan/index.php/2009/12/01/phonegap-symbian-qt-4-6-for-symbian-officially-released/)

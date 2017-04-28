---
title: Update on PhoneGap port to Qt for Symbian
date: 2010-01-15 19:34:34 Z
categories:
- app
author: Ryan Willoughby
link: http://blogs.nitobi.com/ryan/index.php/2010/01/15/update-on-phonegap-port-to-qt-for-symbian/
status: publish
type: post
format: html
---

After getting distracted for a while from my port of [PhoneGap](https://phonegap.com) to Qt for Symbian, I've recently jumped back on it, tightening it up a bit and adding some APIs. We now have Geolocation, Vibration, Acceleration, & Orientation working.

Now we already have a Symbian port of PhoneGap working and available, which uses Nokia's Web Runtime (WRT) technology (which is native to Symbian OS). So why PhoneGap on Qt for Symbian? Well I briefly mentioned some of the limitations faced by using WRT in a previous post; I will touch on those again and expand:

* It is a closed-source proprietary technology, so we cannot actively fix bugs, and we cannot add features (and we want PhoneGap to be open!),
* Performance: when I ported a PhoneGap application developed and tested on the Palm Pre to PhoneGap Symbian WRT, I found that its javascript animation was completely lost. It would get from state A to state B, but the animation in between was non-existent. I originally assumed my phone simply could not handle the animation … until I tried it using PhoneGap Qt for Symbian. It worked.
* Memory: I tried using prototype.js in one of my PhoneGap WRT applications … it would crash immediately upon opening the application simply from the volume of javascript being loaded. Which reminds of when I first started developing with Web Runtime, and my applications would intermittently crash. Initially I would be chasing down the line of code which was crashing the environment … until eventually it became clear that we were simply running out of memory. Wasted a fair bit of time looking for non-existent bugs.

Now PhoneGap Symbian for Qt is still young and perhaps as it grows, it will face the performance & memory issues mentioned above. But for now things are running much smoother.

So far my testing of PhoneGap Qt for Symbian has been limited to my little PhoneGap API demo app, so more testing is definitely on my plate. The platform uses Qt Webkit, which appears to be very modern and so far has worked very nicely for me. Flick-scrolling is not native to the Qt Webview, so I may have to try implementing that as well. But to summarize, PhoneGap Qt for Symbian is now available, though not yet API-complete. [Clone it](http://github.com/wildabeast/phonegap-symbian.qt), [Get Started](https://phonegap.pbworks.com/PhoneGap-Symbian-%28Qt%29), and let me know if you have questions, comments, or suggestions. Or contributions!

[› Visit the original post](http://blogs.nitobi.com/ryan/index.php/2010/01/15/update-on-phonegap-port-to-qt-for-symbian/)

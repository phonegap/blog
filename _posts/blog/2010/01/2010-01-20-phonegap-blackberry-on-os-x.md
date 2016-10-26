---
title: PhoneGap Blackberry on OS X
date: 2010-01-20 00:00:00 Z
categories:
- app
author: Andrew Lunny
link: http://blogs.nitobi.com/andrew/2010/01/30/phonegap-blackberry-on-osx
status: publish
type: post
format: html
---

![BlackBerry Simulator in OS X](http://blogs.nitobi.com/andrew/images/phonegap-blackberry-osx.png)

Nitobi/PhoneGap dev Fil Maj [tweeted](http://twitter.com) the other day about [this excellent tutorial from Aziz Uysal](http://www.azizuysal.com/2009/07/blackberry-development-on-mac-os-x.html), describing how to get the BlackBerry SDK and simulator up and running on OS X, for which it has no official support. Using some Eclipse skills and Wine magic, you can pull up the simulator and enjoy all the benefits of BlackBerry dev without booting up a VM.

If you want to run PhoneGap-BlackBerry in this environment, it’s trivially easy. Here’s how:

1. Do everything it says in the tutorial, until you can run a Hello World app in the simulator
1. Clone the [PhoneGap-Blackberry](http://github.com/phonegap/phonegap-blackberry) repo
1. File -> Import… -> General, Existing Projects into Workspace, then Next
1. Under Select root directory, select `/whatever_your_path_is/phonegap-blackberry/framework/` and then select PhoneGap in the Projects field below
1. Add an `index.html` file to the `src/www` directory.
1. Open `build.xml` for editing. Change the `jde.home` and `simulator.home` properties to match your simulator location (if you follow Aziz’s tutorial, you can copy these properties from the `build.xml` of that project). Edit the `load-simulator` tag (`<target name="load-simulator">`) to match the other `build.xml` file also
1. Drag `build.xml` into the app view (as detailed in Aziz’s tutorial). Then double-click on load-simulator
1. Hit Menu (next to the green button), then Downloads, then PhoneGap
1. Hrrm… ??????????
1. Profit!

Thanks to Aziz for writing such a great tutorial – now we just need someone to get XCode running on Windows 7!

**Edit**: This tutorial was [previous referenced](http://groups.google.com/group/phonegap/browse_thread/thread/ebd3681c8eefba3d/eb29373d7606be8f?lnk=gst&q=blackberry+os+x) on the PhoneGap mailing list by John Britton – I wasn’t aware until he brought it up in a later message. Thanks for bringing this to our attention John.

[› Visit the original post](http://blogs.nitobi.com/andrew/2010/01/30/phonegap-blackberry-on-osx)

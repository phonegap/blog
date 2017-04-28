---
title: PhoneGap Build Icon Support for Android
date: 2011-03-16 00:04:51 Z
categories:
- app
author: Fil
link: http://blogs.nitobi.com/fil/2011/03/15/phonegap-build-icon-support-for-android/
status: publish
type: post
format: html
---

Recently, I've been doing more and more work on the [build service](http://build.phonegap.com) that Nitobi has in beta, which allows users to submit PhoneGap application assets and download built binaries of their app for iOS, Android, BlackBerry, Symbian and webOS.

This week, [Andrew](http://blogs.nitobi.com/andrew/) and I are working on delivering full icon support for the supported [PhoneGap Build](http://build.phonegap.com) platforms. Today we released Android support. Now, if the config.xml bundled in your application contains <icon>elements with different specified sizes, Build will make sure to use the appropriately-sized ones for Android devices with high, medium and low resolution screens.</icon>

Here's a quick example config.xml from a static page I am running called the [John Garrett Drinking Game](http://www.johngarrettdrinkinggame.com) ([Canucks](http://canucks.nhl.com) fans, you know what I'm talking about) - the [code for this is also available on GitHub](https://github.com/filmaj/John_Garrett_Drinking_Game):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<widget xmlns="http://www.w3.org/ns/widgets" xmlns:gap="https://phonegap.com/ns/1.0" id="com.nitobi.johngarrett" version="1.0">
  <name>John Garrett Drinking Game</name>
  <description>
    If you're watching a Canucks game, you need play this.
  </description>
  <author href="http://www.nitobi.com" email="support@nitobi.com">
    Tim Kim, Ryan Betts, Fil Maj
  </author>
  <icon src="img/beer_72.png" width="72" height="72" />
  <icon src="img/beer_48.png" width="48" height="48" />
  <icon src="img/beer_36.png" width="36" height="36" />
</widget>
```

The three specified sizes you see for the <icon>elements correlate to the three resolution levels supported on Android: 72 by 72 (or above) will be used for HDPI screens, 48 by 48 for MDPI, and 36 by 36 for LDPI.</icon>

Later this week we are hoping to land icon support for the rest of the platforms. Stay tuned!

[› Visit the original post](http://blogs.nitobi.com/fil/2011/03/15/phonegap-build-icon-support-for-android/)

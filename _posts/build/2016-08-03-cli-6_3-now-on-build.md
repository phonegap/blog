---
title: PhoneGap CLI-6.3.0 Now on Build
date: 2016-08-03 10:00:00 Z
categories:
- build
tags:
- PhoneGap Build
author: Ryan Willoughby
---

PhoneGap 6.3.0 is now available on [PhoneGap Build](https://build.phonegap.com)! To use it, add the following to your config.xml file:

    <preference name="phonegap-version" value="cli-6.3.0" />

Also noteworthy is that this version has been made the new default, so if you're not locking the phonegap-version in your app's config.xml, it will be built with `cli-6.3.0` (we encourage you to lock your PhoneGap version, especially if you're extensively using device API's and plugins).

The [platform version breakdown](https://build.phonegap.com/current-support) for `cli-6.3.0` (and a link to each version's release notes) is as follows:

 - iOS: [4.2.0](https://github.com/apache/cordova-ios/blob/4.2.0/RELEASENOTES.md)
 - Android: [5.2.1](https://github.com/apache/cordova-android/blob/5.2.1/RELEASENOTES.md)
 - Windows: [4.4.1](https://github.com/apache/cordova-windows/blob/4.4.1/RELEASENOTES.md)

No major version changes are included, so the majority of the updates since 6.1.0 will be fixes and improvements.

As usual, if you have questions or issues, [don't hesitate to let us know](https://forums.adobe.com/community/phonegap/build).

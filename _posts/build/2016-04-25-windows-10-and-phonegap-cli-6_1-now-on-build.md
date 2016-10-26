---
title: Windows 10 and PhoneGap CLI-6.1.0 Now on Build
date: 2016-04-25 10:00:00 Z
categories:
- build
tags:
- PhoneGap Build
author: Ryan Willoughby
---

PhoneGap 6.1.0 is now available on Build, and with this release we're adding support for **Windows 10 Builds**! To use it, add the following to your config.xml file:

    <preference name="phonegap-version" value="cli-6.1.0" />

Although this update only includes minor version increments on each platform, the release adds Windows 8.1 and Windows 10 support to the currently supported Windows Phone 8.1 builds.

The platform version breakdown of `cli-6.1.0` is as follows:

  - iOS: 4.1.0
  - Android: 5.1.1
  - Windows: 4.3.1

### The Cordova Windows Platform

The cordova-windows platform allows you to target one of three sub-platforms: Windows 8.1, Windows Phone 8.1, and Windows 10 (via the Windows Universal App Platform). When PhoneGap Build moved from cordova-wp8 to cordova-windows with the [release of cli-6.0.0 back in February](/blog/2016/02/09/phonegap_6_now_on_build/), we only included Windows Phone 8.1 support, but now Windows 8.1 and Windows 10 can be targeted as well. You can read more about the Cordova Windows Platform in the [Apache Cordova documentation](http://cordova.apache.org/docs/en/latest/guide/platforms/win8/index.html).

To select which of the three Windows platforms you target with your build, use the new `windows-appx-target` config.xml preference:

	<!-- Windows 10 (default): -->
    <preference name="windows-appx-target" value="uap" />
    <!-- Windows 8.1: -->
    <preference name="windows-appx-target" value="8.1-win" />
    <!-- Windows Phone 8.1: -->
    <preference name="windows-appx-target" value="8.1-phone" />

Additionally you can select the architecture that your build targets. Valid values are `anycpu`, `arm`, `x86`, and `x64`:
	
	<preference name="windows-arch" value="anycpu" />


### Distribution to the Windows App Store

These new windows builds have a slightly more involved signing process than the previous Windows Phone Publisher ID method, which was a simple GUID setting. A .pfx certificate file is now required to sign your app and distribute it to the App Store. [This article on MSDN](https://msdn.microsoft.com/en-us/library/windows/desktop/jj835832(v=vs.85).aspx) explains how to create a PFX store file. Ensure the Subject Name of your signing certificate matches the Windows Publisher ID from your [Microsoft Developer Account](https://developer.microsoft.com/en-us/dashboard/account/management).

Go to your [PhoneGap Build Account Settings](https://buildstage.phonegap.com/people/edit), select the **Signing Keys** tab, upload your **Windows 10** key and unlock it, and select it when building your application.

**In addition:**

1. The `author` field in your config.xml must match the Publisher Display Name from *Windows Dev Center -> Account Settings*, i.e:

    ```<author>Adobe Systems Canada Inc</author>```

2. A new config.xml preference `windows-identity-name` has been introduced to set the App Idenity Name in your App Manifest. This preference must match the App Identity Name from your *Windows Dev Center Account -> App Management -> App Identity*:
	
	```<preference name="windows-identity-name" value="PhonegapBuild.PGBDeveloper" />```


Windows 10 support is being released as a beta feature as we work out any quirks, so [let us know if you find issues, or have questions or feedback](https://forums.adobe.com/community/phonegap/build).

---
title: PhoneGap Push Plugin 1.9.0
date: 2016-11-03 00:00:00 Z
tags:
- Release
- News
author: Simon MacDonald
---

We haven't done a post regarding phonegap-plugin-push for awhile, but we have just
released version 1.9.0! Along with bug fixes and general improvements there are three main things you should know about:

1. Default SENDER_ID
1. CocoaPod Support
1. Force Start for Android

## Default SENDER_ID

In order to add the push plugin to your app you need to specify a SENDER_ID:

```bash
$ phonegap plugin add phonegap-plugin-push --variable SENDER_ID="XXXXXXX"
```

But in order to make life easier for developers you can now do:

```bash
$ phonegap plugin add phonegap-plugin-push
```

and it will use the default SENDER_ID to be used with the `phonegap push` command.
It's equivalent to doing:

```bash
$ phonegap plugin add phonegap-plugin-push --variable SENDER_ID="85075801930"
```

You'll still be able to override this value as part of the options passed to the
`init` method for Android. For using GCM over iOS you'll need to remove and add the
plugin again with your correct SENDER_ID.

## CocoaPod Support

Speaking of GCM over iOS, we've removed the GCM libraries from the plugin repo
and they are now fetched and installed via CocoaPod. This has the benefit of
making the plugin repo much smaller and help avoid dependency issues where more
than one plugin include the same library.

Check out [cordova-ios 4.3.0 announcement](https://cordova.apache.org/announcements/2016/10/24/ios-release.html) for more details.

## Force Start for Android

When an Android app is forced closed by the user you can still get push notification
in the notification shade but your `notification` handler is not called as the
web view is not running. Now you can set the `force-start` property in your push
payload which will start your app in the background on Android. This will require
[cordova-android@6.0.0](https://cordova.apache.org/announcements/2016/10/24/android-release.html) or greater.

Sample push payload:

```javascript
{
    "registration_ids": ["my device id"],
    "data": {
        "title": "Force Start",
        "message": "This notification should restart the app",
        "force-start": 1
    }
}
```

## What's New

For those interested in the full CHANGELOG:

## [v1.9.0](https://github.com/phonegap/phonegap-plugin-push/tree/v1.9.0) (2016-07-09)

[Full Changelog](https://github.com/phonegap/phonegap-plugin-push/compare/v1.8.4...v1.9.0)

- 1.9.0 [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/e5b7f22299d900a37064a783da43905ad73c58bf)
- Bumping plugin version to 1.9.0 [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/dc6a11db4157e1070e48e073a8a78401f185d324)
- Prepare for 1.9.0 release [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/0f889bfb5e612ef3ffbc1466deabfe9eb99b760b)
- Update gitignore [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/d70bad64564444c01e59ff494b8ba09d190d3dbb)
- Bumping plugin version to 1.9.0 [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/600993e7739a0a84ef77b60c4a1457f8aea084b6)
- Issue #1154: Register fail iOS 10 [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/e6013d49ecf0025be10fb6bb87152ee4025b5df4)
- Issue #1337: Build failed, invalid package.json [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/8631666e4654fd6acafa6cf160cc59424e912ceb)
- Set default SENDER_ID [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/82ca365f4d6d91b18fc28c338a647a2622e60f6e)
- Issue #158: Notification Event Not Firing When Closed Through App Launcher [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/ca18653d6ff332db41f48824a2d65bd2699ed8bc)
- Merge branch 'master' of [https://github.com/hanicker/phonegap-plugin-push](https://github.com/hanicker/phonegap-plugin-push) into hanicker-master [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/43402909d3b2d5c6ff518cc69e401dc918b585aa)
- Update plugin to use GCM Cocoapods `<framework>` reference in plugin.xml (#1183) [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/b639d83fe125d5b77720d130ccec53af3a5f3d91)
- Updating CHANGELOG [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/e4779de2a5996703ba70656630f35d79415d1af8)
- feat(forced restart, notify javascript) [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/8c03beff9a5a83927b7020ee04c3ed541de04edd)
- restart application after force close (#158 #333) [view commit](http://github.com/phonegap/phonegap-plugin-push/commit/8b7c972dbf617f22218c178d74368b35521eecb9)

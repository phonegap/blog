---
author: Sterling Gerritz
title: Release of PhoneGap Multiview Plugin!
tags:
- Announcement
- Android
- iOS
- Plugin
- Release
- PhoneGap Blog
---

## PhoneGap Releases New MultiView Plugin

We're happy to announce the release of the new PhoneGap MultiView plugin with support for iOS and Android!

The MultiView plugin gives developers the ability to launch multiple Cordova Webviews within one PhoneGap application! Each webview is fully independent, is able to communicate with local storage, and has its own set of plugins.

## The Demo Application

We have included a demo project in the PhoneGap repo so that you can see how the plugin works in action!  The Demo features two views, a "parent-view" and a "child-view", with the purpose of illustrating the passing of data between views.  Please note that the plugin itself can support multiple views. Source code to our Demo Project is included in the PhoneGap repo, to run it in iOS/Android:

```bash
$ cd demo
$ cordova platform add ios (or) cordova platform add Android
$ cordova plugin add --link .. (Android does not link)
$ cordova run ios (or) cordova run Android
```

Please check out a demo video which illustrates the passing of data between webviews:

### Android

[![Youtube - Android Demo](/blog/uploads/2016-12/androidscreenshot.png)](https://youtu.be/_ZzBA28QO4s "Youtube -Android Demo Movie")

### iOS

[![Youtube - iOS Demo](/blog/uploads/2016-12/iosscreenshot.png)](https://youtu.be/WVbxFIGBh0Y "Youtube -iOS Demo Movie")

## MultiView Plugin Installation Instructions

After you have built your project, install the plugin in your project location:

```bash
$ phonegap plugin add phonegap-plugin-multiview (or) cordova plugin add phonegap-plugin-multiview
```

## Quickstart Guide to Using the MultiView Plugin

The plugin and complete documentation are available for download [here in the PhoneGap Repo](https://github.com/phonegap/phonegap-plugin-multiview).

Remember, you must create a JavaScript file for each of your views which correspond repectively to the native portion of the plugin (PGMultiview.java and PGMultiviewActivity.java).

To *launch* a new webview make this call in your application's JavaScript:

```bash
$ PGMultiView.loadView(url, strPayload, success, error);
```

To *dismiss* a webview make this call in your application's JavaScript:

```bash
$ PGMultiView.dismissView(data);
```

![MultiViewSequence](/blog/uploads/2016-12/MultiViewSequence.png)

## Stay Tuned!

This is the first version of the API... More improvements are coming down the pipeline! We will be continually adding more functionality as we incorporate feedback!

## Issues

- Currently data is stored to memory (not disc).  Under most operating conditions this should not be an issue. However, in an extreme low memory state you do risk losing data between views if either PGMultiView.java or or PGMultiViewActivity crash before reaching onStop() in the activity lifecycle.

- This bug should be resolved in the near future, the next release of this plugin bindsEvents() and writes the saved view state to local storage so that it can be retrieved at OnPause() in the Cordova Activities' lifecycle.

## Contact Us

Your feedback is graciously accepted and appreciated!
[Please submit your pull requests and issues here](https://github.com/phonegap/phonegap-plugin-multiview/).

Please feel free to reach out to
[me on twitter!](https://twitter.com/SterlingAndroid) --Sterling

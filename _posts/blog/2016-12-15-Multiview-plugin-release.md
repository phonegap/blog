---
author: Sterling Gerritz
title: Release of Phonegap Multiview Plugin!
date: 2016-12-14
tags:
- Announcement
- Android
- iOS
- Plugin
- Release
- PhoneGap Blog
---

We're happy to announce the release of the new Phonegap MultiView plugin with support for iOS and Android!

The Multiview plugin empowers developers with the ability to launch multiple Cordova Webviews within
one within a Phonegap application! Each webview is fully autonomous, is able to communicate with local storage, and has its own set up plugins.

Please check out our demo video which illustrate the passing of data between webviews:

[Youtube - Demo Project](https://youtu.be/_ZzBA28QO4s)

Source code to our Demo Project is included in the repo, to run it in ioS/Android:

```bash
$ cd demo
$ cordova platform add ios (or) cordova platform add android
$ cordova plugin add --link .. (Android does not link)
$ cordova run ios (or) cordova run android
```

## Installation/Quickstart

The plugin and documentation are available for download [here in the Phonegap Repo](https://github.com/phonegap/phonegap-plugin-multiview)

 -Android

To *launch* a new webview make this call in your application's JS:

```bash
$ PGMultiView.loadView(url, message, success, error);
```

To *dismiss* a webview make this call in your application's JS:

```bash
$ PGMultiView.dismissView(data);
```

To pass data:

```bash
$ startCordovaActivity(url, message);
```

The child view is activated.  Data and a plugin result are passed to the plugin which updates the childview.

```bash
 $ onActivityResult(requestCode, resultCode, intent);
```

When the childview has been backgrounded (aka user navigates away from the PGMultiviewActivity.java) the parent view retrieves
the result of that activity ,"message from parent", and requestCode from the intent

-iOS

To *launch* a new webview:

```bash
$ PGMultiView.loadView(srcUrl)
```

To *close* a new webview:

```bash
$ PGMultiView.dismissView();
```

![MultiViewSequence](/blog/uploads/2016-12/MultiViewSequence.png)

## Stay Tuned!

The current API is in its early stages of development.  We currently only support two views but are continually adding functionality and in process of providing support for multiple views.

## Issues

- Currently data is stored to memory (not disc).  Under most operating conditions this should not be an issue. However, in an extreme low memory state you do risk losing data between views if either PGMultiView.java or or PGMultiViewActivity crash before reaching onStop() in the activity lifecycle.

- This bug should be resolved in the near future, the next release of this plugin bindsEvents() and writes the saved view state to local storage so that it can be retrieved at OnPause() in the Cordova Activities' lifecycle.

## Contact Us

Your feedback is graciously accepted and appreciated!

[Please submit your pull requests and issues here](https://github.com/phonegap/phonegap-plugin-multiview/).

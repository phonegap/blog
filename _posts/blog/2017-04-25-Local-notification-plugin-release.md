---
author: Simon MacDonald
title: Release of PhoneGap Local Notification Plugin!
tags:
- Announcement
- Android
- iOS
- Plugin
- Release
- PhoneGap Blog
---

## PhoneGap Releases New Local Notification Plugin

We're happy to announce the release of the new PhoneGap Local Notification plugin with support for iOS and Android!

The Local Notification plugin gives developers the ability to post notifications from their app that show up in the device's notification area. The API for the local notification plugin follows the [W3C Web Notifications](https://www.w3.org/TR/notifications/) specification.

### Android

![Local Notification - Android](/blog/uploads/2017-04/local-notification-android.jpg).

### iOS

![Local Notification - iOS](/blog/uploads/2017-04/local-notification-ios.png).

## Local Notification Plugin Installation Instructions

After you have built your project, install the plugin in your project location:

```bash
$ phonegap plugin add phonegap-plugin-local-notification (or) cordova plugin add phonegap-plugin-local-notification
```

## Quickstart Guide to Using the MultiView Plugin

The plugin and complete documentation are available for download [here in the PhoneGap Repo](https://github.com/phonegap/phonegap-plugin-local-notification).

To *show* a new local notification make this code to your application's JavaScript:

```js
if ("Notification" in window) {
  Notification.requestPermission(function (permission) {
    // If the user accepts, let's create a notification
    if (permission === 'granted') {
      var notification = new Notification("My title", {
        tag: 'message1', body: "My body" });   
      notification.onshow  = function() { console.log('show'); };
      notification.onclose = function() { console.log('close'); };
      notification.onclick = function() { console.log('click'); };
    }
  });
}
```

To *close* a local notification make this call in your application's JavaScript:

```js
notification.close();
```

## Stay Tuned!

This is the first version of the API... More improvements are coming down the pipeline! We will be continually adding more functionality as we incorporate feedback!

## Issues

- iOS requires that you specify the body for the notification. Without a title and a body the notification will not be shown.

## Contact Us

Your feedback is graciously accepted and appreciated!
[Please submit your pull requests and issues here](https://github.com/phonegap/phonegap-plugin-local-notification/).

Please feel free to reach out to
[me on twitter!](https://twitter.com/macdonst) --Simon

---
title: Add analytics to your PhoneGap app with Appsee
date: 2016-10-06 00:00:00 Z
tags:
- Guest Post
- Community
author: Appsee Team
---

![](/blog/uploads/appsee.png)

## Introduction

Are you in need of an analytics solutions that enables you to zone in on single users and see exactly how they are experiencing your app? Introducing [Appsee](https://www.appsee.com/), the market leader in qualitative analytics; analytics that supply you with the “whys” behind all of the numerical data on your app.

With Appsee's unique features of [user recordings](https://www.appsee.com/features/user-recordings) and [touch heatmaps](https://www.appsee.com/features/touch-heatmaps), you can gather the most actionable insights and make better informed decisions regarding your app's UI, performance, and usability. Basically, it allows you to dive deeper into your app’s user experience and dissect your data for crucial answers. Appsee also automatically detects all screens, buttons and user actions within your app without requiring you to select what to measure in advance and tag them in advance in your code.

Luckily, Appsee supports all apps built with PhoneGap and the integration is extremely simple.

Below we will provide a quick breakdown of how to integrate with Appsee in 2 steps.

## Integration

To integrate Appsee in your phonegap app - you can use our npm plugin in 2 easy steps.

1. Add the Appsee plugin to your project: `phonegap plugin add cordova-plugin-appsee`
1. Call the following method when your app starts, preferably when the deviceready event fires: `Appsee.start("YOUR API KEY")`;

[Register](https://www.appsee.com/start) or [login](https://dashboard.appsee.com/login) in order to get your API key.

This is how your code should look like:

```js
var app = {
    // Application Constructor
    initialize: function() {
        this.bindEvents();
    },
    // Bind Event Listeners
    //
    // Bind any events that are required on startup. Common events are:
    // 'load', 'deviceready', 'offline', and 'online'.
        bindEvents: function() {
        document.addEventListener('deviceready', this.onDeviceReady, false);
    },
    // deviceready Event Handler
    //
    // The scope of 'this' is the event. In order to call the 'receivedEvent'
    // function, we must explicity call 'app.receivedEvent(...);'
    onDeviceReady: function() {
        app.receivedEvent('deviceready');
    },
    // Update DOM on a Received Event
    receivedEvent: function(id) {
        var parentElement = document.getElementById(id);
        var listeningElement = parentElement.querySelector('.listening');
        var receivedElement = parentElement.querySelector('.received');


        listeningElement.setAttribute('style', 'display:none;');
        receivedElement.setAttribute('style', 'display:block;');


        Appsee.start("d3y87d2h723dh8237hd7823");
    }
};
```

![](/blog/uploads/userrecordings.png)
Example of Appsee’s User Recordings

![](/blog/uploads/touchheatmap.png)
Example of Appsee’s unresponsive gesture touch heatmap.

## Conclusion

Pretty easy right? After completing those two steps you are good to go. You should start to see your user sessions populate your dashboard in real-time. Get ready to discover powerful insights on your app’s users, optimize and troubleshoot your app effectively, and ultimately create the best mobile product possible.

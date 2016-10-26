---
title: Power Your PhoneGap App with the New ShowKit SDK
date: 2013-06-13 16:15:00 Z
tags:
- Guest Post
author: Matt Van Veenendaal
format: html
---

ShowKit, a powerful mobile SDK that allows developers to easily integrate audio/video conferencing, screen sharing, and remote gesture control into any mobile application, is happy to announce that our latest release now supports PhoneGap [integration](http://blog.showkit.com/post/52806556213/showkit-now-supports-phonegap).

Together, PhoneGap and ShowKit make developing robust mobile applications easier. PhoneGap simplifies app creation for multiple platforms and ShowKit offers PhoneGap users the ease of adding powerful in-app communication features.

## View more about ShowKit:

{% include video.html type="vimeo" id="65253521" %}

## Check out ShowKit’s demo app to see these features at work:

{% include video.html type="vimeo" id="65406591" %}

## Audio / Video Conferencing

[Showkit](http://www.showkit.com) users benefit from smooth video conferencing, with clear VGA and 720p resolutions at 30 frames per second using minimal CPU resources. ShowKit’s best in class audio / video conferencing feature is built on the only framework that includes hardware accelerated video encoding and decoding. The decoding component is fairly tricky and unique, and enables device to device communication, which is a more complex development than device to web communication. The minimal CPU usage allows the device to run other functions in parallel, such as a game or app. ShowKit’s competitors (which shall remain nameless) use full CPU and only get 4-5fps at that resolution, which isn’t feasible for video conferencing. ShowKit reports that this feature is so easy to integrate that they watched a team of junior mobile developers at the recent ShowKit sponsored [AngelHack Los Angeles](http://angelhack.com/) add a working implementation into their hack in about 30 minutes.

## Screen Share & Remote Gesture Control

(a feature ShowKit is pioneering)
The ShowKit SDK also provides users with shared gestures on UIKit controls, gesture indication graphics, and gaming-compatible screen sharing. ShowKit envisions several possible use cases for this feature set that might include (but not limited to) the facilitation of sales, customer support, or social gaming. Teja Vishwanadha won ShowKit’s prize for best implementation at AngelHack Los Angeles by creating MemoryPlay, a casual memory game with rich real time interaction between players.

## PhoneGap Integration And Exclusives

ShowKit’s technology now seamlessly facilitates integration with PhoneGap, just check out our PhoneGap specific [docs](http://www.showkit.com/docs/phonegap).

1. Drag ShowKit.framework into your project
1. Add the following line to your config.xml file:

  ```xml
  <plugin name="ShowKitPlugin" value="ShowKitPlugin"/>
  ```

1. Initialize the app with your ShowKit API key in index.js:

  ```js
  // The scope of 'this' is the event. In order to call the 'receivedEvent'
  // function, we must explicitly call 'app.receivedEvent(...);'
  onDeviceReady: function() {
    app.receivedEvent('deviceready');
    var apiKey = "aa2ab742-a7B8-4acf-8af4-6694265a2a25";
    ShowKit.initializeShowKit(apiKey);
  },
  ```

1. Include ShowKit.js in any HTML files where you plan to use ShowKit:

  ```js
  <script type="text/javascript" src="js/ShowKit.js"></script>
  ```

1. Select your project in the Project Navigator, select the Target, and then select the Build Settings tab. Search for “Other Linker Flags.” After that, you can build and run your ShowKit-enabled project!
1. Remove the `-all_load` linker flag. Then add `-force_load "$(BUILT_PRODUCTS_DIR)/libCordova.a"` and `-lc++` to your Other Linker Flags

ShowKit recently launched a private beta and is currently available for iOS developers, with web and Android compatibility coming soon. We are offering an exclusive promotion code for PhoneGap users who would like to implement the technology. Interested mobile developers can request an invite from [ShowKit’s](http://www.showkit.com/invites/new) site using the code **"PhoneGap"** to gain immediate access to the SDK.

For additional information and a more in-depth explanation of this technology, developers can register for a [webinar](https://startupminds.clickwebinar.com/PhoneGap_ShowKit_Webinar) that I will be hosting next week. The webinar is exclusively for PhoneGap users and will take place on Wednesday, June 19th, 2013 from 11:05 am – 12:05 pm PT.

> Guest blog post by Matt Van Veenendaal, ShowKit Co-Founder, CTO
> Matt is a graduate of the Swinburne University of Technology. He formerly served as a software engineer at internet security giant Telesign and as the CTO of Ringadoc. As the current CTO of Curious Minds, Matt manages the engineering department. He has a passion for software architecture, design, and various web technologies.

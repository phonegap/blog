---
title: PhoneGap-alytics
date: 2011-05-04 23:19:49 Z
categories:
- Plugins
author: Jesse MacFadyen
status: publish
type: post
format: html
---

_Do you want to gain marketing intelligence and information on how users interact with your PhoneGap app? **You need this plugin!**_

## Introducing the Google Analytics for PhoneGap plugin.

Over the last couple weeks, Joe aka [@infil00p](http://twitter.com/infil00p) and I have been working on some exciting new plugins. We wanted to provide a simple way for PhoneGap developers to get analytics data on the usage of their apps. Instead of doing something silly [edit: removed prickish link], like trying to write our own analytics engine, we integrated with Google's best in class offering.

## But PhoneGap apps are webpages already, can't I just include the script tag for web sites?

Yes, you could, in fact, if you are targeting BlackBerry, Palm or other devices, you will need to do this. For iOS and Android though, this plugin allows analytics data to be stored when the application is running without a network connection, and updated when a network becomes available. You could even track the fact that the network is unavailable, so you can compare metrics of offline vs online usage.

## Building the plugin

Google already provides code for Android and iOS, so we really just needed to make a mapping from the JS side to the native side. Phonegap's pluggable architecture made this simple, as this is exactly what it was built to do. We simply reviewed the Google SDK functionality and mirrored this in JS.

Google's GANTracker class provides the bulk of the functionality and exposes the following methods:

# startTrackerWithAccountID

* given a web-entity-id, start tracking engine.
* the engine will periodically send analytics data to the server.
* the engine will cache data if there is no network connection, and update the server when it can.

# trackEvent

* parameters for category, action, label, value
* when something happens in your app, and you want to keep track of it, you can call trackEvent
* google has an in-depth guide to using custom events [here](http://code.google.com/apis/analytics/docs/tracking/eventTrackerGuide.html)

# trackPageview

* pageViews mean something different in an application, they may reflect actual pages, or perhaps different views within your app.
* The choice of what you send for pageUri is up to you. It can be any string value, for example /application/launch or app/settings.

## Installation and Use

To setup Android, you will need to follow Google's instructions in the docs. For iOS, I have packaged the lib and header, so you can simply add everything in the iOS folder of the repo.

From finder, place the plugin js file in your www folder, and include it in the page. After receiving the deviceready event in your app, start the tracker. Note that I create a local alias, so I don't need to type window.plugins.googleAnalyticsPlugin everywhere, and code can be more readable. This gist demonstrates the initialization, and shows how to track the fact that your app was launched, as well as showing an example trackEvent for tracking playback of a movie.

You can get the code here: [https://github.com/purplecabbage/phonegap-plugins/tree/CoreDump/GoogleAnalytics](https://github.com/purplecabbage/phonegap-plugins/tree/CoreDump/GoogleAnalytics)

More in depth info on Google Analytics for Mobile can be found here: Google SDK Docs [http://code.google.com/mobile/analytics/docs/](http://code.google.com/mobile/analytics/docs/)

... and lots more info on how to use events so that you can track meaningful information on usage. [http://code.google.com/apis/analytics/docs/tracking/eventTrackerGuide.html](http://code.google.com/apis/analytics/docs/tracking/eventTrackerGuide.html)

## Next Steps

Plugin work in general is ongoing. One thing in particular is that we want to make the JavaScript code that you include in your app exactly the same on all the different devices that use it. Currently it is sometimes necessary to have multiple JavaScript files, which is an unwanted evil.

Another goal we are working towards is consistent plugin packaging. Instead of forcing developers to take different steps to ready their app to use a plugin on multiple devices, we want to use a plugin configuration file, so the app code will be exactly the same on each device.

Integration between the PhoneGap Build service and custom Plugins is something we are working towards, so developers can just get down to writing their apps.

Expect more plugins in the coming weeks, as we try to fill more 'Gaps' and make everyone's PhoneGap apps easier to make.

I welcome your comments, feedback, and questions.

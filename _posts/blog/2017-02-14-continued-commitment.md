---
author: Jesse MacFadyen
title: "Our Continued Commitment"
tags:
- Apache Cordova
- News
- Open Source
- Community
---

## Intro

The Adobe PhoneGap team has been quietly contributing to Apache Cordova since it’s conception. We don’t make a lot of noise about what we do, but we are dedicated to advancing the technology, and continuously striving to give web developers the full power of the underlying devices that their hybrid apps run on.

Fresh off on a team planning meeting, we decided it would be nice to tell the community what we are planning, and re-affirm our commitment to Apache Cordova, so there is absolutely no question that we will continue to contribute.

## Security

We have defined an internal team goal of making sure that we have a solution or work around for any security issue within 60 days.  Most likely this number will be far less, however we may refine it later, and we will measure our own performance in the process.  Typically a reporter has 90 days before they announce a security issue, so likely only the reporter (and us) will know if we met the 60 days, but that is our announced target.

## OS Versions

We will also guarantee that we are quick out the door when new OSs come out.  We have set ourselves a 1 month window in which we are confident we will have an update to our tooling and frameworks that works with any updated SDKs, permission changes, or other requirements.  We actually expect our update to be ready before the official wide release of an OS version as we generally have a few months lead time to be ready, but that is where we are setting our guarantee for the time being.  We may refine this after measuring our performance.

## Platforms

We have decided to focus primarily on the iOS, Android and the Windows (uwp) platforms. Other platforms ( node/electron, mac-os ) are interesting to us, but our team does not currently have the capacity to pursue them, so we are focusing on the big(ish) 3.

## Plugins

We have chosen to focus on the plugins that have the greatest impact, highest use, and that we feel are the most needed.  Camera is huge, and we expect it to grow in use, while some other plugins we actually feel should just be part of the framework.  An example of this is the [debug console](https://github.com/apache/cordova-plugin-console).  When it was conceived, it made sense to have as it was expected behavior in the browser, but missing from our tooling.  Nowadays if you use Safari debug tools, you see the console.log(s) without needing a plugin, and similarly `chrome://inspect` shows Android device and emulator console.logs.  The only real case where you still need the plugin is if you are running in Xcode, so ultimately we would like to just patch the tooling there and not have anything for the app developer to install. SplashScreen is also in this category as most of the work of specifying a splash screen is determined at build time, so there is really no need for an API at runtime.

The Cordova (core) plugins that we will be focusing on are :

- Camera
- Device
- File & FileTransfer
- Globalization
- In-App-Browser
- StatusBar
- Geolocation

We will of course continue to push our own plugins as well, especially (appropriately enough)  the [Push plugin](https://github.com/phonegap/phonegap-plugin-push) which has become very popular.  [Barcode Scanner](https://github.com/phonegap/phonegap-plugin-barcodescanner), and [ContentSync](https://github.com/phonegap/phonegap-plugin-contentsync) have also proven to be worthy of our continued commitment.

A [progressive web app plugin](https://github.com/phonegap/phonegap-plugin-pwa) is in it’s early days, but seeks to blur the line between an app in a hybrid app container, and a web focused distribution, without the developer having to write the app twice.

We will also continue to provide tools for plugin authors. The [PhoneGap plugin template tool](https://github.com/phonegap/phonegap-plugin-template), for example, makes it trivial to create a new boilerplate plugin and simplifies that critical first step of defining the associated metadata without having to lookup all the available xml/json tags.

## Outreach

We would like to see the Apache Cordova community continue to grow and have decided to measure the number of signed CLAs we receive per month as our metric. Learn more about contributing to [Cordova here](http://contribute.cordova.io/). This means you are likely to see more team and guest blog posts, more twitter posts about what we are doing and what we need, as well as more conversations from the PhoneGap team in the [Cordova Slack Channel](https://cordova.slack.com/). [Join us here](http://slack.cordova.io/)

## Embedded workflows

Native first hybrid apps, embedded workflows, or what I affectionately call ‘hybrid hybrids’ will be a push for the team as well, although most of this will be delivered through PhoneGap tooling, we will contribute parts to Cordova where it makes sense. The premise of being able to add a little PhoneGap/Cordova to an existing native app excites us, and we feel it would an easy foothold into the hybrid world for developers coming from native platform-centric development.

## Onwards

Regardless of whether we are committing directly to Apache Cordova, or to Adobe PhoneGap, most of the work we do, and projects we create are open source! We will continue to push the web forward, and welcome your pull requests, questions, comments, [bug reports](http://issues.cordova.io/), ideas, stories and support. We proudly count ourselves among the many dedicated [committers](https://projects.apache.org/committee.html?cordova) and contributors to Apache Cordova.

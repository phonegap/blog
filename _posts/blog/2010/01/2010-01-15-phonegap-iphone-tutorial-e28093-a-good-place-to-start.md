---
title: PhoneGap iPhone Tutorial – A good place to start
date: 2010-01-15 01:51:26 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2010/01/14/phonegap-iphone-tutorial-a-good-place-to-start/
status: publish
type: post
format: html
---

PhoneGap has been getting a lot of attention lately, and also a lot of questions on the mailing list about where to get started.

I recently built a small PhoneGap app for iPhone that helps to demonstrate PhoneGap functions.

The application is divided into multiple pages, and each page focuses on one area of functionality.

I have strived to keep each page dedicated to the functionality it presents, and present everything as simply as possible.

There are no dependencies on any other libraries, and the js / css for each page is contained directly there.

## The Notifications page demonstrates key navigator.notifications functions.

* Custom Alerts - with custom title text, and button text.
* Display a loading screen for a fixed length of time
* Vibrate the device
* Show and hide the Activity Indicator ( the spinner at the top bar )

## The Accelerometer page demonstrates navigator.accelerometer functions.

* Start + Stop the accelerometer update logic, and play with a bouncing ball.

( a shout out to Yohei for providing the initial code for this example. )

## The Contacts page demonstrates navigator.contacts functions.

* Display the number of contacts
* Spawn the contact picker screen
* Renders a contact, and makes it clickable, to spawn the contact viewer.

## The GeoLocation page demonstrates how to use navigator.geolocation

* Gets your current location
* Calls Twitter api using JSONP to get tweets within a mile of your location

( a shout out to [Girlie Mac](http://girliemac.com/blog/) this code was shamelessly borrowed )

Hopefully the other platformers will step up and publish / test on other devices.  I have only worked on the iPhone branch so far.

I will be working on the Media api next to demonstrate how easy it is to play mp3s within PhoneGap, and I might even post some of my own music, we'll see.

[Get it](http://github.com/phonegap/phonegap-iphone) while it's hot!

[› Visit the original post](http://blogs.nitobi.com/jesse/2010/01/14/phonegap-iphone-tutorial-a-good-place-to-start/)

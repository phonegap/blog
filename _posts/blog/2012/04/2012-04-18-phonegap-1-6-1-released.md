---
title: PhoneGap 1.6.1 Released!
date: 2012-04-18 22:24:07 Z
categories:
- app
tags:
- Release
author: Steve Gill
status: publish
type: post
format: html
---

We have just released [PhoneGap 1.6.1](https://phonegap.com/download)! The PhoneGap/Apache Cordova Community has worked hard to fix some bugs that arose from the 1.6.0 release that needed to be addressed immediately.

The main issue driving this quick release was the incorrect xml folder that was included with the Android code that caused the network API to fail. This was a bug that needed to be addressed and could not wait for the 1.7 release. Thanks to the community for its quick work on turning around these fixes!

You can view the rest of the changes below in the change log.

## iOS

* Fixed CB-496 - Camera.getPicture - will always return FILE_URI even though DATA_URL specified
* Fixed CB-497 - online and offline events are not being fired in 1.6.0
* Fixed CB-501 - orientationchange event is not being fired in 1.6.0
* Fixed CB-302 - orientation change event fired off twice on iOS 5.x
* Fixed CB-507 - Remove excessive debug logging in execute delegate method in CDVViewController

## Android

* Copying new XML into the templates for 1.6.1\. Turns out tags are broken
* CB-489 - Adding .js to the example, thought it was removed for a reason
* Adding fix for CB-482
* Remove duplicate files from repository
* Automatically update index.html in templates directory on version change

## Windows

* cleanup console logging, toLower on OverrideBackButton
* updated template, permissions, and js

## Bada

* updating bada project parameters
* adding artwork and removing old phonegap references
* CB-4 adding Apache Source Headers
* fixing network problem

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list. All bugs can be found on our [issue tracker](https://issues.apache.org/jira/browse/CB).

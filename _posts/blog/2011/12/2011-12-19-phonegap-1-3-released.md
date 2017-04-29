---
title: PhoneGap 1.3 Released
date: 2011-12-19 18:05:17 Z
categories:
- app
tags:
- Release
author: Colene Chow
status: publish
type: post
format: html
---

The PhoneGap Community has done it again. We are happy to announce the release of [PhoneGap 1.3](https://phonegap.com/download)! In this release, we’ve made great progress with BlackBerry and Windows Phone.

For BlackBerry, we’ve added OSX support so now you can develop for BlackBerry on a Mac!

For Windows Phone, users can now sink their teeth into the full PhoneGap API, Windows Phone Getting Started Guide, more documentation updates and tons of plugins.

PhoneGap 1.3.0 is also available on the [PhoneGap Build web service](http://build.phonegap.com) - by default, all new apps will be built with 1.3.0\. Any existing apps will remain on 1.1.0, and users can choose between 1.1.0, 1.2.0 and 1.3.0 for building apps for five different platforms.

Check out the release notes below to see all of the enhancements and fixes. Alternatively, you can view the commits on [http://github.com/callback](http://github.com/callback).

## General PhoneGap Info

* A vote was held and a motion carried to rename Apache Callback incubator project to Apache Cordova. Plans to transition Callback to Cordova will take place for the PhoneGap 1.4 release.
* PhoneGap issue tracker moved to [https://issues.apache.org/jira/browse/CB](https://issues.apache.org/jira/browse/CB)

## Android

* Added download method to filetransfer
* made getEntry of FileUtils public in order to avoid duplicate code in FileTransfer
* FileTransfer returns JSONObject with code, source and target for upload and download
* Fix for CB-17: WebView caching resized pictures
* Fix for issue #281 of phonegap/phonegap-android: Detect for localStorage if Java has disabled it
* Fix for phonegap-android issue #261: Wrong application scale
* Fix for Issue #33: onReceivedError incorrectly sets openExternal to true
* Remove addWhiteList from public API
* Remove WebViewReflect.java from Android
* Fix for CB-104: Capture not returning an error code on cancel
* Changed createCaptureFile to explicitly check for PNG and to throw an IllegalArgumentException if it is not a JPEG nor a PNG
* Add support for future menu plugin
* Remove PhoneGap.stringify, replace with JSON.stringify
* Fixed: Don't fire resume upon init - only when returning from background
* Fixed: Backbutton should go back in appview history before going back in our history stack
* Added onMessage(id, data) to the plugin API
* Deprecated addService().
* Refactored the backHistory() code so calling navigator.app.backHistory() has consistent behavior with the backbutton
* Added onload attribute to plugin in plugins.xml to create the plugin at load time instead of lazy loading
* Fixed bug with showing loadingDialog property
* Fixed Issue #23 - Crash when using splash screen
* Changed API to postMessage() to call a plugin's onMessage() method
* Optimized enumerations

## Blackberry

* Added OSX support. You can now develop for BlackBerry on a Mac.
* Added download method to filetransfer
* Updated PluginResult Exceptions to use latest naming scheme
* Fixed a memory leak issue with WebWorks
* Added Lifecycle changes and app.js functionalitly
* Added activity and progress notification functionality

## iOS

* Added download method to filetransfer, interface is the same like on Android
* When playing audio from remote URL, stop as soon as download fails and make loading cacheable
* Fixed #197 errors on repeated getCurrentPosition calls. If the location services were off when getCurrentPosition was called, turn them off again after the position is received
* Don't force an orientation change unless the current orientation is unsupported
* Fixed callback/callback-ios#15 - Xcode 3.2.6 Linker error when Build for Active Architecture Only = YES
* Fixed callback/callback-ios#23 - on app resume, it always throws either an offline/online event even though the online state never changed
* Fixed warning - implicit conversion of UIInterfaceOrientation to UIDeviceOrientation (which are equivalent, for the two Portraits and two Landscape orientations)
* Fixed callback/callback-ios#22 - Removed unused DetectPhoneNumber and EnableAcceleration values in PhoneGap.plist
* Fixed CB-96 PGWhitelist does not handle IPv4 host addresses with wild-cards
* Added 'resign' and 'active' lifecycle events
* Fixed CB-101 can't access media in documents://subDir

## Windows Phone

* Added Full PhoneGap API support
* Bug-fixes for XMLHttpRequest calls to local file system, especially important for jQuery Mobile apps
* Updates to the Visual Studio templates, now you can create a quick app that references the PhoneGap library via a dll. Or you can start with a bare-bones project and only add the functionality you need
* [Upcoming] wiki docs on how the App Hub static analyzer sees your code, and determines required permissions
* [Upcoming] getting started screen-casts
* GapView is a usercontrol, so you can use it in your existing Windows Phone app, you don’t have to start over to use PhoneGap
* Addressed issues with File API persistence + local storage
* Getting started guides, documentation updates, wiki updates
* Improvements for plugin architecture, plugins can come from any assembly
* New plugins!
  * FaceBook connect - supports the full graph API available to your phonegap app, consistent with the Android+iOS versions of the plugin
  * ChildBrowser - display external web content without leaving your app
  * PGSocialShare - share status updates and links to LinkedIn, Twitter, Windows Live + Facebook, all at the same time, and via accounts managed on the phone
  * PGMapLauncher - get directions to or from a location, or search near a location using BingMaps. Locations can be specified as lat/lon as well as text like “Steam Clock”, or the users current location
  * LiveTiles - update your app tile on the Metro home screen with relevant info and pictures

[Jesse MacFadyen](http://www.risingj.com/), a core developer for PhoneGap, recently blogged about his experience with bringing PhoneGap to Windows Phone. [Read the full journey here](http://www.risingj.com/blog/archives/147). You can also read the Microsoft announcement [here.](http://blogs.technet.com/b/port25/archive/2011/12/19/full-support-for-phonegap-on-windows-phone-is-now-complete.aspx)

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list.

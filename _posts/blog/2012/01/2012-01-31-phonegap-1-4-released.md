---
title: PhoneGap 1.4 Released
date: 2012-01-31 17:42:00 Z
categories:
- app
tags:
- Release
author: Steve Gill
status: publish
type: post
format: html
---

The PhoneGap Community has done it again. We are happy to announce the release of [PhoneGap 1.4](https://phonegap.com/download)! This release contains many bug fixes from version 1.3.0.

The [PhoneGap Build cloud service](http://build.phonegap.com) will also be adding support for PhoneGap 1.4 starting today.

**UPDATE:** A bug was discovered that disabled orientation change on iOS devices. We have just released PhoneGap 1.4.1 that addresses this.

Check out the release notes below to see all of the enhancements and fixes.

## Android

* fixing whitelist handling
* Change API to postMessage() to call a plugin's onMessage() method.
* Optimize enumerations as suggested by @plowman.
* Fix CB-135 Multithreaded access on CallbackServer javascript object.
* Added license header to new files.
* Remove unused files/classes until they are needed.
* Work-around Feature for Classic PhoneGap 320x480 resolution
* Fixing scale, setting legacy scale
* Removing GapView, since it doesn't actually do anything
* Moving LinearLayoutSoftKeyboardDetect out into its own class and making it more plugin-like
* Editing a comment about LinearLayoutSoftKeyboardDetect
* Changing to use JS directly. There are issues with this approach, and it should use the KeyboardHandler
* Moved Chrome Client out of DroidGap.java
* Moving the WebViewClient out, allowing for PhoneGap to not break on empty console.log
* Removing the classic render feature, since it's not working properly
* README.md: Replace "PhoneGap" with "Cordova" and add incubation disclaimer
* Minor incubation disclaimer fix.
* Add compass demo for Android
* Added authentication framework
* Renamed crdentials/principals to userName/password
* Documentation additions
* Changed createCaptureFile to explicitly check for PNG and to throw an IllegalArgumentException if it is not a JPEG nor a PNG
* Adding JUnit dependency
* Reading preferences from phonegap.xml
* Using preference=fullscreen for fullscreen view
* Making preference reading code more robust
* Fix for issue #281 of phonegap/phonegap-android: Detect for localStorage if Java has disabled it
* Fix for Issue #33: onReceivedError incorrectly sets openExternal to true
* Fix NullPointerException in DroidGap.onMeasure()
* Fixing issue with FileTransfer.upload when the passed in url contains a ?
* Proved generating sqlite database path to open database without permission error
* Camera default destination should be FILE_URI
* CB-145: Android contact.save() crashes for native contacts.
* CB-199: FileTransfer.download fails on Android 4.0
* Allow internal SD Card to be used as storage
* Fixing a timing issue with the web view history not being cleared properly
* Updating version to 1.4.0rc1
* Updating version to 1.4.0

## Blackberry

* #124: Adding Battery events to the PlayBook.
* #153: Default for camera destination type changed from DATA_URL to FILE_URI.
* #CB-122: native JSON writer class needs expandable char buffer
* Fixing playbook plugin manager

## iOS

* Fixed CB-143 - Removing address from iOS contact causes crash
* Fixed CB-153 - Camera default destination should be FILE_URI
* Fixed CB-7 - Update source headers to apache license
* Fixed CB-42 - MediaPlaybackRequiresUserAction can now be set to NO
* Added stand-alone PGViewController (Cleaver - PhoneGap as a Component)
* Fixed iOS 5 quirks with presenting/dismissing modal viewcontrollers.
* Added 'How to Use PhoneGap as a Component' doc to the .dmg (as a PDF)
* Added 'PhoneGap Upgrade Guide' doc to the .dmg (as a PDF)
* Added for legacy support of deprecated PhoneGapDelegate - in core plugins.
* Removed PhoneGapLibTest project and folder
* Updated the app icons, splash-screens, and template icons for the Xcode template to Cordova ones.
* Added Battery core plugin to PhoneGap.plist
  * Fixed CB-212 - iOS orientation switch broken in 1.4.0

## Windows Phone

* Acceleromter fix #CB-141 - InvariantCulture
* Changed default destination to FILE_URI
* Contacts returned from find were not formatted. CB-157
* Audio playback issue CB-142
* Redirect issue trackers to apache
* Wrong slash :: CB-184
* Removed unnecessary navigation blocking for # CB-185
* Added js Connection.CELL for generic cellular connection.
* Fix for single document - multipage layouts
* Added VERSION file to be like other platforms.
* Fixes for loading local XHR using file API, and still using default for remote XHR. responseXML returns document for local files.
* updated phonegap.js to include XHR updates
* Compass API fixes
* 1.4.0 version changes

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list.

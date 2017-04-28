---
title: PhoneGap 1.6 Released!
date: 2012-04-11 20:14:35 Z
categories:
- app
tags:
- Release
author: Steve Gill
status: publish
type: post
format: html
---

We are happy to announce the release of [PhoneGap 1.6](https://phonegap.com/download)! The PhoneGap/Apache Cordova Community has worked hard to fix many bugs (including the nasty local storage bug caused by the iOS 5.1 update) and added some new features.

The biggest news is that Cordova-JS is now on Android, iOS, Windows Phone and BlackBerry! Cordova-JS brings a unified Javascript layer to the PhoneGap project making it more consistent and streamlined. "The inclusions of Cordova-JS paves the path for public plugin API and associated tooling," says Brian LeRoux, one of the key PhoneGap dev leads. You can read more about Cordova-JS [here](https://phonegap.com/2012/03/21/introducing-cordova-js/).

Check out the release notes below to see all of the enhancements and fixes.

## iOS

* Updates for Media API
* Contacts updates for Unified JavaScript
* Fixed Contacts.save return value and Notification.confirm
* Changed Device initialization to use a require-based pattern
* Added require syntax for firing events in ios
* Added a getConnectionInfo method for compatibility
* Added require in pluginresult helper functions
* Updated plist of plugin names -> classes to adhere to common labels in other platforms
* Rewrite of accelerometer code and removed DeviceInfo old init approach
* Added warning about changing compiler settings in xcode
* Changed Accel values to doubles
* Tweaked battery plugin for cordova-js use
* Updated interface to get Camera working.
* Rewrote Location class to use cordova-js unified approach.
* Updated refs from require("cordova") to just "cordova", and other require calls to cordova.require
* Updated sub-project cordovalib steps
* Fixed Compass, Location for cordova-js integration
* Added unification of accelerometer values on ios (based on android values)
* Removed old JS, added cordova-js version
* Changes to CordovaLib makefile for generating JS
* Fixed CB-260: Can't install Phonegap with new Xcode 4.3
* Fixed Xcode app detection (using Spotlight) in Makefile
* Fixed CB-306 - Remove extra template App delegate methods
* Fixes CB-255 - iOS: a parameter with value 'null' is not passed to 'arguments' array
* Fixed CB-236 - Add ContentLength Header in Upload request
* Fixed CB-300 - CDVFileTransfer crashes with 303 and empty response
* Fixed CB-148, CB-316: Playing HTTP / HTTPS urls using the Media API is not working
* Improved Makefile for mixed Xcode 4.2 and Xcode 4.3.1 environment.
* Fixed CB-329 - Add warning if multi-tasking is not supported on an iOS device (to console log)
* Fixed CB-317 : Xcode: Shell Script Invocation Error when directory has spaces in name
* Fixed CB-330 - localStorage / SQLDatabase no longer persistent after iOS 5.01 update
* Fixed CB-347 - iOS 5.1 localStorage / SQLDatabase error after upgrading an app
* Fixed shell script error - picks up new location of cordova.js (unified) now
* Fixed NOTICE file with correct project name
* Fixed CB-49 - UUID replacement
* Fixed CB-361 & use timeout to turn off compass sensor
* Fixed CB-427 - add back iOS only getPicture options
* Fixed CB-349 - Remove sessionKey usage (unused) in CDVViewController
* Fixed CB-237 - Updated splash screen assets
* Fixed CB-387 - try/catch wrapper in native iOS code for cordova-js initialization firing alerts when page without cordova.js is loaded in
* Fixed CB-425 - Notification buttons and title are not working for confirm and alert
* Fixed CB-440 - (LLVM-GCC only) Wrong number of arguments specified for 'deprecated' attribute
* Fixed CB-441 - make fails if PackageMaker.app installed at a path with spaces in a folder name.
* Fixed CB-444 - Xcode template new project - AppDelegate's self.invokeString usage was removed
* Fixed CB-380 - Update Cordova Upgrade Guide for 1.6.0
* Fixed CB-445 - Update "How to use Cordova as Component" Guide for 1.6.0
* Fixed CB-381 - Update Cordova Plugin Upgrade Guide for 1.6.0
* Fixed CB-406 - Update README.md
* Fixed CB-433 - CDVFileTransfer.m methods - convert use of "options" object into "arguments" array
* Fixed CB-377 - add a check for PM_APP, XC_APP, and DEVELOPER in the Makefile
* REMOVED: navigator.splashscreen JavaScript interface (was unofficial) - use cordova.exec(null, null, "SplashScreen", "hide", []) OR cordova.exec(null, null, "SplashScreen", "show", [])

## BlackBerry

* Sync up with cordova-js
* Sync BB network native code with cordova-js
* Sync native Capture implementation with cordova-js
* Switch to cordova.require
* Switch to Cordova artwork for icon and loading screen
* Update build to use unified js
* Provide workaround for OS 7 file rename failures
* Normalize Accelerometer values and cleanup
* Sync plugins.xml with NetworkStatus change
* Update the distribution README file
* Cleanup sample html file for 1.6
* Update javascript to latest cordova-js
* Update version to 1.6.0rc1
* Update javascript to 1.6.0 version
* Update version to 1.6.0.

## Android

* [CB-352] Support initializing DroidGap with existing WebView, WebViewClient and webViewChrome
* [CB-353] Create PluginEntry object to use by PluginManager
* [CB-367] Back button event should fire on key up not key down Also changed menu key and search key to be consistent.
* Tests to verify Android native features.
* [CB-423] Problem displaying patch-9 splash screen.
* Update project template cordova.js reference and title.
* Update to version 1.6.0.
* switched from "require" syntax to "cordova.require"
* cordova.require("cordova") is pretty funny. wish i didnt write it
* updates to JS: removing require+define from global scope, tweaking geolocation code, online/offline events fire on document now
* removed old javascript files and removed unused target + commented out lines in build.xml
* spacing fixes, null check in getPhoneType in contacts, returning error integers instead of objects in contacts
* updating network status plugin label and updating cordova-js to latest
* We show the default 404 on non-resolved domains
* Fixing CB-210 with patch and adding fix for CB-210
* Tweaked File Transfer to fix CB-74
* Changing to the modern icon
* Added temporary Cordova splash for now
* Checking for the callback server before we call sendJavascript for the Kindle Fire, CB-247
* Fixing CB-343: We need to respect the whitelist
* Fixing a bug with File Upload on Android where Chunked mode isn't used by default
* First stab at CB-21, I really need more info before I can close this
* Tagged 1.6rc1
* Fixing the template, since this doesn't have to be unit tested. :)
* Starting Release Process
* Updating the sample index.html
* Updating with tagged JS
* CB-383: Fixes issue with misspelled destinationType for Camera.getPicture()
* Fix for CB-389: resolveLocalFileSystemURI does not work on a resized image captured from Camera.getPicture()
* Fixing license header in com.phonegap.api.PluginManager
* CB-321: Media API: 'mediaSuccess' callback param to new Media() is called soon after new obj created
* CB-163: contactFindOptions.filter does not work as expected on Android
* CB-426: camera.getPicture ignores mediaType in 1.5
* Updating cordova.android.js for CB-421 and CB-426
* CB-438: File metadata.modificationTime returns an invalid date
* Return MediaError object and not error code from native side of Media API
* CB-446: Enhance setting data source for local files in AudioPlayer
* CB-453: FileWriter.append - Chinese characters are not appended to the file correctly
* CB-446: Enhance setting data source for local files in AudioPlayer

## Windows

* file download API
* CB-342 still had navigation to WP7GapClassLib
* ignore DS_Store files
* ignore generated files
* Mark Cast callbacks as Obsolete
* remove Cast callbacks from Capture
* update device version 1.6.0
* update tests for 1.6
* update js to 1.6.0
* added notice
* contact formatting issues
* Changes for use with commoner cordova-js
* actually this was a rename ...
* When execScript fails, it will continue to fail even with an separate thread and multiple tries.
* updated mobile spec tests for CordovaJS
* removed gen'd js file
* spec pages cleanup
* ignore changes to the CordovaSourceDictionary.xml
* include battery tests in 'all'
* minor cleanup
* removed unused resources
* built cordova-js for WP7 1.6.0
* update template for 1.6.0
* updated readme, added resource files to BuildStep
* actual VS project parsing, to avoid including hidden files ex. .git folders
* updated template to use new build script
* Dispatching onNativeReady trigger from native side on separate patch with slight delay. Definitely need to tweak the delay
* Added a constant to multiply accelerometer values by, fixes CB-152 for WP7
* Added timestamp to accel return method
* [CB-460] Added Battery class that at least returns whether the device is plugged in or not
* Added "create" media action
* Fixed CB-459, now back button integrated
* tweaked how native side picks up on non-command-based exec calls (specifically for back button overriding)

## Webos

* Added initial compass support
* added HP copyright notice
* Added compassAPI function
* Added mapping for compassAPI
* update sample application to demo compass api
* changes for [https://issues.apache.org/jira/browse/CB-231](https://issues.apache.org/jira/browse/CB-231)
* add LICENSE & NOTICE file, CB-356
* replace phonegap links with apache cordova links CB-404
* update cordova splash / app icon; CB-237
* added network connection api
* added network connection type api
* get compass api to pass mobile spec tests
* changes for [https://issues.apache.org/jira/browse/CB-231](https://issues.apache.org/jira/browse/CB-231)
* add LICENSE & NOTICE file, CB-356
* replace phonegap links with apache cordova links CB-404
* update cordova splash / app icon; CB-237
* added network connection api
* added network connection type api
* get compass api to pass mobile spec tests

## Bada

* tagging 1.6.0rc1
* CB-405 updating README.rd
* more renaming
* changing VERSION to 1.6.0

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list. All bugs can be found on our [issue tracker](https://issues.apache.org/jira/browse/CB).

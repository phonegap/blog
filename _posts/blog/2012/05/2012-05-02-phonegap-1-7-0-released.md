---
title: PhoneGap 1.7.0 Released!
date: 2012-05-02 17:37:10 Z
categories:
- app
tags:
- Release
author: Steve Gill
status: publish
type: post
format: html
---

We have just released PhoneGap 1.7.0! Thanks to everyone who downloaded 1.7.0rc1\. This release focuses on bug fixes, bug fixes and... more bug fixes! We also added support for Bada 2.0!

You can view the rest of the changes below in the change log.

## iOS

* Fixed CB-183, CB-54 - ios camera targetWidth/Height don't match the documentation Fixes CB-183 and CB-54
* Fixed CB-511 Changed deviceproperties version to "cordova" property
* Fixed CB-483 - FileTransfer - unknown property attribute 'atomic' when building from source (Xcode 3 only)
* Fixed CB-507 - Remove excessive debug logging in execute delegate method in CDVViewController
* Implemented CB-536 - Add new selector to CDVViewController to create a new CDVCordovaView, so subclasses can override it
* Workaround for CB-509 - geolocation.clearWatch doesn't shut the GPS down under iOS Fixed CB-537 - media.seekTo fails with NSRangeException
* Fixed CB-544 - iOS Geolocation fails if Cordova.plist EnableLocation = YES
* Fixed CB-543 - FileTransfer.upload WebKit discarded an uncaught exception
* Fixed CB-391 - camera.getPicture crash
* Implemented CB-535 - Add a way to log JavaScript exceptions, parse errors, and get JS stack frame events (with line numbers, etc)
* Fixed CB-494 - Move Cordova.plist section from "How to use Cordova as a Component Guide" to its own doc
* Fixed CB-571 - stubbed out create method to remove error when creating Media objects, also added another check if file does not exist.
* Fixed CB-386 - added retina iPad splash screens. made sure retina ipad icon files shows up during load.
* Re-fix CB-347 - localStorage / SQLDatabase Error after App update (timing issue for applying fix)
* Adjust splash screen position based on orientation and status bar size

## Android

* [CB-164] Changed network plugin to sync from async and removed setKeepCallback(true) on plugin result in there. Fixes location.reload() not firing deviceready due to network plugin being unresponsive
* Proper fix for CB-164. Online/offline events now propagated to webview properly
* [CB-473] run ant clean before ant debug install
* CB-480 work, back button and history issues are preventing this from being tested properly
* Fixed back button behaviour. WIN
* Reverting the back button change that I made, for some reason certain methods aren't inherited when you extend DroidGap
* Fix for CB-549
* Updating the JS and re-tagging 1.7.0
* CB-539: FileTransfer.download fails when target starts with 'file://'
* Removing un-needed logs
* Refactor Android SplashScreen
* Adding SplashScreen plugin to plugins.xml

## Windows

* added issue with regards to debugging media functionality in the framework to the README
* Updating various script files to latest
* added hint to debug output when device ready cannot fire because the dev did not include the tag in their page.
* release was private, and therefore uncallable from js
* changed test project to use updated tests + jasmine
* remove method added, dispatches not supported error
* debug output for exception in ProcessCommand
* remove unused
* added mouse support
* fancy animation on load, ala metro style
* splash image is animated away on load
* update JS from cordova-js, update version file
* rebuild of lib + template gen
* Added notification alert/confirm button text. CB-110
* remove version number from readme instructions so we don't have to change it every time.
* remove old build cruft
* rejigger, packaged zip is rc1 but assets are 1.7.0
* updates 1.7.0.js file with latest changes, remove rc version
* fetch meta viewport on page load
* CB-596
* wip for handling both meta + preventDefault
* metaviewport tag content attribute user-scalable yes|no is observed.
* added tagged 1.7.0 js src, alert patch in template with comment
* 1.7.0 release packaging
* remove old template
* update example to 1.7.0
* filetransfer download returns FileEntry on success
* repackage for 1.7.0
* updated test project for jasmine tests
* update template for 1.7.0
* Fixed filetransfer boundary without parameter.
* [CB-559] Cache instantiated plugins in CommandFactory
* [CB-338] fixing firing online and offline events
* [CB-336] getFormatData did not return due to threading issues in Capture.cs
* [CB-334] Nickname was not being returned properly in contacts.search

## Bada

* added Bada 2.0 support

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list. All bugs can be found on our [issue tracker](https://issues.apache.org/jira/browse/CB).

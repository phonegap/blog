---
title: Phonegap 1 8 0 Released
date: 2012-06-06 00:00:00 Z
---

We have just released PhoneGap 1.8.0! Thanks to everyone who downloaded 1.8.0rc1\. This release focuses on bug fixes!

Curious about our release schedule? Read [Brian LeRoux's](http://twitter.com/brianleroux) blog post, [Rolling Releases: How Apache Cordova becomes PhoneGap and Why](https://phonegap.com/2012/04/12/rolling-releases-how-apache-cordova-becomes-phonegap-and-why/) to get more background.

View the 1.8.0 changes below in the change log:

## iOS

* Fixes CB-819 fail callback not invoked
* [CB-794] Add HTTP status code to FileTransferError object for iOS
* [CB-359] Updates to adhere to W3C spec for geolocation. Changing actions based on changes incorporated into cordova-js
* [CB-683] pause/resume events now should pass in event object into handlers
* [CB-464] rewrite of accel plugin, simplified accel to start/stop actions.
* [CB-623] added Logger plugin
* Fixed CB-513 - Remove cast functionality from CDVPluginResult, obsolete
* Fixed CB-594 - Remove checks for retainCount
* Fixed CB-637 - Add a doc on how to update the template project in the bin subfolder Updated bin folder scripts.
* Fixed CB-669 - verify.sh file in a new Cordova-based application project should not be included in the .app bundle
* Fixes CB-471 - LocalFileSystem.PERSISTENT "do not back up" file attribute iOS
* Fixed typo in File.getMetadata - error callback had OK instead of ERROR status
* Fixes CB-610 - Capture.bundle missing microphone image resources for retina iPad results in mis-drawn recording interface
* Fixes CB-751 - Undefined function is called when orientation change
* Fixes CB-754 - Use of -weak_library in 'other library flags' of generated template XCode app causes crashes in Simulator when Obj-C Blocks are used
* Fixes CB-628 - Scrub installation process, document artifacts of Xcode 3 support, mention no ARC
* Fixed CB-628 - Scrub installation process, document artifacts of Xcode 3 support, mention no ARC
* Fixes CB-684 - Not enough time for background execution of WebSQL/LocalStorage backup (when app goes to the background)
* Fixes CB-766 - Update bin/debug shell script to point to Homebrew ios-sim 1.4 download Fixes CB-464 - Refactor accelerometer native code in iOS
* Fixes CB-760 - Camera returns incorrect image size
* Fixed warning in CDVLocation
* Fixed EXCBADACCESS error in CDVAccelerometer
* Fixes CB-818 - Make CDVViewController also implement initWithNibName
* Fixes CB-825 - Makefile: remove direct download of Markdown and wkhtmltopdf (uses homebrew to download)
* Fixes CB-328 - Cordova crashes on iOS 3.x devices
* Cordova 1.8.0 Release Notes 1/13
* Fixes CB-851 - guide for using url schemes in iOS

## Android

* Properly querying the Andoid content DB when deleteing an image file
* Switch to using stripFileProtocol in FileUtils.notifyDelete
* Fix problem in Android template example getPicture
* CB-808: CameraLauncher leaks bitmaps in Android
* CB-837: CaptureCB - mediaFile.fullPath does not resolve to file
* CB-844: Contact.find does not return urls
* CB-849: Cannot search by birthday
* Change 'websites' to 'urls'
* Cb-858: Media record defaults to sdcard which may not be mounted
* CB-860: MediaFile.getFormatData broken for Image from Capture
* [CB-659] create script should work on android
* [CB-659] create script for android on windows now works fully. also pulls down commons-codec jar appropriately
* Make PluginResult return valid JSON so the JS side can use JSON.parse
* updated create script CB 839
* Fix README.md formatting to install commons-codec-1.6.jar
* We should not be having a compiled version of cordova.jar in the test directory
* Adding Apache Header to Test Directory
* Forgot to add lifecycle/index2.html's header
* Adding more Apache Headers. Not sure if this should have headers or not
* Working towards Apache compliance
* Adding more Apache licence headers
* Accidentally committed a vim swp file
* Adding header to test cordova.xml
* updating the test plugins
* Removing Default Android Graphics and replacing them with our own
* Removing the commons-codec
* Updating README telling people to copy commons-codec
* Modifying generated classpath
* Don't commit Eclipse preferences
* Tweaked create so it fetches the commons-codec using curl
* Auto detect whether we have the jar already. Also, just create the directory whether it exists or not
* Changing from currentTimeMillis to nanoTime, we need precision on Android 2.3
* Updating the JS and the version for tagging
* dont check in node_modules peepz!
* added package.json for npm install goodness
* documented running npm install
* comeat me lawyers
* adding node_modules to gitignore
* restructured geolocation plugin
* Fixes for new geo stuff
* axing lowercase java file
* adding uppercase java file!
* updating JS to latest for geolocation updates
* [CB-683] Pause and resume events should route through fireDocumentEvent so we get the event object passed into the handler
* [CB-683] updating JS for fix for 683
* [CB-804] ADded proper cordova icon sizes for the create script
* [CB-463] rewrite of accel plugin
* [CB-463] added the JS updates for accel refactor
* [CB-463] added accuracy checking to native accel implementation, this way getCurrentAcceleration returns fairly accurate results
* removed a trailing log
* [CB-463] added accuracy checking to native accel implementation, this way getCurrentAcceleration returns fairly accurate results
* removed a trailing log
* [CB-463] updated js and rewrote accel plugin again to support the start/stop approach. optimized. single callback used for message passing
* Small spacing fixes
* [CB-792] Add HTTP status code to FileTransferError
* Fix calling cordova.plugin.storage.failQuery function from native code

## BlackBerry

* [CB-465] First pass at accel update. Watch acceleration doesnt seem to work yet though
* [CB-465] Simplified accel plugin (still based on Drews implementation) to just start/stop actions.
* [CB-642] Add license headers according to apache RAT
* Move org.apache.cordova.media to org.apache.cordova.capture.
* Add Media API.
* [CB-762] Change BlackBerry plugin from Contact to Contacts.
* Prefix file:// protocol for resolveLocalFileSystemURI if not specified.
* Move FileUtils from org.apache.cordova.file to org.apache.cordova.util.
* [CB-465] Refactor Accelerometer code for addWatch / clearWatch.
* [CB-822] Revert change to prefix file protocol for resolveLocalFileSystemURI
* [CB-793] Minor formatting cleanup.
* [CB-847] Recognize .MP4 as video recording extension.
* [CB-793] Add HTTP status code to FileTransferError object

## Windows Phone

* create new project CLI
* [CB-466] Rewrite accel for WP7
* CB-520 : back button handling is performed in js code and uses window.history.back()
* parent path is now a string and not a FileEntry CB-665
* added try/catch for backbutton handling when a page is not loaded in the webbrowser, was an exception
* filepath contains the extra slash to match other devices, and passes tests that expect specific filepath string values, although cannonically the same
* added output log for audio file not found
* added deploy tool to install and launch on device WIP
* removed duplicate mobile-spec tests, test project now redirects to tests hosted in the gh_pages branch of mobilespec
* debug + emulate scripts
* added usage, and parameterized device to deploy to
* added command line tools to template
* removed debug log
* updated bare template with latest changes
* Fixed threading issue in audio, + Defect [CB-602], added more info to log statements, INFO/ERROR
* removed calls to resolve DNS because they take 30 seconds when no network is available and prevent deviceready
* commented out unused - unminified js code
* Consolidated exception handling + option parsing
* update assembly info for 1.8
* added platform info, for sanity
* updated example,templates,tests to 1.8.0rc1
* updated tests + example
* [CB-643] Added license headers where appropriate.

## WebOS

* modifications to OS checking in Makefile
* CB-557 make sure Makefile works on Win & OSX
* update to 1.8.0
* added Apache license header

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list. All bugs can be found on our [issue tracker](https://issues.apache.org/jira/browse/CB).

Looking for older versions of PhoneGap? Download PhoneGap 1.7.0 and earlier from [Github](https://github.com/phonegap/phonegap/tags).

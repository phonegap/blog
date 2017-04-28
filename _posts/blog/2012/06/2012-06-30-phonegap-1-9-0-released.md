---
title: PhoneGap 1.9.0 Released!
date: 2012-06-30 00:56:43 Z
categories:
- app
tags:
- Release
author: Steve Gill
status: publish
type: post
format: html
---

We have just released PhoneGap 1.9.0! Thanks to everyone who downloaded 1.9.0rc1\. This release focuses on bug fixes, the long awaited inclusion of Cordova webview on Android (Cleaver on iOS), and the inclusion of create scripts for Android, iOS and BlackBerry.

Cordova webview (Cleaver on iOS) allows integration of PhoneGap, as a view fragment, into a bigger native application. Stay tuned for a blog post going over Cordova webview in more detail. For now, you can find out how to embed a Cordova webview over at [http://docs.phonegap.com](http://docs.phonegap.com).

**Note:** Some PhoneGap Android plugins might have issues working with this latest version. If you are using plugins, please make sure to do some tests before upgrading.

Curious about our release schedule? Read [Brian LeRoux's](http://twitter.com/brianleroux) blog post, [Rolling Releases: How Apache Cordova becomes PhoneGap and Why](https://phonegap.com/2012/04/12/rolling-releases-how-apache-cordova-becomes-phonegap-and-why/) to get more background.

View the 1.9.0 changes below in the change log:

## iOS

* Fixes CB-915 - Pause/resume events get fired twice
* Fixes CB-877 - Opening a .doc file under iOS causes the file system API to break (and any other plugins that may use NSMutableArray pop)
* Fixes CB-864 - Failure in writing a large file blocks Cordova
* Fixes CB-907 - Wrong URL encoding when downloading/uploading files from/to URLs with Unicode characters in the path
* Fixes CB-906 - Hardware mute button doesn't effect Media API playback
* Fixes CB-879 - Support to set the volume when playing short sounds
* Enhanced CB-471 - LocalFileSystem.PERSISTENT "do not back up" file attribute iOS. Supports new iOS 5.1 iCloud Backup attribute (the old way is deprecated, and only for iOS 5.0.1)
* Fixed CB-748 - refactored-UUID is broken and changes over time (changed according to Apple's guidelines for this)
* Fixes CB-647 - Prefix/Namespace common native libraries
* Fixes CB-961 - Can not remove contact property values anymore
* Fixes CB-977 - MediaFile.getFormatData failing
* [CB-943] decrease accelerometer interval from 100ms to 40ms
* [CB-982] add usage help to create script, remove unnecessary parameters from debug project-level script
* Removing component guide; going into the docs
* Fixes CB-957 - (iOS) iOS Upgrade Guide Migration
* Updated CB-957 - Include Xcode 4 requirement
* Fixes CB-914 - Deactivate CDVLocalStorage (Backup/Restore, safari web preferences update)
* [CB-914] Added BackupWebStorage setting in cli template
* Enhanced CB-471 - LocalFileSystem.PERSISTENT "do not back up" file attribute iOS. Supports new iOS 5.1 iCloud Backup attribute (the old way is deprecated, and only for iOS 5.0.1)
* Fixed CB-748 - refactored-UUID is broken and changes over time (changed according to Apple's guidelines for this)
* Fixes CB-647 - Prefix/Namespace common native libraries
* Fixes CB-942 - iOS failing FileTransfer malformed URL tests
* Updated CB-957 - Include Xcode 4 requirement
* Fixes CB-914 - Deactivate CDVLocalStorage (Backup/Restore, safari web preferences update)
* [CB-765] Header Support iOS FileTransfer upload
* Removed Upgrade Guide and Cleaver Guide from repo - they are all in the [PhoneGap docs](http://docs.phonegap.com) now
* [CB-863] Splash screen on iOS not using localized UILaunchImageFile value

## Android

* adding a new create script
* updating script to cleanup on exit/error
* testing create2 script
* updating Windows !@#% build script
* removing old create and templates
* renaming create2 and templates2
* updating templates reference
* renaming create2
* updating cordova.js version
* fixing create script
* adding tools verification to batch file
* updating build.xml templates reference
* checking if project exits
* updated reference in test
* deleting old stuff
* updating test for CB-916
* adding bash helper scripts
* updating bash create script and node test
* adding appinfo
* updating windows create.js and creating node test
* adding windows scripts
* fixing create
* windows build/debug/launch scripts
* removing echoes
* deleting old BOOM
* setting +x on script files
* forgot to add +x on BOOM
* creating project without source
* updating create script to work from distro and source
* log was actually doing nothing...fixing it
* CB-937 fixing debug
* CB-937 fixing debug for windows
* Formating and removal of commented code.
* Add exit message.
* Update for getActivity().
* Add comments.
* Enable onMessage() to return a value.
* CB-369: Authentication Code doesn't seem to work. -- Verified basic auth works and provided test case.
* CB-779: Verify that fullscreen and backgroundColor preferences are set properly - This check-in enables fullscreen and adds test for it.
* Add usage comment.
* Remove unused imports.
* CB-800: Fix preferences for the CordovaWebView. - Test case needed to implement CordovaInterface.
* Optimize loading "about:blank"
* Need to call pluginManager.onDestroy() to clean up plugins.
* Backbutton broken by adding new onKeyDown method without calling its super.
* Fix exception when defaultValue=null.
* Support showing the app title bar through a preference.
* CB-481 refactored prompt() call in JS to exec, moved showing of webview out of chrome client and into app plugin (so we can invoke via exec)
* small tweaks to readme re: testing
* Merging in use of uri variable between Simon and my changes.
* Added MediaScanner abilities to camera launcher plugin. Now images saved to SD card should show up in the android gallery app right away
* Removing images and saving images to jail if SaveToPhotoAlbum is set to true
* Tacked on file extension to camera file
* added . in front of the temp files passed into camera app. presumably this hsould stop the gallery app from picking it up
* Fixed the 0-byte files in gallery. Also fixed exif rewriter for saveToPhotoAlbum:false JPG files. Thanks for your help Simon!
* Merging in use of uri variable between Simon and my changes.
* Refactored cleanup in camera code a bit. Removed overrides for Scanner functionality
* Removed some legacy button code that existed in droidgap + app plugins
* Removing CordovaWebView Guide; its going into the docs
* Creating the CordovaWebView, modifying DroidGap to use that
* Adding the tests from the GitHub Prototype
* Cleaning out the asssets/www directory. This should house mobile-spec
* Work on CB-369, Moving Authentication OUT of DroidGap
* Moving whitelisting into the WebView, still need to read the config in the WebView if required
* Moving init code into the WebView
* Partially moved the callback server into the WebView. The WebView MUST own the CordovaWebViewClient and the CordovaWebChromeClient
* Minor tweaks to DroidGap, allows for the ChromeClient and ViewClient to be overridden
* Move the callback server into the View, preparing to start CordovaWebView testing
* Tweaking DroidGap so it compiles into a JAR, starting testing
* Updating the tests a bit, still not running
* Fixing the manifest errors
* Managed to get this building minus Jail Activity, still a long way to go
* Rolling back half-baked change that broke the code in the branch, we need to rethink the Callback Server
* Working. Pushing the callback server change again.
* Massive refactor of CordovaInterface. Deprecation and Exception throwing to notify the user that we're changing things
* Updated tweaks to get up and running
* Removing runnable code for timeout because it's not thread-safe
* Adding old code back, we can't access webViewClient methods without them being on the UI thread. :(
* Added another runnable, this code is hideously awful
* Removing Jail functions for now
* Removing the cordova jar, it shouldn't be in the repo
* Adding the CordovaException class
* Changing viewClient to default visibility
* Fixed the bug caused when running on Eclipse
* Minor tweak to the test so it loads the correct HTML
* Starting to move the history into the CordovaWebView, and getting the WebDriver working again
* Tweaks to move history over into the WebView
* Adding screenshot and activity to the test, although Actvity isn't a standard plugin
* Moving preferences into CordovaWebView, need to discuss prefs when using CordovaWebView
* Working on CB-585
* Adding Apache headers to the new classes
* Adding Apache headers to the tests on the branch
* Removing the hacked-up jars that I used to get this to work, since I can't distribute them
* Updating the history configuration. We can switch between histories
* Added loadConfiguration to the standalone WebView
* Updating the project, removing generated artifacts
* Moving the Callback Server Start/Stop to the onPageStarted fixed timing errors
* A quick stab at CB-510
* Broke the merge, need to add GPSListener.java
* Adding empty tests. May have to re-think the way we test this method
* Updating Activities
* Forgot to recheck Plugin. Adding it back
* Removing tests that don't work and modifying CordovaWebView so it works as a stand-alone component again. Mobile-spec currently doesn't work
* Setting up a default CordovaWebViewClient and CordovaChromeClient for when we are blowing up via XML layouts
* Forgot to add the proper constructor. The Clients need to know about their webView.
* First Draft of how to use CordovaWebView
* Added JUnit to the README, removed WebDriver for now. Need to figure out distribution.
* Adding the Cordova Upgrade Guide
* Removing the classes we agreed were not used
* Adding tests to the README
* Two automated tests completed
* Missed this error in the merge commit
* Working on tests
* Weird merge error. Yo dawg, I heard you like catching exceptions, so we put a catch around your catch. FAIL
* Adding logs
* CB-582: Automating User WebView/WebViewClient/WebChromeClient tests
* Adding the WebDriver Tests
* Fixing up tests
* This is a poorly written test. What was I thinking?
* Fixing up tests
* This is a poorly written test. What was I thinking?
* I think we need to rethink how we automate this test
* Removed merge because I missed the preference set
* Adding more undocumented features for app title bar and full-screen
* Default should be false not true
* One more time, getting the title default right
* Starting the Buttons Branch
* Tweaks to CordovaWebView to support other keys
* Fixing work-around to work for both ? and #
* Adding updated JS
* Since we moved binding of buttons into a view, let's remove it from the Interface
* Weird merge error didn't account for isBackButtonBound
* Re-adding getContext because yo dawg, I heard you like contexts in your contexts
* Forgot to add it renderscript.opt.level to the project. This will fix ant issues
* Add Android 4.0 workaround for links with params
* Fix imports for changes in 45680a5
* add volumeupbutton/volumedownbutton events
* prevent volumeup/down default behaviour
* listening to volume events now override default behaviour
* upgrade to latest cordova.android.js
* updated NOTICE file
* CB-878: Splash screen in Android fullscreen mode showing not correct
* Adding getContext, startActivity to CordovaInterface
* Revert: Adding getContext, startActivity to CordovaInterface
* Removed need for getFormatData/Image to load image into memory
* CB-920: FileTransfer UTF-8 bug
* Fixing merge error in FileUtils.notifyDelete
* CB-883: SplashScreen without show() method, only hide()
* CB-910: Camera out of memory error
* CB-919: Camera Plugin returned with empty error message
* CB-978: FileTransfer.upload from a directory with a space fails
* Decode image from File instead of content resolver
* Cache bust returned Image URI if saveToPhotoAlbum is false
* Switch getPicture from Gallery to use file instead of content resolver
* Using a better scaling algorithm to resize the image
* Fix double image problem on Samsung phones
* Rotate image if taken in portrait mode
* Reset orientation exif information when photo is rotated
* Wire rotation fix to correctOrientation parameter
* Only load Exif information if necessary
* Tagging to 1.9.0

## BlackBerry

* [CB-980] Quote key values in JSON returned from native.
* [CB-981] Return FILE_NOT_FOUND error for bad file name.
* [CB-606] Added create script for unix and windows
* removed node modules from version control, whoops
* added debug and emulate commands. log not possible on BB/PB
* Removed unused scripts/cruft.
* Added debug flag parameter being passed to widget packager inside ./debug script
* CB-965: fixed create script to work with distribution and src
* [CB-752] Implement saveToPhotoAlbum CameraOption on bb device
* Forgot to update version file
* [CB-962] Fix for debug script not working on bb
* [CB-962] Making build script work again with ant build and load-device commands on bb
* Made sure cordova scripts are executable when copied over
* Re-fixed cordova scripts being able to execute in bb
* Added in captureAudio for playbook
* Fixed up whitespace/tab issue
* Adding in microphone permission/feature to config
* [CB-973] Fixed up tab issue
* [CB-962] - File permission stuff got overwritten in last few commits - bringing it back
* [CB-965] - windows version of create script failing
* [CB-965] - needed flag for destination directory
* 1.9.0

## Windows Phone

* Capture parses EXIF data and rotates image based on EXIF_Orientation
* camera API rotates image based on EXIF data
* removed Debug logging, cleanup
* added license header
* fixed exiflib link
* added image capture view - wip
* CB-668 UploadOptions does not serialize Params
* update version numbers
* updated js file
* update example
* updated test proj
* CB-953 mouse events fired twice
* js+path updates for 1.9.0 release
* rebuilt for 1.9.0 release
* Minor improvement for CB-953 mouse events fired twice
* [CB-795] Added HTTP status code to WP7 FileTransferError interface. Catches 404 on download.
* CB-570 resize image if user defined width & height provided
* code formatting ResizePhoto method name for code consistency
* Created VS Package for automatically deploying the project template into visual studio

If you wish to follow or join in the development of this project, send an email to [callback-dev-subscribe@incubator.apache.org](mailto:callback-dev-subscribe@incubator.apache.org) to subscribe to the developer mailing list. All bugs can be found on our [issue tracker](https://issues.apache.org/jira/browse/CB).

Looking for older versions of PhoneGap? Download PhoneGap 1.8.1 and earlier from [Github](https://github.com/phonegap/phonegap/tags).

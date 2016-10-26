---
title: PhoneGap 0.9.5 Released!
date: 2011-04-28 21:40:18 Z
categories:
- app
author: Steve Gill
status: publish
type: post
format: html
---

You can now download PhoneGap 0.9.5\. It was officially released today. Some of you are asking for release notes/change log. You can view the roadmap we followed on the [wiki](http://wiki.phonegap.com/w/page/28291160/roadmap-planning). I have also gone to each repo and pulled the commit logs between 0.9.4 -> 0.9.5\. Here they are for your viewing pleasure.

## iOS

### Becky Gibson (11):

* fix ticket #79 and other file api cleanup
* name change from phonegap-(ver) to phonegap.(ver)
* Updates for different callback function types
* Update PhoneGap.exec mechanism to more closely match other platforms.
* Implementation of Directories and Systems File API
* Update JavaScript so PhoneGap modules are created only once, even if included multiple times.
* Implement readAsDataURL for iOS
* Updates to fileTransfer to conform to documenation
* Updated FileTransfer to return bytesWritten
* Remove files used in older implementation of contacts.
* fix ticket #122 - allow for lossy conversion when encoding data to write to file

### Jesse (6):

* Added Javascript Callback shouldRotateToOrientation which is called before looking up supportedOrientations in the plist. shouldRotateToOrientation should return true or false depending on it's current state/preference. shouldRotateToOrientation is expected to exist in the global scope.
* Fixed setAutoresizingMask. It was accessed as a method when it is a property.
* Lifecycle events pause/resume
* Orientation issue : should always return YES for at least one orientation.
* Anchor tags with `target="_blank"` will correctly open in MobileSafari.
  * Targets of `_self` or `_top` will open in the app.
  * If target is NOT specified, it will open in the app.

### Shazron Abdullah (3):

* Updated the FAQ for Xcode 4.
* Updated issue tracker link in README
* Updated the version to 0.9.5

### ascorbic (1):

* Add FileTransfer

### shazron (27):

* Updated FAQ
* Added i386 to VALID<em>ARCHS in PhoneGapLib project - so running in the Simulator on Xcode 4 works oob
* Updated FAQ for Xcode 4 error
* Fixed annoying grammar errors in FAQ
* Added helper text for xcode config file
* Updated PhoneGapLibTest project for new shell script
* Fixed typo in console.log (maxDepth)
* Crash fix: navigator.network.isReachable, when using the isIpAddress option.
* Fixed static analyzer warnings, set PhoneGapLib compiler to LLVM GCC 4.2
* Updated PhoneGap application template to handle PhoneGapLib and project locations with spaces in it. Fixes issue #130
* Updated Makefile for new phonegap.js filenames, and removed references to the iPad project template.
* Updated installer docs to to reflect latest changes.
* Updated FAQ item regarding issue #130
* Fixed incorrect usage of bzero.
* Shell script to create a PhoneGap project from the command line.
* Fixed create</em>project.sh to handle relative path to folder to put new project in.
* Modified PhoneGap app template project (added explicit SKIP<em>INSTALL=NO) and PhoneGapLib project (added explicit SKIP</em>INSTALL=YES). This is so "Build and Archive" will work properly under Xcode 4. This fix is for a bug that was fixed in Xcode 4.
* Fixed navigator.geolocation.watchPosition to only call the success callback when the position changes (not every single time).     Removed annoying NSLog.
* Re-fix for watchPosition: successCallback is only called in the first instance because navigator.geolocation.lastPosition will always be equal to the position passed in the callback (it would never have changed). Internal var to watchPosition is kept to keep track of the last position.

## Android

### Bryce Curtis (9):

* Logging status from wrong object.
* Worked around JavaScript bridge exception for Android 2.3.  Use "prompt" instead of calling objects directly.  There were several objects called from JavaScript, including BrowserKey, so key events had to be reworked.
* Ticket 106 - Simplify splash screen logic based upon idea from vadim.
* Add support for setting sms body using uri "sms:#?body=text".
* Bug 110 - When you close an app on Android you see a JS error in logcat.
* Add check to only init and run JS code once - even if included multiple times.
* Bug 126: NullPointerException in onDestroy()
* Ticket 136: window.openDatabase() in Android 3.0 throws SECURITY_ERR (most code written by Simon MacDonald - I just tested and checked in)
* Update version to 0.9.5

### Fil Maj (16):

* Fix for ticket 86 (build fail if phonegap-android dir is located under a dir with "lib" in it). Also bug fix in build if config.xml didnt contain an (icon) element.
* Fix for build: version needs to be included in .jar and .js generated files.
* First pass at extracting icon width/height info and assigning to proper resolution dirs (i.e. ldpi, mdpi, hdpi) during build.
* Fix so that if not all icons are specified, doesnt error the build out.
* Use icon with no width/height if specified. Set default icon to highest-resolution icon when possible.
* Issue 107: Always send pause event to JS.
* Issue 107: always send resume event to JS.
* As best a fix as can be made for issue 95: on HTC devices, if text input is in bottom half of page, it does not get scrolled up to top half of page when you tap it and virtual keyboard comes up.
* Fix for lighthouse ticket 115: certain versions of Android 2.2 return "null" for window.openDatabase. Hook in PhoneGap fallback for storage in this case.
* Fix for ticket 121: Checking for null return on native openDatabase call not enough as only allowed one DB per PhoneGap app. Have to proxy openDatabase and check at runtime.
* Partial resolution for ticket 57: some issues with camera functionality not firing callbacks properly.

### Jos Shepherd (1):

* Added native prompt() dialog support

### Mark Darbyshire (1):

* Implement localStorage.key() and localStorage.length     This brings PhoneGap's implementation in line with [the spec](http://dev.w3.org/html5/webstorage/). It makes the following [demo](http://people.w3.org/mike/localstorage.html) work when you include PhoneGap. I was hopeful it would make my app, which makes use of LawnChair, work, but I've had no such luck as of yet.

### Roman (1):

* Hidden NPE fixed, which appeared when someone pass null as arguments
  (for such SQL as e.g. CREATE TABLE).

### Vadim Voituk (1):

* Added CupcakeLocalStorage.clear() method (in according to [the spec](http://dev.w3.org/html5/webstorage/#the-storage-interface))

### macdonst (10):

* File API: System and Directories
* Ticket #90: Move <em>createEvent from File to PhoneGap
* PhoneGap Android Ticket 113:     FileTransfer returns FILE</em>NOT<em>FOUND</em>ERR on http 500 error
* Support old way of adding service in PhoneGap 0.9.5
* Ticket 124: File Transfer multipart badly formed trips mod_security
* Read As Text missing load event call
* W3C Media Capture API
* Ticket 127: Android FileReader/FileWriter methods should return FileError object on error.
* Fixing file commands so that they run async
* Issue 60: Contact search unicode problem

### paulb777 (3):

* JSLint clean JavaScript sources. No fatal errors remain. Options can turn off rest of warnings
* Add networking to example and fix contacts
* Update index.html to Add networking to example

## BlackBerry WebWorks

### Justin Tyberg (26):

* Replace org.json.me JSON Java implementation.
* Add PhoneGap.extend() function for implementing classical inheritance pattern.
* Add PluginResult constructor.
* Add support for W3C File API: Directories and System specification:
* Remove override of 'touchstart' event with 'click' event.
* Update README.md.
* Propagate resume and pause events from PhoneGap JavaScript to PhoneGap     native extension.
* Move file path normalizing method to FileUtils class.
* Add support for null Java values to JSONObject.
* Add JS closure to device.js to avoid creating global Device object.
* Add ApplicationUtils class.
* Add media capture support.
* Add util method to LocalFileSystem to check if path is root file system     path.  Makes for cleaner JavaScript when removing directories.
* Media capture: eliminate duplicate image capture modes in     navigator.device.capture.supportedImageModes.
* Add capability for plugins to delay onDeviceReady until after they     have initialized themselves.
* Cleanup PhoneGap base JS.  Keep from loading more than once.
* Keep navigator.device object from being defined more than once.
* Keep navigator.device.capture from being defined more than once.

### Michael Brooks (4):

* Update project script to allow closing the simulator.
* Update project script to close simulator before load-simulator.
* 18 - Bypass access feature defined by the config.xml
* Update formatting of config.xml

### unknown (1):

* Update FileReader read method signatures to match W3C File API spec.

## webOS

* phonegap-palm depreciated. phonegap WebOS newly added.
* works with webOS 3
* modified how orientation was set and the getCurrentOrientation api notification class was also modified phonegap
* webOS no longer requires Mojo framework

## Bada

* Newly Added!

Cheers,
-Steve Gill

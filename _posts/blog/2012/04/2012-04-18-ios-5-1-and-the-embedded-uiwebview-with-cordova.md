---
title: iOS 5.1 and the embedded UIWebView with Cordova
date: 2012-04-18 20:18:24 Z
categories:
- app
tags:
- Guide
- iOS
author: Shazron Abdullah
status: publish
type: post
format: html
---

[![](/uploads/2012/04/ios51_cordova.png)](/uploads/2012/04/ios51_cordova.png)There are two issues with Apple's iOS 5.1 SDK that are important to Cordova and web developers that use the embedded UIWebView:

1. localStorage and WebSQL databases have been moved to _~/Library/Caches_ from _~/Library/WebKit_
1. "SECURITY_ERR: DOM Exception 18" error when calling window.openDatabase after updating to iOS 5.1

## Persistence of localStorage / WebSQL databases

The first issue is a policy issue -- this change means that localStorage and WebSQL databases are not backed-up and may be deleted by iOS at any time to save space. In the "[Data Storage Guidelines for iCloud](https://developer.apple.com/icloud/documentation/data-storage/)" article it describes data in ~/Library/Caches as "Data that can be downloaded again or regenerated".

You thought localStorage was supposed to be persistent? So did I, but it appears that expiring localStorage is well within the definitions of the spec: [Section 6.1 "Expiring stored data"](http://www.w3.org/TR/webstorage/#user-tracking)

The solution for embedded UIWebView developers is to backup and restore the databases from _~/Library/Caches_ to persistent storage (e.g the Documents folder), or move the storage location to persistent storage.

This issue has been worked around and the backup/restore mechanism is implemented in Cordova 1.6.0, and the issue has been further discussed also in this bug: [https://issues.apache.org/jira/browse/CB-330](https://issues.apache.org/jira/browse/CB-330).

## `SECURITY_ERR`

The second issue appears to be a genuine Apple bug when you are on iOS 5.1, and upgrading an app to a newer version. This issue has been reported to Apple and they know about this issue: [rdar://11081309](rdar://11081309) [rdar://11081647](rdar://11081647) [rdar://10296507](rdar://10296507) [rdar://11105407](rdar://11105407) [rdar://11063678](rdar://11063678)

A sample of what was filed is here: [http://openradar.appspot.com/radar?id=1608403](http://openradar.appspot.com/radar?id=1608403)

Through the community's efforts (see this issue here: [https://issues.apache.org/jira/browse/CB-347](https://issues.apache.org/jira/browse/CB-347)) and our experimentation, we hypothesize that during an app upgrade the app bundle's GUID is changed, but the WebKit database locations in the app's .plist have **not** been changed. These database locations have hard-coded paths in them (which of course include the app bundle's GUID).

The way we arrived at this conclusion is by:

* Printing the app bundle path before and after an app upgrade when on iOS 5.1
* Iterating through the app's .plist keys and values and observing the "_WebDatabaseDirectory_" and "_WebKitLocalStorageDatabasePathPreferenceKey_" values

The data supports our conclusions. The app bundle path does change when upgrading the app (the GUID changes). The plist values which point to database paths within our app bundle point to a path that is not in our app bundle, and the GUID is from the previous app bundle GUID.

This issue has been 'fixed' by Cordova in 1.6.0, by changing the paths in the app's .plist to the correct paths.

Hopefully in a newer version of iOS this issue will have been resolved by Apple by either:

* Changing the database locations in the app's .plist when the app bundle's path changes OR
* Use relative paths for the database locations, not absolute ones

## Changing the database location

For the second issue, it is also clear that a developer can change the database location permanently to persistent storage, and not do the backup/restore method. iOS Cordova is steering clear of this solution because of the potential of side-effects if and when this issue is resolved by Apple.

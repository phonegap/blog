---
title: PhoneGap Static lib for iPhone-XCode
date: 2009-10-27 13:54:48 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2009/10/27/iphonegap/
status: publish
type: post
format: html
---

I recently spent some time evaluating the iPhone branch of PhoneGap and have made some changes that I think will make things easier to develop.

One of the key issues that I wanted to address was that PhoneGap existed as a repository and anyone that made an application with it would invariably have to mix their code in. In a very few cases it is possible to make a complete application using PhoneGap out of the box, but what if you need to add, remove or change something? As soon as you start messing with the core PhoneGap code, you are looking at huge merge issues when updates are pushed to the PhoneGap repo. Most likely you will just ignore any new commits, and your code will be stuck in time from the moment you changed it, or you will have to pick through the updates, and decide what is worth re-implementing in your own codebase.

My changes work as follows: You do not create a PhoneGap app anymore! You create an app that inherits from PhoneGap. This means your PhoneGap code can be in a git repo somewhere (github) while your application code can be in it’s own repo. If there are updates to the PhoneGap codebase then ( _as long as the API has not changed_ ) you simply update PhoneGap and build your app.

In order to make these changes, I had to simplify some of the PhoneGap code. I removed the dependency on XIB files so the UIWebView is now created through code instead of automagically by XCode boilerplate code behind the scenes. The PhoneGap core code is now a static library that you link to and inherit from so there are some things you will have to do to create a new phonegap application. Also keep in mind that this is all subject to change as we are currently looking at ways of making this dead-simple.

You can git the code [here](http://github.com/phonegap/phonegap/tree/plugins/iphone/)

## The new PhoneGap 12 step program

1. In XCode create a new WindowBased iPhone Application.
1. Select the project and add a reference to the PhoneGapLib project. ( The one you downloaded from git )
1. Add a reference to all headers in the PhoneGapLib project ( _these are needed so the compiler can know what you will be linking against, and what the base PhoneGapDelegate protocol looks like_ )
1. Delete the MainWindow.XIB interface builder file that XCode created.
1. In main.h add your app delegate class name to the UIApplicationMain call.
  ex.
  `int retVal = UIApplicationMain(argc, argv, nil,@"MyAppDelegate");`
1. Change the interface of your application delegate to inherit from PhoneGapDelegate.
  ex.
  `@interface MyAppDelegate : PhoneGapDelegate { }`
1. Select the build target in your project and add a dependency for PhoneGapLib.
1. Add **libPhoneGapLib.a** to the ‘Link Binary with Library’ build step.
1. Add the **www** folder to the ‘Copy Bundle Resources’ build step.
1. Place **phonegap.js** in your **www** folder along with all your html/css/js application code.
  _( note: this is a little bit hack-y, and we are looking at ways of improving this step especially )_
1. Add project references to the following frameworks
  * **AddressBook**.framework
  * **AddressBookUI**.framework
  * **AudioToolbox**.framework
  * **AVFoundation**.framework
  * **CFNetwork**.framework
  * **CoreGraphics**.framework
  * **CoreLocation**.framework
  * **Foundation**.framework
  * **MediaPlayer**.framework
  * **QuartzCode**.framework
  * **SystemConfiguration**.framework
  * **UIKit**.framework
1. Build and Go.

## So What’s Next?

Recent PhoneGap discussions have led us to the conclusion that we need a plug-in architecture. It will be much easier to get people to contribute if they can focus on a key piece of functionality and not have to implement things throughout the codebase + it also gives a clearer separation of contributions and would allow for unit testing.  This latest addition/change is a step towards a more plug-able architecture. Thanks also to Shazron for his help, support and suggestions along the way.

So get reviewin’ !!

[› Visit the original post](http://blogs.nitobi.com/jesse/2009/10/27/iphonegap/)

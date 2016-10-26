---
title: BlackBerry Build Script
date: 2009-12-01 22:01:50 Z
categories:
- app
author: Fil
link: http://blogs.nitobi.com/fil/2009/12/01/blackberry-build-script/
status: publish
type: post
format: html
tags_old:
- blackberry
---

Hey everyone,

We've been making some exciting progress with [PhoneGap](http://www.phonegap.com) recently.

![The Ant Window in a PhoneGap BlackBerry project](http://www.nitobi.com/fil/bb/ec_ant.jpg)

The Ant Window in a PhoneGap BlackBerry project

First, the [Mobile Spec](http://github.com/filmaj/mobile-spec) - our own homebrew set of tests for the PhoneGap API - is taking off. People are starting to watch it, fork it, and add to it. I am really stoked to see that - keep it coming!

Second, the PhoneGap team has been working on making developing and building PhoneGap applications easier. A big step towards this was putting together some build scripts so that you - the PhoneGap developer - did not have to go through the same, tedious steps to test and develop applications in your platform's IDE. [Shazron](http://blogs.nitobi.com/shazron) recently rolled out an installer for those iPhone PhoneGap developers out there and I saw it in action (as detailed in [this](http://blogs.nitobi.com/shazron/2009/11/24/phonegap-mobile-spec-tests-on-iphone/) post) - it is hot shit. Super-easy! [Joe](http://blogs.nitobi.com/joe) has the same thing going for Android, the Android.jar he put together is a huge step towards that. So, without further ado, I present to you: an [Apache Ant build script for PhoneGap BlackBerry](http://github.com/filmaj/phonegap/commit/1868917a2c0e4bcaa75a8c24faf0ffb5ca8ffa11)! I've added it to the repository, as well as instructions in the readme on how to use it.

In my short time using it, the biggest win for me as a developer is the ability to build, sign and deploy to device with one command. It's super-fast too - **way** faster than using RIM's 'Desktop Manager' software to load the application onto the device.

If you've tried using it, post to the comments and tell me how it went! I'd be glad to help out, too, if you're having problems.

Have fun!

[› Visit the original post](http://blogs.nitobi.com/fil/2009/12/01/blackberry-build-script/)

---
title: 'Android Testing: The Emulator is your friend'
date: 2010-10-27 00:44:02 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2010/10/26/android-testing-the-emulator-is-your-friend/
status: publish
type: post
format: html
---

A while ago, I broke my Nexus One, and because I switched from Rogers to Telus back in February, I was unable to use my other Nexus One and I had to go back to using the Motorola Milestone as my phone. Now, I'm trying to look at the bright side of this is that I was forced to live like most users of Android, which is that I'm stuck using Android 2.1 (_and while I'll happily root a Nexus One and void it's warranty, I'm a bit more sketched out by the Milestone's Signed Bootloader, and would like a backup phone before going through the rooting process._)

This isn't a huge deal with PhoneGap, except that I found a bug that was only in Android Webkit. The issue is that Motorola's Webkit behaves differently than the stock Emulator Webkit, and that each phone Motorola implements has a unique firmware. That's where the [Motorola Developer Add-Ons](http://developer.motorola.com) came to the rescue. I was able to get Emulator Images that were roughly similar to my phone's build, and was able to confirm the bug. Motorola really stands out with this tool, and it seems that after doing [some](http://developer.htc.com) [initial](http://innovator.samsungmobile.com/galaxyTab.do) [checking](http://developer.sonyericsson.com/), it seems that Samsung only has an emulator for the Galaxy Tab, and not for their other Android devices, HTC doesn't even have an emulator and just offers source so you can patch the [Android Open Source Project](http://source.android.com) and generate your own images. Sony Ericsson has an Emulator for their Android 1.6 devices so if you need to test on the Xperia line, you can test on that as well.

The downside is that the Emulator is painfully slow in comparison to the device. Furthermore, most Emulator Images are still very unfinished, and others have annoying side features. They may be a custom boot animation, or random resolutions that aren't supported. The Android Emulator is definitely the weakest link, and it would be great if we could rely on Android Webkit to be the same across all devices, and behaviours (like proxies) to work across all devices as intended. Unfortunately, life is not that simple.

[› Visit the original post](http://blogs.nitobi.com/joe/2010/10/26/android-testing-the-emulator-is-your-friend/)

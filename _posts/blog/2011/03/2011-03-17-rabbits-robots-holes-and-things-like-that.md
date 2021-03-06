---
title: Rabbits, Robots, Holes and Things like that
date: 2011-03-17 23:25:55 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2011/03/17/rabbits-robots-holes-and-things-like-that/
status: publish
type: post
format: html
---

I finally got some free time to do something that has been nagging me for quite some time, which is attempt to actually debug WebKit. Note that I said WebKit, and not PhoneGap. The main motivation for this was the fact that everyone at Nitobi depends on WebKit to work, and sadly on certain Android devices, certain things like the Android WebKit bridge don't quite work as expected. Now, I understand that this bug doesn't affect the top-of-the line phones like the Nexus One, the Nexus S, the Motorola Droid/Milestone, but could show up on budget devices, such as the Motorola Spice, the HTC MyTouch4G (that cheap thing with the Keyboard from T-Mobile that looks like an HTC Magic), or pretty much every Android device that has a screen smaller than 480×800, since they seem to have the weaker processors and a smaller memory footprint.

So, while we have worked around it, it'd be good to actually fix this problem for everyone, not just for us, so I decided to take a look into this issue. Now, since this is a WebKit failure, I decided that I'm going to have to hook up an Emulator to this process. This is easier said than done, since WebKit is written in C, the build is done on an Ubuntu machine, and this is leading into gdb territory. Furthermore, WebKit is a shared library, NOT an exectuable, and PhoneGap Android is written in Java! How do we go about doing this.

I decided to ask Google, and I found [this entry on the Android Platform group](http://groups.google.com/group/android-platform/browse_thread/thread/92c5c966e85324e2/3a700b662d237959?lnk=gst&q=gdb+webkit#3a700b662d237959) that details the process. Unfortunately, email isn't the clearest way of communicating things, so I'm going to start at the beginning. The first thing you need to do is fetch the Android source, to do this, [follow the steps here](http://source.android.com/source/download.html).

Once you have the source code, the next step in the process is setting the debug flags. To do this, first it's a good idea to run lunch and pick which platform you want to debug this on. Once you do this, you need to copy from build buildspec.mk.default to the root directory of your android repo. Then rename it to buildspec.mk, and add two lines to it:

```make
DEBUG_MODULE_libwebcore:=true
DEBUG_MODULE_libxml2:=true
TARGET_CUSTOM_DEBUG_CFLAGS:=-O0 -mlong-calls
ADDITIONAL_BUILD_PROPERTIES += debug.db.uid=100000
```

Then, since we're doing a debug build, you need to go to external/webkit and edit Android.mk. Uncomment this line:

```make
LOCAL_PRELINK_MODULE := false
```

This will allow you to have HUGE webkit files that won't break your build. Webkit will be extra large due to the fact that you now have debugging symbols included in the libraries. Once this is done, then make the app, and go home. A debug build of WebKit in the AOSP seems to take at least three times as long as a regular Android build. Once it has built, assuming that you picked the Engineering Image for the Android Emulator, you need to specify the the ANDROID_PRODUCT_OUT, then you will be able to start the emulator and get the device going. Once you start the emulator, you need to setup port forwarding:

```bash
adb forward tcp:5039 tcp:5039
```

The next step is pretty important, since this is frustrating. To debug WebKit, start a WebKit process, then attach the Java Debugger to that process. I chose to do this in Eclipse, where it's just like debugging a regular Android app. Once the Java Debugger is attached, then attach gdb to it. It's important to run Android's GDB, and you have a copy of this located in the AOSP tree. Due to the fact that I hate using Eclipse for anything other than Java development, I decided to go and use a tool that I haven't used since my university days, namely DDD, which is a brutally old front-end to GDB, but it works well enough, and gives you access to the GDB command line.

Anyway, to connect GDB up you need to do the following on the device:

```shell
gdbserver 10.0.2.2:5039 --attach pid
```

And in GDB/DDD/whatever, you need to run these commands:

```shell
set solib-absolute-prefix /home/(yourdir)/aosp-official/out/target/product/generic/symbols
set solib-search-path /home/(yourdir)/aosp-official/out/target/product/generic/symbols/system/lib
file /home/(yourdir)/aosp-official/out/target/product/generic/symbols/system/app_process
```

Once you have both debuggers, you need to run cont! Then the app will work until you crash it, where it will show you where it crashed. This is as far as I got with this process. I think it's pretty ridiculous that you need to run two different debuggers with this, but it makes sense, since there's WebKit and there's the Dalvik/Android stuff above WebKit. It's funny listening to people talk about Native vs Web on Android, since in Android's case, the Web Apps are FAR more low-level than things running in Dalvik Virtual Machine. This also may explain the extremely broken nature of WebKit on Android, and why there's so much divergence of WebKit across these platforms.

I'm going to keep working on this. If you know anyone who's actually patched WebKit on Android, or works on this at HTC, Motorola, Google, Samsung or another company, please let me know what your workflow looks like, since it'd be good to get ramped up on this to fix some of the extreme brokenness and quirks that are causing Android's browser to quickly become one of the worst browsers for the web. Given how pro-Android I've been in the past, that should be a sign that things are really broken.

[› Visit the original post](http://blogs.nitobi.com/joe/2011/03/17/rabbits-robots-holes-and-things-like-that/)

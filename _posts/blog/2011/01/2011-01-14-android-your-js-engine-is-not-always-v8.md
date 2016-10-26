---
title: 'Android: Your JS Engine is not always V8'
date: 2011-01-14 18:59:54 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2011/01/14/android-your-js-engine-is-not-always-v8/
status: publish
type: post
format: html
---

Recently, I watched some Mobile Web training, and I noticed that people overlook many things about Android. Namely these facts:

* WebKit is different on every phone
* The Browser and the WebKit engine are different things.
* WebKit can have a different engine

So, as usual I will talk about how the source to Android is OPEN, and how with the source code, I can look at the build scripts and find out what Android ACTUALLY supports instead of doing feature detection or the other things people in turtlenecks use to decide what Android can and can't do very well. Below is the applicable Makefile for WebKit:

```make
# Two ways to control which JS engine is used:

# 1\. use JS_ENGINE environment variable, value can be either 'jsc' or 'v8'

# This is the preferred way.

# 2\. if JS_ENGINE is not set, or is not 'jsc' or 'v8', this makefile picks

# up a default engine to build.

# To help setup buildbot, a new environment variable, USE_ALT_JS_ENGINE,

# can be set to true, so that two builds can be different but without

# specifying which JS engine to use.

# To enable JIT in Android's JSC, please set ENABLE_JSC_JIT environment

# variable to true.

# Read JS_ENGINE environment variable

JAVASCRIPT_ENGINE = $(JS_ENGINE)

# The default / alternative engine depends on the device class.

# On devices with a lot of memory (e.g. Passion/Sholes), the

# default is V8\. On everything else, the only choice is JSC.

# TODO: use ARCH_ARM_HAVE_ARMV7 once that variable is added to

# the build system.

ifeq ($(ARCH_ARM_HAVE_VFP),true)

    DEFAULT_ENGINE = v8

    ALT_ENGINE = jsc

else

    DEFAULT_ENGINE = jsc

    ALT_ENGINE = jsc

endif

ifneq ($(JAVASCRIPT_ENGINE),jsc)

ifneq ($(JAVASCRIPT_ENGINE),v8)

    # No JS engine is specified, pickup the one we want as default.

    ifeq ($(USE_ALT_JS_ENGINE),true)

      JAVASCRIPT_ENGINE = $(ALT_ENGINE)

    else

      JAVASCRIPT_ENGINE = $(DEFAULT_ENGINE)

    endif

endif

endif

```

So, if you're running a low-end Android device, like a Motorola Quench, your Javascript Engine will be different from the Nexus S, HTC EVO with CM7, the Motorola Droid, the Nexus One, etc. Since nobody has seen the official Android 2.3 on anything other than the Nexus S, I can only really do experiments with Cyanogen on an HTC Dream, which isn't really accurate.

Recently, there was an issue with the emulator image on Android 2.3 that directly affected PhoneGap. Because I have no idea what Javascript Engine is on the emulators, I suspect that this image may creep up again on low-end phones and cause even more fragmentation than before. This is a REALLY bad thing, since it makes web development on Android even more frustrating, and will chase developers away from that platform. Like everything else in Android, things are always changing, so if any phone manufacturers are reading this and can test PhoneGap on their low-end line and get back to me, that would be greatly appreciated.

[› Visit the original post](http://blogs.nitobi.com/joe/2011/01/14/android-your-js-engine-is-not-always-v8/)

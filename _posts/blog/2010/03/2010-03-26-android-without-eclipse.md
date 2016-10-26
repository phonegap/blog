---
title: Android without Eclipse
date: 2010-03-26 23:32:23 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2010/03/26/android-without-eclips/
status: publish
type: post
format: html
---

Now, for people who are Java developers, I can understand the attachment to Eclipse, but for the rest of us, Eclipse is a giant piece of bloatwear that gets in the way of the code and what we want to do with that code. However, it's a fact of life for Android developers, or is it?

Building and running Android Applications:

Now, the first command that we deal with is the android command, which can generate a project. In typical java fashion, it takes a crap ton of flags, but you can create a project by typing this:

```sh
android create project -t 7 -k package name - a name -n name
```

This will create an android project. Now, on Android, the DroidGap script actually uses the Android script to create a project. So, once you have your project, what do you do with it? Well, the first thing to do is to build it, which you can do with ant. When you type ant on an Android project, you'll get a list of commands like this:

```sh
    help:
         [echo] Android Ant Build. Available targets:
         [echo]    help:      Displays this help.
         [echo]    clean:     Removes output files created by other targets.
         [echo]    compile:   Compiles project\'s .java files into .class files.
         [echo]    debug:     Builds the application and signs it with a debug key.
         [echo]    release:   Builds the application. The generated apk file must be
         [echo]               signed before it is published.
         [echo]    install:   Installs/reinstalls the debug package onto a running
         [echo]               emulator or device.
         [echo]               If the application was previously installed, the
         [echo]               signatures must match.
         [echo]    uninstall: Uninstalls the application from a running emulator or
         [echo]               device.
```

I think this is pretty self-explanatory, BUT there needs to be something said for the difference between debug versions and release versions of the same piece of software. Most of the time, you'll want to sign the apks with a debug key, so that these are specific to your workstation. However, when releasing a project, you will want to sign it with a key in the keystore. _(It's important to take care of your keystore and not to do what I did and forget about it. This is why I haven't gotten a free Nexus One from Google for the PhoneGap Demo Application.)_

Of course, this only works either for one phone, or one emulator. What if you have multiple emulators? No problem, use adb. The Android Debug Bridge is one of the most handy tools in the Android Developers toolkit, and is extremely handy for debugging. To see what devices you have, run adb devices like this:

```sh
bowserj@shapley:~/Orbot$ adb devices
List of devices attached
0123456789012 device
```

To install an APK onto a device, type the following:

```sh
apk -s 0123456789012 install phonegap.apk
```

## Debugging Javascript and Java on the Android WITHOUT ECLIPSE

Now, here's where things get interesting. When you need to debug javascript in the latest version of PhoneGap, you can use logcat to do so, all you need to do is run adb logcat, like this:

```sh
adb logcat
```

Of course, to actually use a Java Debugger, such as jdb, you need to attach it to a process on the device. ADB has you covered as well, all you need to do is this:

```sh
adb jdwp
```

Then once you have the PID that you want, do this:

```sh
adb forward tcp:8000 jdwp:
jdb -attach localhost:8000
```

Then you're in! Make sure that you don't have another process (i.e. Eclipse) running that connects to this, and you should be able to debug your Java code just like how you would debug Java code normally. I admit that I'm not a jdb/gdb ninja and things like DDD have made me dumb. Therefore, I'd appreciate any book recommendations on how to use JDB/GDB for debugging.

[› Visit the original post](http://blogs.nitobi.com/joe/2010/03/26/android-without-eclips/)

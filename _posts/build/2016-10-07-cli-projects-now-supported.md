---
title: PhoneGap Build Now Accepts CLI Projects
date: 2016-10-07 10:00:00 Z
categories:
- build
tags:
- PhoneGap Build
author: Brett Rudd
---

PhoneGap Build started with "Initial Commit" in August 2010. It is now October 2016 and we just committed "fixed typo".  A lot has changed in those years, including a fixed typo. But more importantly, during this time Cordova and PhoneGap Build have diverged in how projects have been structured, and we are now closing that (ahem) gap.

PhoneGap Build has always had the requirement that the `index.html` and optional `config.xml` be in the same directory at the root of your app.  Meanwhile Apache Cordova has matured and evolved their project structure to what most of you are familiar with:

![](/blog/uploads/build/cli_project.png)

Although not 100% compatibile with the Cordova project functionality we are now accepting apps with this structure.  We are not deprecating or removing support for how projects were working in the past. Additionally there is no extra configuration for you to add to use this new format.

The main difference with the legacy structure we have required in the past is that the required `config.xml` is in the root of the project, while `index.html` and other html and javascript assets are in a directory named `www`.

We are also suppoorting the `merges` directory that enables you to include platform specific assets in your project.  During build the merges directory for each platform will be copied over your `www` directory.  Typically this is used for platform specific styelsheets, javascript files or images.

You can include other directories in your project and they can be referenced in config.xml for splashes and icons and there is no need to use .pgbomit to have those directories removed from the built app.

There are a few caveats to our support:

- the `platforms` and `plugins` directories are ignored and are not included when building an app. So any assets included in these directories wont be accessible to your application
- splashscreens and icons should be specified relative to the config.xml
- content src is not supported and is always `index.html` (for now!)
- `hooks` sadly are still unavailable (for now!)

For more information read the [documentation](http://docs.phonegap.com/phonegap-build/getting-started/app-project-structure/).

As usual, if you have questions or issues, [don't hesitate to let us know](https://forums.adobe.com/community/phonegap/build), talk to us on twitter at @phonegapbuild or yell at me at @brettrudd

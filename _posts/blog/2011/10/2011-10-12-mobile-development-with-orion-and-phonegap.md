---
title: Mobile Development with Orion and PhoneGap
date: 2011-10-12 00:20:19 Z
categories:
- app
tags:
- App
- PhoneGap Build
author: Colene Chow
status: publish
type: post
format: html
---

What would it take to build a complete mobile tool chain in the browser? The question is quite relevant for today's mobile developers, who currently have to download large SDK's to develop and build their mobile applications (and buy a Mac if you want to develop for iOS). If you want to target several mobile platforms, and maybe even some future mobile-friendly desktop platforms, you're going to have to download, learn, and maintain quite a few of these SDK's.

Not only that, but many developer workflows are quite suited to running directly on a mobile or tablet device. Imagine for example testing your mobile application on a device, and being able to quickly switch back to your development tools to tweak styling or layout, enter bugs, kick off new builds, etc.

The short answer is that we're not there yet, but the future is closer than you think. The [PhoneGap Build](https://build.phonegap.com/) service, which recently went into [open beta](http://www.phonegap.com/2011/09/30/phonegap-build-moves-to-open-beta/), provides a solution for assembling and packaging mobile applications remotely from your browser. The recently created [Orion](http://eclipse.org/orion) project is one of many efforts to bring development tools to the browser. By combining the currently available Orion tools with PhoneGap Build, we can already create and build a complete mobile app from your browser:

1. [Fork](https://github.com/phonegap/phonegap-start/fork) the sample web application on [GitHub](https://github.com/phonegap/phonegap-start).

  [![](/uploads/2011/10/ph-fork.png)](/uploads/2011/10/ph-fork.png)

1. In [OrionHub](http://orionhub.org/), clone the Git repository into your Orion workspace. Complete instructions on cloning can be found [here](http://wiki.eclipse.org/Orion/How_Tos/Cloning_repository_from_github).

  [![](/uploads/2011/10/ph-edit1.png)](/uploads/2011/10/ph-edit1.png)

1. In the Orion Navigator, find and edit your application config.xml file. For example, change the application name and description.
1. Open the Orion Git Status page from either the Repositories page or the Navigator menu. Commit and push your changes.

  [![](/uploads/2011/10/ph-push.png)](/uploads/2011/10/ph-push.png)

1. In [PhoneGap Build](https://build.phonegap.com/), supply the URL of your Git repository.

  [![](/uploads/2011/10/pg-build.png)](/uploads/2011/10/pg-build.png)

1. Once the PhoneGap worker drones are finished, you will have a list of compiled native applications ready for download.

  [![](/uploads/2011/10/ph-download.png)](/uploads/2011/10/ph-download.png)

This is where the current browser-based mobile tools story comes to an end. In theory you can now submit your built application to the various mobile app stores [directly from Phone Gap](http://www.phonegap.com/app-submission/). In practice, you're going to want to test and iterate your application using a [mobile emulator](http://speckyboy.com/2010/04/12/mobile-web-and-app-development-testing-and-emulation-tools) before unleashing it to the world. There is obviously an opportunity here for someone to develop a web-based test and emulation platform for mobile to fill in this gap.

Aside: Before embarking on this investigation, I started downloading the [Android SDK](http://developer.android.com/sdk/index.html). This admittedly trivial mobile application was started, developed, built, and a blog post written while the SDK was still downloading. By the time the blog post was published, the download was sitting at 73% done and had a 1.5GB disk footprint. That's the SDK for only one mobile platform. Clearly the current Android SDK tools are far superior to anything available in a browser today, but it gives you a glimmer of what the future may bring.

> John Arthorne has worked on the [Eclipse](http://wiki.eclipse.org/Eclipse) and [Equinox](http://wiki.eclipse.org/Equinox) projects for the past decade in many different areas. He was the main developer on the resource model for many years, and designed the platform's concurrency infrastructure. In recent years he has focused on the [Orion](http://wiki.eclipse.org/Orion) server, provisioning ([p2](http://wiki.eclipse.org/P2)), [e4](http://wiki.eclipse.org/E4), and overall platform [API quality](http://wiki.eclipse.org/API_Central). John is a member of the Eclipse [Architecture Council](http://wiki.eclipse.org/Architecture_Council), [Planning Council](http://wiki.eclipse.org/Planning_Council) and [Eclipse Project PMC](http://wiki.eclipse.org/Eclipse/PMC), and is a Senior Software Developer at IBM Canada.

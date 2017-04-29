---
title: 'PhoneGap Android: Creating projects and filing bugs'
date: 2010-01-06 18:35:10 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2010/01/06/phonegap-android-creating-projects-and-filing-bugs/
status: publish
type: post
format: html
---

So, apparently I forgot to mention the build.rb script I wrote last year. It's checked into the phonegap-android repository, and you can pull it. To use it, you just have to do the following:

1. First, build a PhoneGap.jar (this should be built before being distributed in future releases)

  `ant jar`

1. Run build.rb with the various attributes:**

  `ruby build.rb TestApp com.testapp www /foo/bar`

1. Profit.

You should have a test application created. The application name should have no spaces, and it's expected that you know enough about Android development to change the res/values/strings.xml file to what you want it to be (you don't need to know much). The www directory should have an icon.png in it for the icon that you want to use with your application. It's an early script, and it's an intermediary step that's designed to make life easier for those who don't want to bother with Eclipse.

Also, many people go here to post bugs. While I appreciate all the comments I get on Android, it works better if the bugs are also filed in the [PhoneGap bug tracker](https://phonegap.lighthouseapp.com). That way I can keep track of what's broken. It's also the place to put feature requests, since like the Android developers themselves, I will often not reply to the forums because I'll be too busy with other tasks. I hope to have a plugins project added here soon.

[› Visit the original post](http://blogs.nitobi.com/joe/2010/01/06/phonegap-android-creating-projects-and-filing-bugs/)

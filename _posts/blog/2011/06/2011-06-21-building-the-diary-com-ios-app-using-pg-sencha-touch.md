---
title: Building the Diary.com iOS App using PG & Sencha Touch
date: 2011-06-21 01:27:30 Z
categories:
- app
author: admin
status: publish
type: post
format: html
---

We have recently got our app, [Diary Mobile](http://itunes.apple.com/gb/app/diary-mobile/id357481953?mt=8), approved by Apple. It was under review for 6 days and it took one more day until we were in the App Store. We actually used PhoneGap to replace a previously built native app developed by a third party and decided to bring development in house for agility.

We wanted to share and give confidence that PhoneGap apps are getting approved by Apple. We were pretty anxious. Some points I am sure you will all ask is what we used and how it was. The app was built with PhoneGap 0.9.2 and Sencha Touch 1.0.1a, it uses Flurry for analytics via a PhoneGap plugin. We've upgraded both PhoneGap and Sencha Touch to the latest and greatest for a future release, currently on a development branch.

## Some points of interest...

* We built a Flurry API PhoneGap plugin for iOS (to be released open source in the near future). It goes to show that PhoneGap makes it very easy for us to extend the code if something is missing. Especially if the Objective-C only native option is open source. Even if you have no knowledge of Objective-C, there are plenty of examples of PhoneGap plugins over at [PhoneGap's Github page](https://github.com/phonegap/phonegap-plugins) to get you started.
* We also built another PhoneGap plugin to use the Local Notifications on iOS (also to be open sourced soon).
* We are looking at using the core codebase to create an Android version for the next release, then Blackberry.
* Performance was the biggest challenge, Sencha Touch is quite a beast and we've had to patch quite a lot of it to make it more performant and apply bug fixes.
* The app uses a lot of Ajax calls and stores everything in HTML5 Local Storage.
* We built an entirely REST API for which the app communicates with to make it as efficient and fast as possible.

When we were first building this App, we were always looking for affirmation of what to build it with (rejection worries,etc). So we hope this post helps relieving some of those worries and prove a combination of a Javascript Framework with PhoneGap works well.

We have to say it wasn't easy, performance was tricky at times. Here are some tips...

* Initialize variables outside of FOR loops.
* For Sencha Touch, actually look at the source code, it's a lot more readable than it seems.
* Cache using Global variables.
* Keep Ajax calls efficient and minimize starting of asynchronous calls all at once by making them to be action based. Similar to techniques when caching a normal website.
* It's javascript, you will need to get your hands dirty using hacks with setTimeout() once in a while.

The App is free but needs you to sign up as it compliments our web application at [Diary.com](http://diary.com). You can download the app at [http://itunes.apple.com/gb/app/diary-mobile/id357481953?mt=8](http://itunes.apple.com/gb/app/diary-mobile/id357481953?mt=8)

We hope to share more of our journey and battles as our app grows. Good luck with your PhoneGap development!

Kenneth Lee
(CTO at Diary.com)

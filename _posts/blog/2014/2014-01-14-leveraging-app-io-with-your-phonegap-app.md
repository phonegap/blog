---
title: Leveraging App.io with your PhoneGap App
date: 2014-01-14 11:00:04 Z
tags:
- Guest Post
author: David Truong
format: html
---

Ever wanted to quickly test your PhoneGap app in an iPhone, without actually having an iPhone? App.io is a relatively new service that allows you to run your native iOS app in any browser, on any device, without the need for complicated provisioning or plugins. This means that you are now able to run and test the app you built with PhoneGap, directly in the browser!

Here’s an example of [Infogems.net’s](http://www.infogems.net) app they build in PhoneGap, running in the browser:
Link: [https://app.io/LutPah](https://app.io/LutPah)

The process is incredibly easy as App.io only requires the simulator build of your app. To create the simulator build of your app, [follow these instructions](http://docs.phonegap.com/en/3.3.0/guide_platforms_ios_index.md.html#iOS%20Platform%20Guide_open_a_project_in_the_sdk) to open your app in Xcode:

Once you’ve deployed to the simulator, simply navigate to

```sh
~/Library/Developer/Xcode/DerivedData/<b>YourAppName</b>/Build/Products/Debug-iphonesimulator/
```

Zip the .app file found in the directory, and upload it to your [FREE App.io account](https://app.io/signup?ref=phonegap).

> Guest blog post by David Truong
> David Truong is Head of Business Development at App.io, where he spends time hustling to spread the word about App.io and posts GIFs in the company chat.

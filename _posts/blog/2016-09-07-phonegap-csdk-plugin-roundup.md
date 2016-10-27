---
title: Adobe Creative SDK Plugin Roundup
date: 2016-09-07 00:00:00 Z
tags:
- PhoneGap Blog
- Release
- News
- Plugin
- Announcement
author: Jen Gray
---

We're so excited to announce a slew of plugins that enable developers to take advantage of the Creative SDK native components for iOS and Android without writing a single line of Objective-C, Swift, or Java.

Let's talk about each and give you a look at all the great templates to help you get started.

## About the Adobe Creative Cloud SDK

The Adobe Creative Cloud provides the world’s best creative tools and content. Now, with the [Creative SDK](https://creativesdk.adobe.com/), you can access a number of UI components and headless APIs to give your users these creative tools and connect them to the Creative Cloud platform right within your mobile or web app. It’s the engine behind some of the best creative apps on the market and at the heart of Adobe’s own mobile offerings.

## About the plugins

Imagine being able to take a photo within your app, edit the photo and then send the photo directly to Photoshop on the desktop! Now you can! And it'll feel seamless to your users.

### Client Auth plugin

The [Client Auth plugin](https://github.com/CreativeSDK/phonegap-plugin-csdk-client-auth) is your first stop on the way to integrating the Adobe Creative SDK into your PhoneGap app. Client Auth is required for all Creative SDK integrations.

[Register your application](https://creativesdk.adobe.com/docs/ios/#/articles/gettingstarted/index.html#register_application)

### Image Editor plugin and template

The [Image Editor plugin](https://github.com/CreativeSDK/phonegap-plugin-csdk-image-editor) provides a solution for developers seeking to add powerful photo editing to their Android, iOS and Web apps. The Image Editor includes over twenty advanced imaging tools covering everything from Effects and Crop to Redeye and Blemish.

As a companion to the Image Editor plugin, the Creative SDK team has released a PhoneGap template so you can get started right away.

These templates are essentially sample apps that you can download via NPM, build from your command line, and run on your device (these plugins support iOS and Android).

When you try out the Creative SDK Image Editor PhoneGap template, without writing any code, you’ll have a sample app for your reference that looks like this:

![](/blog/uploads/2016-08/creative-sdk-phonegap-template-image-editor.png)

The buttons let you use the Creative SDK Image Editor to edit the photos on the screen or use camera to take a new photo for editing.

You can get started with the Creative SDK Image Editor template for PhoneGap by checking out [the repo on GitHub](https://github.com/CreativeSDK/phonegap-template-csdk-image-editor).

The README covers everything you need to get going, including prerequisites, setup steps, and files to check for sample code.

### Send to Desktop API plugin and template

The [Send to Desktop API plugin](https://github.com/CreativeSDK/phonegap-plugin-csdk-send-to-desktop) provides a simple way for your mobile users to send their work from your app directly to Adobe desktop apps. You can specify which application the shared data will open in: PHotoshop, Illustrator and InDesign.

The team just released this template to get started. Again, without writing any code, you'll have a sample app for your reference that looks like this:

![](/blog/uploads/2016-08/csdk-phonegap-send-to-desktop.png)

In the template app, you can:

- Log in and out with your Adobe ID ([User Auth UI plugin](https://github.com/CreativeSDK/phonegap-plugin-csdk-user-auth))
- Take a photo ([Cordova Camera plugin](https://github.com/apache/cordova-plugin-camera))
- Edit the photo ([Image Editor UI plugin](https://github.com/CreativeSDK/phonegap-plugin-csdk-image-editor))
- Send the photo to Photoshop on the desktop ([Send To Desktop API](https://github.com/CreativeSDK/phonegap-plugin-csdk-send-to-desktop))

### User Auth UI plugin

The [User Auth UI plugin](https://github.com/CreativeSDK/phonegap-plugin-csdk-user-auth) provides a solution for developers seeking to allow their users to login to the Adobe Creative Cloud.

## Get involved

Read more about the releases over on the [Creative SDK Blog](https://blog.creativesdk.com/2016/08/phonegap-plugins-for-the-creative-sdk/). And if there's another Creative SDK PhoneGap plugin you'd like to see, leave a comment!

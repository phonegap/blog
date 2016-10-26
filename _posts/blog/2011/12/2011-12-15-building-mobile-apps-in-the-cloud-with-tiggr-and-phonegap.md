---
title: Building Mobile Apps in the Cloud with Tiggr and PhoneGap
date: 2011-12-15 00:57:37 Z
categories:
- app
tags:
- Guest Post
- App
- iOS
author: Colene Chow
status: publish
type: post
format: html
---

> Guest blog post by Max Katz

## Tiggr - the easiest platform for building mobile apps in the cloud

[Tiggr](http://gotiggr.com) is a cloud-based mobile apps builder. It lets developers build HTML5/JavaScript and native apps very quickly, entirely in the cloud. There is nothing to download, nothing to install, and nothing to configure. Just create a new project, and you are ready to start building your mobile app with HTML5/JavaScript and PhoneGap.

## Building mobile UI with jQuery Mobile

To build the mobile UI, there is a visual editor and [jQuery Mobile](http://jquerymobile.com) components, as shown below. You simply drag and drop components into the phone area.

![](/assets/tiggr2/pg_visualeditor.png)

You can create multiple screens, navigate between screens, store data in Local Storage, and write custom JavaScript. This means you can create the complete UI for your mobile app and also test in a Web browser.

## Testing the mobile app

Testing is one of the most innovative features in Tiggr. There is a big Test button at the top. Clicking that button opens up a browser window with the mobile app in it. Need to test the app on the actual device? Scan the QR code, and e-mail the URL to your device. Don’t forget to make the app public. (More about testing native apps a little bit later.)

![](/assets/tiggr2/pg_test.png)

## Consuming any cloud service

Once the UI is ready, the next step is connecting to cloud services. In Tiggr, you can connect to any cloud REST service. Below is an example of using the service editor to define a connection to Twitter’s search REST service:

![](/assets/tiggr2/pg_restservice_url.png)

Once the service is defined, it is mapped to the UI. A service usually has inputs and outputs. Mapping specifies how different UI components are related to different service parameters for input and output. There is even a visual data mapping editor available (service output is shown on the left, screen components are shown on the right:

![](/assets/tiggr2/pg_mapping.png)

The JavaScript column (on the left) allows you to write custom JavaScript to give you more power and flexibility when mapping service to UI (custom JavaScript is also available when mapping UI to service).

One last step is adding an event to invoke the service. For example, on a specific button click (HTML click event) the service could be invoked. You can of course use any other HTML events. With Tiggr this is easy.

**Native apps with PhoneGap** PhoneGap is an awesome mobile app platform. It takes advantage of Web technologies developers already know: HTML and JavaScript. PhoneGap makes it super easy to wrap any mobile Web app as native, but also provide access to device native features via its elegant and easy-to-use [API](http://docs.phonegap.com/en/1.2.0/index.html).

**Exporting native app** Every app (native) in Tiggr comes with PhoneGap installed. To export the app as native is as simple as clicking the big Export button:

![](/assets/tiggr2/pg_export.png)

If you are targeting for Android, then you can download Android Release binary (.apk). This file is ready for the Android Market. Tiggr has a Android .apk file editor for you to enter all the necessary information.

If you are targeting iOS, then export iOS xCode project (Eclipse). You can then build the app on your machine or use cloud-based [PhoneGap Build](http://build.phonegap.com) service to build for iOS.

As an alternative, for both Android, iOS or any other platform you can download the mobile Web version (Web resources, HTML/CSS/JS) and use PhoneGap Build service to build for the platform.

For example, if you need to build for BlackBerry, then simply download the mobile Web version and upload to PhoneGap Build. It’s that simple.

## Using PhoneGap API

What if you need to invoke PhoneGap API to access device features? Well, that’s very simple too. Tiggr comes with Run Custom JavaScript action, which can be invoked on any HTML event.

As an example, we will implement a Vibrate button.

![](/assets/tiggr2/pg_app_buttons.png)

First, we add the click HTML event to the button: ![](/assets/tiggr2/pg_clickevent.png)

Add an action - Run Custom JavaScript: ![](/assets/tiggr2/pg_runcustomjs.png)

and finally add the PhoneGap JavaScript call: ![](/assets/tiggr2/pg_runcustomjs_editor.png)

Another option is to create a JavaScript file (Project > JavaScript), write all the custom code in functions in the file, and then invoke any function via the Run Custom JavaScript action. ![](/assets/tiggr2/pg_createjs.png)

Note that you can also import an existing JavaScript file (from a URL or via uploading). ![](/assets/tiggr2/pg_js_file.png)

Invoking a function from the custom JavaScript file is done via Run Custom JavaScript action: ![](/assets/tiggr2/pg_runcustomjs_location.png)

**Testing native apps** Once you use a native API, testing in Web browser is no longer as useful. To test native apps, you can use Tiggr Mobile Tester. It’s a native app ([Android](https://market.android.com/details?id=com.exadel.tiggr.projectlist.), [iOS](http://exadel.org/tiggrmobiletester)) that lists all your mobile app in Tiggr. You simply tap any app in the list to launch the native app for testing. It’s the easiest and fasted way to test a native app without having to install it. The tester app looks like this: ![](/assets/tiggr2/pg_tiggrmobiletester_1.png)

## Device components

Being able to invoke custom JavaScript (and PhoneGap API) almost from anywhere makes Tiggr and PhoneGap so powerful. But, that’s not all. Tiggr now has components in the Device palette which are based on PhoneGap API: ![](/assets/tiggr2/pg_device.png)

This is even simpler than using the API. More components are planned to be added such as Camera and others.

## Tiggr and PhoneGap - The ULTIMATE mobile app development combo?

We think so.

You have Tiggr, a cloud-based mobile apps builder. There is nothing to install or configure. Tiggr uses jQuery Mobile, HTML5, JavaScript and CSS to build mobile apps. The app's UI is built inside a visual editor, the app can easily be connected to any cloud service, and the app can be tested at any point in a browser or on a device. At the end, you can export the app source.

Then, you have PhoneGap, a powerful framework that uses HTML5 and JavaScript to build native mobile apps and makes it super easy to access native features in an app, such as contacts and camera. PhoneGap’s cloud-based build service allows you to build quickly for multiple platforms.

When you combine the two, Tiggr and PhoneGap, you get powerful cloud-based HTML5 mobile apps builder with an easy way to incorporate native device features and build for multiple mobile platforms.

Sign up for [Tiggr](http://gotiggr.com) and build your mobile app today.

> Max Katz is Head of Developer Relations for Tiggr at Exadel. You can find his writings about Web and mobile technologies on his [blog](http://mkblog.exadel.com), and follow him Twitter at [@maxkatz](http://twitter.com/maxkatz). He also runs the [Tiggr blog](http://blog.gotiggr.com). Lastly, you can always email him at [max@exadel.com](mailto:max@exadel.com).

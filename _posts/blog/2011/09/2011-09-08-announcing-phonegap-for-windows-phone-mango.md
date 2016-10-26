---
title: Announcing PhoneGap for Windows Phone Mango
date: 2011-09-08 09:42:55 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2011/09/08/pg-wp7mango/
status: publish
type: post
format: html
---

Over the last month and a bit, Nitobi has been working closely with Microsoft to bring PhoneGap to WP7 devices. I am happy to say that it's now here, and ready for beta exposure.

## The Genesis of PhoneGap for Windows Phone 7

Our starting point was the excellent work of Matt Lacey, who created the initial project and did the initial exploration of device functionality. The upcoming Windows Phone Mango update to devices brings a rich set of HTML5 features and IE9 to the device.

Thanks to Microsoft sponsorship, Sergei Grebnov has been making contributions to the code and has implemented the MediaCapture and Camera APIs. This is Sergei's first foray into PhoneGap, but he has proven to be a valuable asset to the project and was up to speed quickly.

Nitobi has dedicated two developers to the project, myself and Herm Wong. We've been busy dusting off our Sliverlight+C# skills and implementing the other APIs.  ( the infamous Shazron has also jumped in just this week )_ _

Here's the outcome!

Some code  here : [https://github.com/phonegap/phonegap-wp7](https://github.com/phonegap/phonegap-wp7)

[](https://github.com/phonegap/phonegap-wp7)Some more info here: [http://bit.ly/PhoneGapMangoIntro](http://bit.ly/PhoneGapMangoIntro)

## What You'll Need to Get Started

So you want to get on it, enough talk? You will need Visual Studio 2010 with the "[WP7 SDK](http://create.msdn.com/en-us/home/getting_started)" installed (the free express version works fine)

Detailed instructions will be posted shortly as a getting started guide on PhoneGap.com, in the meantime :

* fork/git or download/unzip the repo to your harddrive
* copy the file GapAppStarter.zip to the folder : My DocumentsVisual Studio 2010TemplatesProjectTemplates
* Launch Visual Studio 2010 and select to create a new project_ ( PhoneGapAppStarter should be listed as an option, give it a name )_
* Right-Click on the solution and select Add->Existing Project, and add the project :  frameworkWP7GapClassLib.csproj from the downloaded repo
* Right-Click your main project and "Add Reference" to the WP7GapClassLib project
* build and run!

## Where Are We ? What APIs Are Done?

Here's an overview of where we're at:

* Accelerometer
* Camera
* Compass (unit testing is waiting on us having a device that supports compass)
* Contacts
* Events (partial, still underway)
* GeoLocation
* MediaCapture
* Connection
* Notification

These have all been implemented per the spec, and function as expected with some quirks being added to the documentation as you read this.

The `deviceready` event is fired on startup, and like other device platforms, is the signal that you can begin making PhoneGap API calls.

The GeoLocation API did not require any work, as IE9 implements the spec as defined by W3C.

Still to come :

* File
* Storage

## How Does it Work? _A peek under the hood._

PhoneGap-WP7 includes a library project which contains the core functionality, and you reference this project from your own project. Your own project will include the www folder which is where your Gap html/js/css will live. All files in the www folder must be added to the project in Visual Studio and marked as content so they will be packaged with your app when it runs on the phone. We will be releasing a Visual Studio template to allow you to simple select NewProject->PhoneGap-WP7 project and auto-magically be on your way.

Packaging of applications is quite different on WP7\. All resources (your PhoneGap js/html/css code in the www folder) are packaged into the XAP as resources but cannot be accessed directly at runtime, so an extra unpackaging step is required.

When the app is first run, all resources listed in the manifest are copied from the binary XAP to IsolatedStorage. IsolatedStorage is a per application File location, similar to a per app Documents folder in iOS. IsolatedStorage is managed per app, so separate applications cannot interact with the same document store. We are working to make this as transparent as possible, so your workflow does not have to change. Build scripts and tooling will eventually take care of the dirty work, but for now you will be building directly from Visual Studio.

After unpackaging the contents of the www folder, your www/index.html file is loaded into an embedded headless browser control. This is essentially the same paradigm as other platforms, except here it is an IE9 browser and not a webkit variant. IE9 is a much more standards-compliant browser than previous IEs, and implements commonly used html5 features like DOMContentLoaded events, addEventListener interfaces, and CSS3\. Be sure to use to get the html5 implementation otherwise the browser may fallback to a compatibility mode, and your code will likely choke and die. You should also use in your html .

## Gotchas + Known Issues

IE9 does not expose touch events, or even mouse events to JavaScript. The only UI event that is available to your code is the click event. This means that many interfaces that are based on scrolling libraries and a WebKit DOM will not function as expected. The browser control DOES appear to support the CSS value of overflow:scroll, however there is no momentum and the scrolling feels sticky. I have done some quick exploration into exposing mouse events to JavaScript via the container and they do look promising. I will be moving on to this after I completed the Events API so your code can override the back-button and search-button.

IE9 supports localStorage, and sessionStorage, however they are not available to pages that are loaded without a domain. We will be investigating implementing this API ourselves, and managing the storage in IsolatedStorage.

## Reporting issues, tracking progress and keeping up to date.

The project code is maintained on [github](https://github.com/phonegap/phonegap-wp7), so you can follow it there. Any issues you come across can be filed in the Issue Tracker on github.

As with the other devices, general question can be directed to the PhoneGap mailing list, where the community is ready and waiting to help. For questions specific to Windows Phone 7, please include 'WP7′ in the subject.

## Will PhoneGap for WP7 support plugins?

This was a key focus, as keeping the architecture plug-able is a primary concern, and in my view, where the real power lies.

PhoneGap-WP7 maintains the plugability of other platforms via a command pattern, to allow developers to add functionality with minimal fuss, simply define your C# class in the WP7GapClassLib.PhoneGap.Commands namespace and derive your class from BaseCommand.

PhoneGap exec works in exactly the same way as other platforms :

```js
PhoneGap.exec(callbackSuccessFunction,callbackErrorFunction, PLUGINNAME, PLUGINMETHODNAME, paramObj);
```

## What is Left to Do? How can You Contribute?

Sergei has begun working on the File API, so you can expect full file access to create, modify, delete files as well as upload/download to/from a server.

I am busily trying to wrap up some of the life-cycle events (Events API) so your application can be notified when the app is pushed to the background. I will be looking into exposing mouse events to JavaScript shortly after that.

If you have expertise in any of the Native portions, or JavaScript, you are welcome to fork the repo on github.

Keep in mind: PhoneGap can only accept pull requests from contributors who have signed the CLA so we can make sure that PhoneGap remains open source and free. PhoneGap is dual licensed as [defined here](http://www.phonegap.com/about/license).

Even if you don't contribute code back, I/we would love to hear about your experience building with PhoneGap for WP7, good, bad or indifferent. Please direct your kudos, or comments to the [Facebook page](http://www.facebook.com/PhoneGap). You are also welcome to contribute to the documentation, and wiki pages, got a great getting started tutorial? Let us know! Want to tell the world about your WP7 PhoneGap app? Let us know!

We will be posting new information to the blog as updates are made, as well as on the mailing list, and PhoneGap.com.

Forever Endeavor,
-jm

[› Visit the original post](http://blogs.nitobi.com/jesse/2011/09/08/pg-wp7mango/)

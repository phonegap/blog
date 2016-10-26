---
title: Converting an iPhone PhoneGap app to a Palm PhoneGap app in 10 minutes
date: 2010-05-31 19:51:40 Z
categories:
- app
author: Steve Gill
link: http://blogs.nitobi.com/steve/?p=23
status: publish
type: post
format: html
---

Last week I heard about Palm's new hot app promotion. It is pretty much an incentive to developers to make palm apps, have them get ranked and get some easy money (find details [here](http://palmhotapps.com/)). I realized that a lot of PhoneGap developers seem to just develop for the iPhone and android and I wanted show how easy it is to convert that iPhone PhoneGap app to a palm PhoneGap app.

The app which I am converting is called Snow Reports. You can download the source from my github at [http://github.com/stevengill/SnowReports](http://github.com/stevengill/SnowReports). You will see that I already have a working version of the app for iPhone, android, and palm. I have made three screen casts walking through converting the iPhone version to the Palm version.

## Screen Cast!

## Set Up

Once you have followed the getting started guide for palm on the [phonegap wiki](http://wiki.phonegap.com/Getting-Started-with-PhoneGap-Palm), you should have your system setup and ready to make the palm version of this app. Make sure you download the latest version of phonegap-palm from github [here.](http://github.com/phonegap/phonegap-palm) We want to copy over the contents from the www folder in the iphone repository into the phonegap-palm/framework/www folder.

## Changes I Made

There were very few changes I had to make to get this working perfectly on the palm emulator. The ultimate goal of PhoneGap is to have the user never need to make changes to the source but the PhoneGap team hasn't started focusing on rendering issues yet so until then we will have to make a few css tweaks.

For index.html, first thing that all Palm applications need is the mojo library.

```html
<script src="/usr/palm/frameworks/mojo/mojo.js" type="text/javascript" x-mojo-version="1" ></script>
```

You will also notice that in the meta viewport tag that height is set to 460px. This is set for the iPhone and takes into account header in the webview. With palm we can have varying heights of devices so I usually set this to device-height.

```html
<meta name = "viewport" content = "width = device-width, height = device-height">
```

For snowreport.css, some of the styles that looked good on the iPhone will not render over so good on the Palm emulator. Here are a the two styles I changed to make it look pretty:

```css
.header div, .footer div {
  height: 34px;
  padding-top: 8px;
  background-repeat: repeat-x;
  float: left;

}
.footer .mid-blue, .footer .mid-black {
  padding: 8px 9px 0px;
}
```

### Some Cleaning Up

There are a few things left over to do before I can call this app complete:

* I want to copy Icon.png from the iphone/SnowReports to phonegap-palm/framework/www directory.

* Then I want to change the id of my app. Open up appinfo.json file located in phonegap-palm/framework/www and edit the id. In my screencast I chose com.palm.snowreports. In reality you probably want to name this something different. If you leave it as com.palm.* it might not get accepted by the palm store due to them thinking you are trying trick the store into saying that palm made the app. The reason why it is set to that by default is because there is a bug in webOS that requires you to have com.palm if you want vibration in your apps. Palm is currently looking into this and will hopefully release a fix soon. Your best bet as a developer is not to include vibration for the moment and change this id to something unique.

After you have changed the Id and have the emulator running, in the terminal you will need to do a make, palm-install com.palm.snowreports, and palm-launch com.palm.snowreports.

There you have it. That's how simple it is to convert your iPhone PhoneGap app to a Palm PhoneGap app and ready to submit to the Palm webOS app store. Get to it developers!

[› Visit the original post](http://blogs.nitobi.com/steve/?p=23)

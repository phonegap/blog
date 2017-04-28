---
title: CraftyJS on Android Device Using PhoneGap
date: 2011-07-19 21:11:14 Z
categories:
- app
author: Tim Kim
status: publish
type: post
format: html
---

## Introduction

Howdy,

Today I’m going to be blogging about how to get starmelt’s CraftyJs game built in PhoneGap and deployed on an Android device. At the end of this article you should know how to fill the device’s screen with your game view and the few tweaks to disable the webkit highlight event.

I’ll be using the build.phonegap.com service to build my app as well as the Android sdk tools to install onto device. Both are easy to sign up for/download so that’ll take you about a half hour to get everything ready.

## Step One: Get the craftyjstut from github

The first step is grab the repo for starmelt’s tutorial game which is located here: [https://github.com/starmelt/craftyjstut](https://github.com/starmelt/craftyjstut)

Once you have the repo downloaded, we’ll have to arrange some of the folders/files around so that we can zip everything up and send off to build.phonegap.com to package up our game for us. It is worth noting that the way that PhoneGap works is by basically wrapping a browser that points to a www directory where you put all of your assets in and packaging it as an application that can be installed onto a mobile device.

So the idea here is we’re going to have a single folder that has an index.html to provide the entry point to our application and from that index.html we’ll link to the CraftyJs, our game code, and as well as any other assets we wish to include.

## Step Two: Re-arrange the folder structure

Now to re-arrange our folder structure. The repo has the folder structure of firststeps/ img/ lib/ and samegame/. Copy and paste the img and lib folder into the samegame/4_polishing folder. Then edit the index.html script links such that the img and lib links represent the new path.

[![](/uploads/2011/07/folder_structure.png)](/uploads/2011/07/folder_structure.png)

## Step Three: Tweaks to the HTML

Within the head tags in index.html, we’re going to add this meta tag to ensure the viewport is fitted to the gameboard. Basically, the device-width argument tells the Android browser to perfectly fit the web page’s width to match the screen.

```html
<meta name="viewport" content="width=device-width" />
```

If you wish to read more about meta tags for viewports, this guide should be pretty handy: [http://developer.android.com/guide/webapps/targeting.html](http://developer.android.com/guide/webapps/targeting.html)

In addition, we’re going to add this style to the body so that it disables an annoying highlight on the element that your tapping on device like so:

```css
body {
  -webkit-tap-highlight-color:rgba(0,0,0,0);
}
```

## Step Four: Tweaks to the game code

We’re going to edit the samegame.js code, but only just slightly. Basically I’m just going to resize the dimensions of the board through the global variables so that it fits a little more nicely on device:

```js
var WIDTH = 320, HEIGHT = 530, BOX_WIDTH = 32, BOX_HEIGHT = 32, BOARD_TOP = 50, BOARD_LEFT = 0, BOARD_ROWS = 14, BOARD_COLS = 10, TWEEN_FRAMES = 15, FONT = "24px sans-serif";
```

Note the dimensions of the game board is set to 320x530. This is roughly the 3:5 aspect ratio that I’m trying to shoot for so that it matches the aspect ratio of my Nexus One.

## Step Five: Test on device

Now to zip up everything - within the 4_polishing folder, zip all the files and folders and upload it to build.phonegap.com.

After a short wait, you should get an apk file ready to be installed on device. Fire up your command prompt/terminal and install onto device by using the `adb -d install -r “pathtofile”`.  Note the arguments -d and -r; -d defines that we are  installing to a device connected via usb and `-r` means to just re-install the app if it already exists on device. If you want to use the emulator instead, try using `-e` instead of `-d`.

Now to see what it looks like:

[![](/uploads/2011/07/2011-07-06_0002.jpg)](/uploads/2011/07/2011-07-06_0002.jpg)

But when we rotate:

[![](/uploads/2011/07/2011-07-06_0003.jpg)](/uploads/2011/07/2011-07-06_0003.jpg)

## Step Six: Add the config.xml file to the folder directory

Hrm, when we rotate the screen the whole game viewport rotates and becomes unplayable. Luckily, we can set a parameter so that the game board doesn’t rotate when the device rotates by setting the orientation to portrait. We do through this by adding a config.xml document into the 4_polishing folder and then defining the property like so:

```xml
<!--?xml version="1.0" encoding="UTF-8"?--> CraftyJs starmelt tutorial CraftyJs Game Tim Kim <!-- SET TO PORTRAIT -->
```

Edit: Whoa, not sure what happened but it looks like most of the config.xml stuff didn't get copied and pasted over. Here it is again:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<widget xmlns="http://www.w3.org/ns/widgets"
  xmlns:gap="https://phonegap.com/ns/1.0"
  id="com.craftyjs.tutorial"
  version= "1.0.0">

  <name>CraftyJs starmelt tutorial</name>
  <description>CraftyJs Game</description>

  <author href="https://github.com/timkim"
    email="tim.kim@nitobi.com">
    Tim Kim
  </author>

  <gap:platforms>
    <gap:platform name="android" minVersion="2.1" />
    <gap:platform name="webos" />
    <gap:platform name="symbian.wrt" />
    <gap:platform name="blackberry" project="widgets"/>
  </gap:platforms>

  <icon src="icon.png" gap:role="default" />

  <!-- SET TO PORTRAIT -->

  <preference name="orientation" value="portrait" />

</widget>
```

You can also add a whole bunch of other goodies like the icon for the app, splash screen etc in this file as well. To read more on how the config.xml works, go here: [https://build.phonegap.com/docs/config-xml](https://build.phonegap.com/docs/config-xml)

Now:

[![](/uploads/2011/07/2011-07-06_0004.jpg)](/uploads/2011/07/2011-07-06_0004.jpg)

[![](/uploads/2011/07/2011-07-06_0005.jpg)](/uploads/2011/07/2011-07-06_0005.jpg)

Hooray! And that’s how to get a CraftyJs game working on device using PhoneGap.

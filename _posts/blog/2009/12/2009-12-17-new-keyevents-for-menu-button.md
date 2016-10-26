---
title: 'New: KeyEvents for Menu Button'
date: 2009-12-17 19:43:17 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2009/12/17/new-keyevents-for-menu-button/
status: publish
type: post
format: html
---

![phonegap_menu](http://blogs.nitobi.com/joe/wp-content/uploads/2009/12/phonegap_menu.png)

One of the big complaints that we keep hearing when you port PhoneGap apps over is that they don't follow the Android UI specifications AT ALL. The alerts don't have buttons, the back key doesn't do what it's supposed to do, etc, etc.

Well, we fixed the back button, and introduced a new event, menuKeyDown. When the menu key on any Android device is pressed, this will fire an event that will let the user know if they need to present the user with a menu of some sort. The menu could come from the bottom like the typical Android menu, or be a lightbox that takes over the window. The event exists so that the user can decide on it.

Also, the alerts have buttons now! I'm going to push these up to the EDGE version of PhoneGap momentarily.

[› Visit the original post](http://blogs.nitobi.com/joe/2009/12/17/new-keyevents-for-menu-button/)

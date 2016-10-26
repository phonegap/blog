---
title: The State of PhoneGap with Windows Mobile
date: 2009-06-02 12:22:08 Z
categories:
- app
author: Shazron Abdullah
link: http://blogs.nitobi.com/shazron/2009/06/02/the-state-of-phonegap-with-windows-mobile/
status: publish
type: post
format: html
---

Well there is no state really, except for the proof of concept currently (by PhoneGap contributor Jose Noheda). I was re-factoring the PoC code, and getting everything working with the PhoneGap Javascript common code. In a nutshell, PhoneGap WinMo cannot use the existing PhoneGap js [1], as js support in the IE control in WinMo is too primitive. The current IE in WinMo is based on desktop IE 4 (released in 1997) and only supports JScript 3/Javascript 1.3.

## So where does this leave PhoneGap WinMo? These are the ways we can proceed:

1. Have a totally separate Js codebase, based on JScript 3, for WinMo. Con: Maintenance nightmare?
1. Upgrade to IE Mobile 6\. This discussion has its own section, below.
1. Use WebKit with Qt [5]. Pro: We can probably use Qt Webkit in Nokia phones (soon, not supported yet), because well, Nokia owns Qt. Con: Using Qt adds a 10MB overhead, minimum.
1. Use our own WebKit control. Con: I don't know how long this effort will take, and it is the riskiest.

## Internet Explorer Mobile 6

IE Mobile 6 is based on desktop IE 6 (which was released in 2001) but with the IE 8 Javascript engine [2]. However, only newer (unreleased as of yet) phones will get this version, according to Microsoft [3]. Although there are development emulator images available, they are no substitute for testing on a device.

Even if we somehow get IE Mobile 6 on existing phones (with unofficial ROMs, eg through xda forums[6]), .NET code cannot take advantage of this, because Microsoft does not want to break existing compatibility with existing code that uses hosted controls [4].

## Footnotes:

[1] Sample PhoneGap Javascript code that fails under IE Mobile 4 JScript

[http://pastie.org/485649](http://pastie.org/485649)

[2] IE Mobile 6 release blog post

[http://blogs.msdn.com/windowsmobile/archive/2008/11/11/internet-explorer-mobile-6.aspx](http://blogs.msdn.com/windowsmobile/archive/2008/11/11/internet-explorer-mobile-6.aspx)

[3] IE Mobile 6 will not be available for current phones

[http://blogs.msdn.com/windowsmobile/archive/2008/11/11/internet-explorer-mobile-6.aspx#9063740](http://blogs.msdn.com/windowsmobile/archive/2008/11/11/internet-explorer-mobile-6.aspx#9063740) **[All comments were deleted after the fact by MS]**

[4] IE Mobile 6 will not be available in hosted controls (ie .NET WebBrowser component)

[http://blogs.msdn.com/windowsmobile/archive/2008/11/11/internet-explorer-mobile-6.aspx#9064039](http://blogs.msdn.com/windowsmobile/archive/2008/11/11/internet-explorer-mobile-6.aspx#9064039)**[All comments were deleted after the fact by MS]**

[5] Qt toolkit

[http://www.qtsoftware.com/](http://www.qtsoftware.com/)

[6] XDA Developers forum

[http://forum.xda-developers.com](http://forum.xda-developers.com/)

[› Visit the original post](http://blogs.nitobi.com/shazron/2009/06/02/the-state-of-phonegap-with-windows-mobile/)

---
title: Windows Phone & Apache Cordova/PhoneGap Hackathon
date: 2012-05-22 23:04:00 Z
categories:
- app
tags:
- Windows Phone
- Event
author: Jesse MacFadyen
status: publish
type: post
format: html
---

A couple weeks ago I had the pleasure of travelling to San Francisco to participate in a mobile app porting event organized and sponsored by Microsoft. This post is a little overdue now, however this was such a great event I just had to write about it.

The goal of the event was to get a better understanding of the issues developers face when porting their Apache Cordova apps to Windows Phone. I have been focused on Windows Phone development for the last ~8 months, so it was a great opportunity to observe developers using the library, and the tools I helped create. We wanted the event to be focused on porting existing apps, so we were a little more exclusive than usual in asking for developers who were already familiar with Apache Cordova, and had existing apps already published to other markets and ready to port to Windows Phone.

We aimed for a small group so we could really dig deep with attendees and get a real sense of where the platform and tools succeeded and where we could do a better job. The event was well attended and we easily filled our 20ish available spots.

## TECH-ATTENDEES

Microsoft had members of the Mobile IE team on hand, plus members of the [newly formed interop team](http://blogs.msdn.com/b/interoperability/archive/2012/04/12/announcing-one-more-way-microsoft-will-engage-with-the-open-source-and-standards-communities.aspx), and were giving away phones to anyone who could get their app running in the emulator. Adobe sent developers from the jQuery team, tech evangelists, and of course members of the PhoneGap team.

Microsoft supplied more than just pizza and beer, they supplied windows laptops, pre-configured with [all the tools needed.](http://www.microsoft.com/en-us/download/details.aspx?displaylang=en&id=27570) The assumption was that developers would be coming from the Mac world, especially the iOS developers, and while you can develop everything on Mac hardware ( which I do ) we did not want to wait for developers to install Windows 7 on a bootcamp partition.

Jean-Christophe Cimetiere (aka JC) was also able to expedite AppHub membership requests so developers could immediately run their apps on the device. Microsoft gave away Windows 7 licenses to everyone, so that they could install on their own machines and continue working on their projects after the event.

## MY-ROLE

I did a brief presentation to kick things off, which was really just an introduction to the platform, and what differences to expect. I also covered a few pain points, that I knew would hold developers up, covering things like mouse events, and css transitions. Currently jQuery Mobile (jQM) is the only framework that has an easy migration path for the differences between mobile IE9 and the various WebKit browsers found on all of the other devices Apache Cordova supports. This is largely due to the way that jQM relegates to native scrolling, and scales back transitions when CSS3 transitions/animations are not available.

A particular stumbling block that I knew would hold up porting was the absence of mouse events in the Windows Phone WebBrowser control. I had previously spent a lot of time experimenting with mouse emulation, so I knew that this was a large barrier for newcomers to the platform. With this in mind, I focused a couple days before the event, and proudly announced full support for mouse events. In my presentation I was able to demonstrate some interactions that were previously not even possible, including: a basic slider component, allowing scroll from some elements, and preventing it from others, finger drawing on a canvas, and running the iScroll4 sample page unmodified to demonstrate momentum scrolling with fixed header + footers.

{% include video.html id="4CPaCgHQNrc" %}

The mobile IE developer team was super impressed with what I had accomplished, essentially working around an issue that they are very much aware of. Hopefully this functionality will make it into a future device update. I was able to make some recommendations about how it is implemented in the future, but for now the mouse events are only available in hosted silverlight webbrowser controls, and not IE9 which ships on all windows phone currently. The c# class that enables mouse interaction is not dependent on Apache Cordova, and is usable in any silverlight windows phone app, so I will be making it available as a standalone repo as well, so mouse events can be added to any Windows Phone app that is using the Webbrowser component.

Coincidentally, (or not?), my colleagues [lunny, hardeep] who have been working on Adobe's PhoneGap build service [announced](https://phonegap.com/2012/04/24/phonegap-build-welcomes-windows-phone-7/) support for Windows Phone the same day. I was able to demonstrate uploading a simple app zip, downloading the XAP file, and installing and running it on my connected phone. Flawless! Great work Build team!

## DEV-ATTENDEES

The event had about 20 attendees, of which many were able to make progress of porting their applications. The developers who came got help from Microsoft employees and Adobe employees from the PhoneGap team, the WebKit team and Adobe Evangelists. The WikiMedia team also attended to work on the windows port of their [Wikipedia PhoneGap App](https://phonegap.com/app/wikipedia/).

During the day I saw multiple successful ports, including apps from some people who were just experimenting, and others who were porting large amounts of code from Android and iOS.

Attendees ranged from one-dev shops working on their own projects, to developers contributing to large scale open source projects ( [Wikipedia PhoneGap app](https://phonegap.com/app/wikipedia/). ), to developers from companies that had their own app-builder services.

Microsoft will be releasing a blog post with updates on some of the ports people were working on, hopefully with links to published apps in the Marketplace.

## Metro theme for JQuery Mobile

MicroSoft’s Abu Obeida announced the availability of a new Metro theme for Windows Phone. His blog post is <http: blogs.msdn.com="" b="" interoperability="" archive="" 2012="" 04="" 26="" more-news-from-ms-open-tech-announcing-the-open-source-metro-style-theme.aspx="">here. Abu has been working closely with [Sergei Grebnov](https://github.com/sgrebnov) over the last few months to make the Metro theme available to webpages using jQuery Mobile. ( Sergei is a key contributor to Apache Cordova for Windows Phone, and I have worked closely with him over the course of my work on Windows Phone. )</http:>

During the event Abu demonstrated the Metro look and feel applied to an Apache Cordova application by simply changing the css files ( another win for the web ) The extra cool part is the fact that Sergei has implemented an Apache Cordova Windows Phone plugin so your app can not only display the Metro look and feel, but it can also display it based on the device options set by the user. Windows Phone supports user selected color themes, and some control over text size, all of which are immediately available to your Cordova app. Abu demonstrated this by switching to the Settings app, changing the theme color, and returning to the app, where magically all controls were updated to the the new theme. Nice work!

## TAKEAWAYS

* Visual Studio 10 Express for Windows Phone is not the best place to be editing html and js. While Visual Studio Web Developer Express can handle all the html/js editing, it is a separate tool, and if I am going to use a second tool, I prefer Sublime Text.
* Debugging tools for JavaScript suck, we desperately need the ability to step through code, set breakpoints, and all that. Attempting to find issues with alert/console is very discouraging.
* It is difficult to drop 300 KB of js code into a new device project and have it just work. In JavaScript, it only takes one error to break EVERYTHING. ( Debugging tools would help !!! )
* jQuery Mobile works almost everywhere.
* It is tough to add a whole bunch of files at once to Visual Studio when they have a folder structure you need to maintain. ( or at least it appears to be, I will be doing a short post on an easier way. )
* We need more documentation.

Developing Windows Phone + Apache Cordova applications is pretty straightforward, and based on comments from attendees, things work as expected. Developers familiar with the Cordova project seemed to get up to speed on Windows Phone very quickly. Visual Studio is a decent tool for the task, and developers were able to use it quickly even having never used it before.

I found this to be a very productive event, and gained some valuable insight into the types of features developers need to be effective. Microsoft is planning on continuing to host events like this in the future, this was really a small scale test, so I look forward to being involved in future events as well.

## LINK BAIT

* [Metro theme for JQuery Mobile](http://blogs.msdn.com/b/interoperability/archive/2012/04/26/more-news-from-ms-open-tech-announcing-the-open-source-metro-style-theme.aspx)
* My Blog, where you can expect posts on update [http://risingj.com](http://risingj.com)
* [The Apache Cordova WP7 github mirror](https://github.com/apache/incubator-cordova-wp7)

## Adobe

* Jesse MacFadyen [@purplecabbage](http://twitter.com/purplecabbage)
* Shazron Abdullah [@shazron](http://twitter.com/shazron)
* Steve Gill [@stevesgill](http://twitter.com/stevesgill)
* Terry Ryan [@tpryan](http://twitter.com/tpryan)

## MicroSoft

* Jean-Christophe Cimetiere [@jccim](http://twitter.com/jccim)
* Abu Obeida Bakhach [@abuobeida](http://twitter.com/abuobeida)
* Olivier Bloch [@obloch](http://twitter.com/obloch)
* Justin Woo [@jzwoo](http://twitter.com/jzwoo)

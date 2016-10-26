---
title: 'April Updates: New Features on build.phonegap.com'
date: 2011-04-11 18:26:20 Z
categories:
- PhoneGap Build
author: Fil
status: publish
type: post
format: html
---

[![](/uploads/2011/04/PhoneGap-Build-Winning.jpg)](/uploads/2011/04/PhoneGap-Build-Winning.jpg)

Over the past couple of weeks, we've made some good progress on our cloud-based building solution for PhoneGap developers, [PhoneGap Build](http://build.phonegap.com). For those that are out of the loop, this service takes the pain away from building your HTML, CSS, and JavaScript-based applications to various platforms by letting the cloud handle the compilation and packaging of each mobile platform's binary. This way, PhoneGap developers can focus on what they do best: building awesome software using standards-based web technologies. If you haven't signed up for it, [go do so now, right from the home page](http://build.phonegap.com)!

I wanted to highlight some of the work that we've completed over the past month or so to make sure that developers out there are taking full advantage of the features provided by [PhoneGap Build](http://build.phonegap.com).

Some of the bigger features we've deployed recently include:

* **Better config.xml support**. To quickly recap, [config.xml is the W3C-advised way of configuring "widgets"](http://www.w3.org/TR/widgets/), or web-based device applications. [PhoneGap Build](http://build.phonegap.com) fully utilizes this file as a way for the developer to specify metadata for their application. Some recent additions to the config.xml support include:

* **Icon support**. By specifying one or more `<icon>` elements, you can have PhoneGap Build use images inside your application package for the app icon(s). Specifying a few different icons of different sizes helps, as some platforms like [Android support multiple icons of various resolutions](http://developer.android.com/guide/topics/resources/providing-resources.html#DensityQualifier) and will show the best one depending on device screen density. You need to specify a few attributes for this element; go ahead and check out the details in our [config.xml documentation section.](https://build.phonegap.com/docs/config-xml)

* **Splash screen**. By specifying a `<splash>` element, you can tell PhoneGap build which image to show for the splash screen. The splash screen is displayed immediately upon the application being loaded. It will continue to be displayed until your PhoneGap app has finished loading your first page in. Again, refer to the [config.xml documentation section on PhoneGap Build](https://build.phonegap.com/docs/config-xml) for details.

* **Better error reporting**. We have done some work to try to analyze submitted applications and check ahead of time if any of the build processes will have trouble with it. In particular, BlackBerry builds have been failing at a notoriously high rate. There are a variety of factors that cause this, but most of them stem from the very strict rules the BlackBerry Widget Packager has on file and directory names. Apparently even icon images that are greater than 16 kB will cause the Widget Packager to crap out! In light of this, we are trying to report these errors back to our Build users before we queue the app up for building. If you see the red error sadface, hover over it and you may get a more verbose description of the potential problem.

We're constantly tweaking the web interface for [PhoneGap Build](http://build.phonegap.com), too. Each application now has a last-built timestamp, and we also keep track of how many times each app has been built. Additionally, we've expanded our documentation a bit. I've mentioned that [the config.xml docs](https://build.phonegap.com/docs/config-xml) are improved, but we've also expanded the ["Build Failed?" section](https://build.phonegap.com/docs/build-failed) to try to address some of the common errors we've been seeing.

Last but not least, I wanted to mention some cool things that we're currently working on for [PhoneGap Build](http://build.phonegap.com) that we are going to release pretty soon. First, **PhoneGap plugin support is coming very soon**! We have iOS plugins working (internally just for now :) ) and Android plugins in the works. Eventually we'll get support for plugins on the other platforms as well. The other feature we're working on, that I think will generate a lot of excitement for our users, will be w**eb-based CSS inspection and JavaScript console support**. I don't want to give too many details out, but for those keeners out there, perhaps check ou[t Patrick Mueller](http://twitter.com/#!/pmuellr)'s [Weinre](https://github.com/pmuellr/weinre) project to get an idea of where we are heading with this.

One more thing: if you are using [PhoneGap Build](http://build.phonegap.com) right now and have a question, a problem, or just want to let us know how much you like us, drop by the [PhoneGap Build support site](http://getsatisfaction.com/nitobi). We're pretty fast with responding and we like to iterate on new ideas, fixes and features quickly, so let your voice be heard!

We're excited with the direction we're heading and can't wait to enable more PhoneGap developers. Keep on building apps, folks.

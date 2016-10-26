---
title: Introducing iPhone Cleavage
date: 2010-04-21 05:52:13 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2010/04/20/introducing-iphone-cleavage/
status: publish
type: post
format: html
---

So if you want to make an iPhone app using your HTML/CSS/JavaScript skills, what do you use? PhoneGap! obviously.

If you want to add some iPhone native controls, screens, whatever… [PhoneGap Plug-ins](http://github.com/purplecabbage/PhoneGap-Plugins) seem like a fairly easy path, even though they are still largely undocumented, and unknown to most, at least they are somewhat planned.

But what if you have a native iPhone app already, and you want to quickly throw in some phonegap. Before today, there was no easy way to do this because phonegap for iPhone was architected to be the one and only Application delegate. This is the newest use case I have chosen to address.

This approach of breaking PhoneGap functionality into it's own control space makes some exciting new things possible in the near future. Including:

* Multiple page / view apps where the views are persistent ( instead of having to reload or navigate between pages )
* Sandboxed child apps
* The ability to divide work among multiple developers, without having to constantly keep track of other's changes.
* Better division of responsibility within code modules ( divide and conquer methodologies ).
* Drop-in functionality, for code libraries, add them to your app more easily, and build up your control library over time.

## Introducing Cleavage for iPhone.

First off, you may be wondering about the name. I wanted to stick with the 'gap' theme so I started brainstorming on other types of gaps.

At first I considered [Diastema](https://en.m.wikipedia.org/wiki/Diastema)) as it has a nice ring to it. After thinking on that for awhile I decided it would be best not to alienate phonegap developers as we are predominantly Madonna, Letterman, and Mad Magazine fans. _( What, me worry?)_

Other Gaps I considered were :

* Rift - too sci-fi
* Gape - um, too close to Gap
* Fissure - too literal, and weird …
* cavity, chasm, crack, … - just not it

So cleavage it is! .. and given it's current state it is very much as Jerry Seinfeld says.

> "Looking at cleavage is like looking at the sun. You can't stare at it long, it's too risky. You get a sense of it then you look away."

Please keep in mind that this is very much a work in progress, but expect some updates in the near future.

I have posted the PhoneGap control sample app to: [http://github.com/purplecabbage/cleavage](http://github.com/purplecabbage/cleavage)

Documentation and such to follow later in the week, I hope, here is a quick getting started description.

In order to use this in your own ( pre-existing ) iPhone OS project, you will need to:

1. add all PhoneGap required frameworks to your project ( the sample project has them all )
1. add a reference to PhoneGapLib ( you will need the latest checked in version )
1. place your html/js/css in a www folder in the project and be sure it is packaged in the root of your app when built
1. include phonegap.js from PhoneGapLib, as it is not auto-copied over for you like it is in a typical phonegap iPhone app.
1. set linker flags for -all_load and -ObjC

[› Visit the original post](http://blogs.nitobi.com/jesse/2010/04/20/introducing-iphone-cleavage/)

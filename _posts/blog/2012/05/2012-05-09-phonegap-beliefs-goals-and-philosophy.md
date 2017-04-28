---
title: PhoneGap Beliefs, Goals, and Philosophy
date: 2012-05-09 09:06:35 Z
categories:
- app
tags:
- Insight
author: Brian LeRoux
status: publish
type: post
priority: 5
format: html
featured: true
---

This article seeks to clear up misunderstandings about the goals of PhoneGap.

Our goals are wrought from our beliefs, and development philosophy. Understanding a free software project, like PhoneGap, requires more than knowledge of the implementation details. It requires understanding the individuals behind the code. Knowing the people and what motivates them inform you more about whether the technology is right for you, your goals, and the people you work with. The world is diverse and very often this comes across in our code, and the tools we use to write it.

## Background

PhoneGap was born at Nitobi Software in the summer of 2008\. Nitobi was very much a web consultancy with deep roots in the JavaScript scene, and web dev at large. Being a consultancy we had a few beliefs that have grown into the PhoneGap project team members. These views are mine own and shared by many PhoneGap developers and Apache Cordova committers.

## Beliefs

We have two core tenants of belief:

* The web solved cross platform.**
* All technology deprecates with time.

We believe the web has been the most convincing solution to reaching many devices of differing capabilities. Truly, C is the only technology that deserves the title but even then, all readers here know, there be dragons there. HTML, CSS, and JavaScript, for all the respective warts and quirks, have reached critical mass. This is in no small part due to the incredibly low barrier for authoring web technologies. Anyone, at any time, can publish anything from anywhere. _That is the stuff of revolutions, and our evolution as a species._

Our second belief makes a brave statement: all technology deprecates. This is more of an observation, and history is on our side. With this in mind, as consultants, we knew hitching our wagon to any one horse could have disastrous consequences. Of course this is not absolute. Some technologies span many decades to the profit of the specialist. **As technologists it is our responsibility to remain present and aware of change.** Whether we act is the choice. _The consequences of not acting could be witness to a technology replacing our own._

## Goals

Understanding our beliefs makes it easier to understand why we have composed a development team that is proficient in 8 languages, as many operating systems, and works daily with enough phones to fill a refrigerator. We would put 'em in the fridge but that's where we keep the beer so [we built a giant wall](https://phonegap.com/2012/03/29/phonegaps-new-device-wall/). **The device wall isn't something to keep phones in: it's for keeping proprietary platforms out.** Beliefs in hand, let us look at the goals with PhoneGap.

We have two high level goals with PhoneGap:

* The web as a first class development platform.
* The ultimate purpose of PhoneGap is to cease to exist.

The web is decidedly **not** a first class development platform: opaque introspection, blunt tools, poor API surface area, and a rather limited set of GUI elements. The web has host of other problems, or perhaps features, such as the sandbox and many missing APIs which need addressing which provides a fantastic opportunity. In short, we feel the web as a platform is at a disadvantage, and we're working to polyfill those gaps with PhoneGap.

Our second goal is not nihilistic but is rather a commitment to standardization of the web as a platform. We believe in a web open to everyone to participate however they will. No locked doors. No walls. The things we do with PhoneGap are directly influenced by the work we see at the W3C, WHATWG, and other research such as Mozilla's WebAPI, BONDI, WAC, Webinos, webOS, Tizen and the like.

## Philosophy

Many of us are UNIX geeks. We believe in simple, wickedly sharp, purpose built tools. PhoneGap is a solution much the same. We are not trying to be everything to everyone. We do believe the web has solved a great many use cases in software, and as it improves, it will continue to do so.

It isn't without a sense of irony that our first belief (the web solved cross platform) is at stake with the second (all tech deprecates). **This is why we act.** We know the web is not the platform it can be and we are actively working to improve it. We recognize that the limitations of the web platform are harming the viability for a great many use cases and giving an edge to proprietary solutions with better tools. That is not the future aligned with our beliefs, nor our goals.

Attachment is the root cause of all suffering. We are not attached to the web, JS or any of it. Indeed, in order to implement PhoneGap many of us are now veterans of many platforms, languages, tools and operating systems. Keep 'em coming: we'll put a browser there too.

We ship fast, often twice a month, and have done so for a long time now. I've heard it said that PhoneGap can lag behind native implementations and, while technically correct, we rarely lag more than two weeks. Additionally, there is a very low barrier for a developer to author a plugin for functionality we haven't yet writ ourselves. [I highly encourage you to read about our release philosophy.](https://phonegap.com/2012/04/12/rolling-releases-how-apache-cordova-becomes-phonegap-and-why/) I feel we are among the best at it in the industry today.

## Closing Thought

We agree that there are no silver bullets, and the web isn't the best tool for every job. However, the web is not getting worse, and the browser abstraction layer is ultimately the same across operating systems (C, C++). If the web doesn't do something today it's not because it can't, or won't, but rather it is because we haven't gotten around to implementing that capability yet.

If you want to help the web get there you can [learn more about contributing here](http://cordova.io). If you want to have an intelligent debate on the real drawbacks of PhoneGap: [you can start by trying it out here](https://phonegap.com/download).

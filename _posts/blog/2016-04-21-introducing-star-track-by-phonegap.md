---
title: 'Introducing: Star Track by PhoneGap'
date: 2016-04-21 00:00:00 Z
tags:
- Announcement
- Framework
- Documentation
- App
author: Tommy-Carlos Williams
---

A Complete PhoneGap Example App Using [Framework7][framework7.io] and the [Spotify API][spotify-api]

TL;DR: [Check it out now on GitHub][star-track-github]

## The Name

Let's get something out of the way. It is _not_ a serious name. We have no plans to release _Star Track_ on any app stores and we know that at the very least it is already the name of a postal logistics service in Australia. It's just a cute name that pretty much describes what the app does. What does it do? So glad you asked.

## What is It?

Many people might be familiar with [Holly Schinsky's blog][hollys-blog] and her ongoing series featuring implementations of her _iTunes Media Finder_ app. _Star Track_ is inspired by her _iTunes Media Finder_, but instead uses the Spotify Web API. If you don't yet follow Holly's blog, you should. Go bookmark it in another tab or something and come back. I'll wait.

![Star Track Screens](/blog/uploads/2016-04/star-track-screens-ios.jpg)

In a nutshell, _Star Track_ allows you to search for songs (tracks), then preview the tracks in your results. If you like a track, you can add it to your favourites (star it). I know right? Like the name a bit better now?

## Why We Built It

_Star Track_ was built for a few reasons. We really wanted a _complete_ app beyond a basic Hello World that you could try out straight away on your device(s) jumping right into a finished experience. The goal was also to help alleviate any concerns about hybrid apps, such as those made with PhoneGap, having performance issues. There is a pretty long-standing trope that PhoneGap is slow. Dispelling that has been a bit of a passion of mine.

![PhoneGap isn't Slow](/blog/uploads/2016-04/google-search-is-mean.jpg)

Secondly, the PhoneGap team are at the very beginning stages of writing a series of documentation, guides, and tutorials that would take you "from idea to app store". Far too much of the prevailing information on developing PhoneGap apps concentrates on getting started, and while that is very useful, it leaves you to figure the rest out on your own. Forced to cobble info from Stack Overflow, other blogs. Leading to the need to ask questions on forums, IRC, mailing lists, and Slack. To have a continuing series, we needed a common app that the tutorials walk you through building from scratch. _Star Track_ will be that app. Kind of the software equivalent of "here's one I prepared earlier", so to speak.

## Framework 7

> Studies show that a todo list is the most complex JavaScript app you can build before a newer, better framework is invented
&emdash; from [A JS framework on every table - by Allen Pike][js-framework-on-every-table]

Once we decided to build _Star Track_, we had to decide _how_ we were going to build it. Use React? Angular? Build everything from scratch? We wanted something approachable that was understandable by relative beginners _and_ the ES2015 crowd. Guides that are too centered on something specific can turn off those that have no interest in that particular framework. Not only that, but a tutorial written for framework A might be incomprehensible to someone used to developing in framework B. We also wanted it to look nice.

We decided on Framework 7 because it was approachable and looked lovely. Framework 7 apps are written in a back-to-basics jQuery style of coding that should be just as readable by the deepest immutable devotee as it is by someone taking their first tentative steps into the pool.  Framework 7 is written specifically for mobile apps and it shows. It has features like gestures for navigation, fast beautiful animations, and looks at home on iOS as well as Android thanks to the recent addition of a Material theme.

![Star Track Material](/blog/uploads/2016-04/star-track-screens-android.jpg)

_Star Track_ and the guides will be written using Framework 7, but shouldn't be so entrenched in it that the concepts won't be easily transferable to your personal favourite. I am also hoping that we will have side-track articles that might go into how a topic might be implemented in one or more of the other popular frameworks.

## Spotify and the Browser Platform

If you'll recall from way back up near the top of the page, I said that _Star Track_ was, at its heart, a version of Holly's _iTunes Media Finder_ but using the Spotify API instead? The main reason for the change is Spotify's support for CORS. I have always been a fan of staying in the browser for as long as I could when developing a PhoneGap app. Browsers have the best developer tools and a truly excellent developer experience. They also have a test-debug-change-test-again iteration speed that makes native developers cry. The problem with this mantra has always been plugins. As soon as your app relies on the functionality in a plugin like Contacts or Media, you have to start using a simulator. Or worse, if your app relies on the Camera plugin, the iOS Simulator doesn't even support that, so you are testing on a device or out of luck.

The "browser platform" changes all that at least for a core set of plugins and ones whose authors have added support. I am not going to go into it here. There are [other][browser-platform-phonegap] [posts][browser-platform-raycamden] that can do it justice better than I can. Let's just say that CORS support in the Spotify API meant that _Star Track_ can be developed, tested and debugged using the browser platform and that is a good thing.

## Templates

Another thing we've been getting excited about lately are templates. PhoneGap and Cordova now support [creating new apps using a template][phonegap-templates] from a local folder, npm, or a git URL. This is a really exciting development as it allows quick creation of apps from boilerplate set-ups like the [React Hot Loader template][react-hot-loader-template] or the [Framework7 template][framework7-template]. _Star Track_ itself was developed by starting with the Framework 7 template. Not only that, but it also makes sharing an example app like _Star Track_ much easier. Instead of having to clone a GitHub repository then run the app, you can just create a new PhoneGap app that is a copy of _Star Track_.

```bash
phonegap create StarTrack --template https://github.com/phonegap/phonegap-app-star-track
cd StarTrack
phonegap serve

```

## What's Next?

What's next for you is to take it for a spin. See what you think. Create an app using it as a template. Try it on both Android and iOS. Tell us what you think.

For us the next step is to get started actually writing the new guides. Taking you from "idea to app store". This post is already way too long. I better get back to it.

[framework7.io]: http://framework7.io
[spotify-api]: https://developer.spotify.com/web-api/
[star-track-github]: https://github.com/phonegap/phonegap-app-star-track
[hollys-blog]: http://devgirl.org
[js-framework-on-every-table]: http://www.allenpike.com/2015/javascript-framework-fatigue/
[browser-platform-phonegap]: https://phonegap.com/blog/2016/02/19/browser/
[browser-platform-raycamden]: https://www.raymondcamden.com/2014/09/24/browser-as-a-platform-for-your-phonegapcordova-apps/
[phonegap-templates]: https://phonegap.com/blog/2016/02/24/phonegap-cli-6-0-0/
[react-hot-loader-template]: https://github.com/phonegap/phonegap-template-react-hot-loader
[framework7-template]: https://github.com/phonegap/phonegap-template-framework7

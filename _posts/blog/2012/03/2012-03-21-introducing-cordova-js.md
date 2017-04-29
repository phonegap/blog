---
title: Introducing Cordova-JS
date: 2012-03-21 19:38:38 Z
categories:
- app
tags:
- News
author: Fil
status: publish
type: post
format: html
---

A lot of exciting things have happened in the past six months or so: my former employer [Nitobi](http://nitobi.com) got acquired by [Adobe](http://adobe.com) and our team of about 18 more or less got split right down the middle. Half are now settling into San Francisco, while the rest (me included) are holding down the Canadian fort in Vancouver and doing our best to represent [Adobe](http://adobe.com) up in the Great White North.

I'm still working on [PhoneGap](https://phonegap.com), now reborn as an [Apache Software Foundation](http://apache.org) project known as [Cordova](http://incubator.apache.org/cordova). My most recent task has involved bringing the disparate implementations of [Cordova](http://incubator.apache.org/cordova)'s [JavaScript API](http://docs.phonegap.com) - a consistent, cross-platform API - under one repository. Up until this point, each platform maintained its own set of JavaScript files implementing this API. The idea and implementation I'm going to present in this post is that 90+ percent of the JavaScript for any given [Cordova](http://incubator.apache.org/cordova) platform is identical. Most of the [Cordova](http://incubator.apache.org/cordova) API boils down to sending simple messages to the native framework, with the expectation that a failure or success callback will be fired in the future back in [Cordova](http://incubator.apache.org/cordova)'s web context. The unified JavaScript project is called [cordova-js](http://github.com/apache/incubator-cordova-js).

I'm excited to say that in [Cordova](http://incubator.apache.org/cordova) 1.5 we landed [cordova-js](http://github.com/apache/cordova-js) in the [Android implementation](http://github.com/apache/cordova-android). In [Cordova](http://incubator.apache.org/cordova) 1.6 we are going to drop it into the [iOS implementation](http://github.com/apache/cordova-ios)! It has already landed in the Apache [Cordova](http://incubator.apache.org/cordova) [iOS master](http://git-wip-us.apache.org/repos/asf?p=incubator-cordova-ios.git;a=commit;h=ab2afceeffda5c5bef9410d1f60b45426176f171)!

The project has been an up-and-down ride. [Dave Johnson](http://twitter.com/davejohnson) and [Michael Brooks](http://twitter.com/mwbrooks) of [Nitobi](http://nitobi.com) initially championed this idea with the [phonegap-js](https://github.com/davejohnson/phonegap-js) project. Months later, [Gord Tanner](http://twitter.com/gordtanner) from [RIM](http://rim.com) (along some [daleks](https://raw.github.com/apache/incubator-cordova-js/master/build/dalek)) was using the same direction [phonegap-js](https://github.com/davejohnson/phonegap-js) laid down to integrate new APIs in their open source device and API emulation tool, [Ripple](http://ripple.tinyhippos.com/). [Gord](http://twitter.com/gordtanner) and company (mostly the old [TinyHippos](http://tinyhippos.com) crew, which got acquired by [RIM](http://rim.com)) reached out to us to show us what they did. What we saw blew our minds: clean, modular syntax for all API definitions with a very clear architecture and obvious mappings to JavaScript properties and globals. Around this time I jumped in to help out where I could and [Gord](http://twitter.com/gordtanner), [Ken Wallis](http://twitter.com/ken_wallis) and [Laurent Hasson](http://twitter.com/ldhasson) from [RIM](http://rim.com) all flew up to Vancouver so that we could discuss the [cordova-js](http://github.com/apache/incubator-cordova-js) implementation and hack on it for a few days (and maybe drink a few beers while we're at it). Turned out to be a very fruitful week with lots of progress made. One of the early contention points of the project was: how are we going to implement the module system? Should we use an existing solution out there or roll our own? Luckily for us peeps in Vancouver, [Mozilla](http://mozilla.org) has an [office and a team up here](http://twitter.com/mozillayvr), and among the talented people working there is [James Burke](http://twitter.com/jrburke), author of [require.js](http://requirejs.org). Who better to talk to about the situation than a man closely involved and directly influencing the various styles of JavaScript modules floating around? We ran a little lunch-n-learn and invited [James](http://twitter.com/jrburke) over to come share ideas. Initially we ended up using [almond.js](http://github.com/jrburke/almond), a small module loader that was compatible with both [AMD](https://github.com/amdjs/amdjs-api/wiki/AMD) and [CommonJS](http://commonjs.org) modules. Later on, to enforce our own requirements (specifically around throwing exceptions for non-existent modules), we forked and cut down [almond.js](http://github.com/jrburke/almond) to the bare-bones that we need for [cordova-js](http://github.com/apache/incubator-cordova-js) purposes. Finally we were on track to ship a working version of [cordova-js](http://github.com/apache/incubator-cordova-js). Android was our first target. [Joe Bowser](http://twitter.com/infil00p) (of [Adobe](http://adobe.com)/[Nitobi](http://nitobi.com)) and [Simon MacDonald](http://twitter.com/macdonst) (of [IBM](http://ibm.com)) helped make that happen. [Becky Gibson](http://twitter.com/becka11y) (of [IBM](http://ibm.com)) and [Shazron Abdullah](http://twitter.com/shazron) ([Adobe](http://adobe.com)/[Nitobi](http://nitobi.com)) put a lot of work in to get it going on iOS. [Patrick Mueller](http://twitter.com/pmuellr) ([IBM](http://ibm.com)), [Brian LeRoux](http://twitter.com/brianleroux) ([Adobe](http://adobe.com)/[Nitobi](http://nitobi.com)) and [Jesse MacFadyen](http://twitter.com/purplecabbage) ([Adobe](http://adobe.com)/[Nitobi](http://nitobi.com)) chimed in to offer advice and guidance. Truly a team and community effort across corporations (warms my heart!). Thanks to everyone involved for making it happen. This lays down the foundation for us to hit our goals for [Cordova](http://incubator.apache.org/cordova) 2.0.

## Why?

If it works, why f_*_ with it? The answer lies in the road ahead to [Cordova](http://incubator.apache.org/cordova) 2.0\. We want any arbitrary device APIs - be they [Cordova](http://incubator.apache.org/cordova) "core" APIs or not - to be installable, discoverable and removable at a developer's discretion. For those familiar with [PhoneGap](https://phonegap.com) [plugins](http://github.com/phonegap/phonegap-plugins), this is exactly the same idea. A stock [Cordova](http://incubator.apache.org/cordova) API is no different from a plugin. We've been part of the way there for some time now; all of the various native implementations employ some manner of plugin architecture. The JavaScript, however, has been a wild-west of sorts. We are changing that with the introduction of [cordova-js](http://github.com/apache/cordova-js).

The biggest change is the use of modules in JavaScript. [CommonJS](http://commonjs.org)-inspired but much simpler, it does the job for now. A [simple `define` and `require` syntax](https://github.com/apache/incubator-cordova-js/blob/master/lib/require.js) is used and scoped only to the cordova.js file. Within the cordova.js file you'll see things like:

```js
define('cordova/channel', function() {
  // Amazing code goes here
});

// ... somewhere else in the code

var channel = require('cordova/channel');
channel.onDeviceReady.fire();
```

All of the little interesting bits inside the cordova.js file are wrapped in a `define` call, turning cordova.js into a set of small, focused modules tasked with doing one thing well. Early on we scoped our module syntax globally. [This turned out to be a bad idea](https://issues.apache.org/jira/browse/CB-304). Now, `define` and `require` are available inside the cordova.js file, or if you want to use it for your own projects you can access these methods via `cordova.define` or `cordova.require`.

A side effect of using a [CommonJS](http://commonjs.org)-inspired module syntax is that we can use the resulting script file interchangeably between [node](http://nodejs.org) and [PhoneGap](https://phonegap.com)/[Cordova](http://incubator.apache.org/cordova) contexts. Due to our simple module system for use in WebView contexts, we can maintain the convention of one-closure-per-file employed in other [CommonJS](http://commonjs.org) environments, or piggy-back off of [node](http://nodejs.org)'s module system to do cool things such as run unit tests locally in [node](http://nodejs.org). Winning!

As for changes introduced with [cordova-js](http://github.com/apache/incubator-cordova-js), the main one is the name switch in your JS from `[PhoneGap](https://phonegap.com)` to `cordova`.

Next up I'll be aiming to explain a general process for upgrading pre-1.5 plugins to this new approach (perhaps a case study / real world plugin upgrade to go along with it?).

Happy coding!

[This post was originally posted by [Fil Maj](http://twitter.com/filmaj) on [filmaj.ca](http://filmaj.ca)]

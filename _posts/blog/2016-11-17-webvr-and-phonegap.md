---
title: WebVR and PhoneGap
date: 2016-11-17 00:00:00 Z
tags:
- Release
- News
author: Shazron Abdullah
---

I attended the ["WebVR Ecosystem and API Update" meetup](http://www.meetup.com/sfhtml5/events/230072340/) held on May 25th, 2016, in Google's San Francisco offices (which are near Mozilla's) overlooking the Bay Bridge. The WebVR event is usually held once a year and it was sponsored by both Google and Microsoft.

The event was $10 per ticket, and about 200 people showed up -- which included a raffle for prizes (lots of bottles of wine, plus a grand prize being a ChromeBook Pixel) and catered dinner and drinks, as well as the talks. There was not enough seating, some people had to stand.

The talks were [recorded and posted on YouTube](https://www.youtube.com/watch?v=iPsWEH1PUes&feature=youtu.be&list=PLUj8-Hhrb-a1TFwToqb6GcMgRHafG403a), with speakers from [wevr](http://wevr.com/) [[Tony Parisi](https://twitter.com/auradeluxe)] now at [Unity](https://unity3d.com/community), Google [[Brandon Jones](https://twitter.com/Tojiro)][[Boris Smus](https://twitter.com/borismus)], Mozilla [[Kevin Ngo](https://twitter.com/andgokevin)][[Diego Marcos](https://twitter.com/dmarcos)], [AltVR](http://altvr.com) [[Amber Roy](https://twitter.com/amberroyVR)] now at [Oculus](https://www.oculus.com/), and Microsoft [[Liv Erickson](https://twitter.com/misslivirose)].

I will be giving my summary of the talks, as well as concluding with what this means for Adobe PhoneGap.

## WebVR 1.0 (Google and Mozilla)

[WebVR](https://webvr.info) is a [W3C Draft spec](https://w3c.github.io/webvr/), which provides a JavaScript API to virtual reality devices. WebVR is designed for embeddable VR experiences in stereo at 60 frames per second in the browser, with support for head-mounted displays. None of the current browsers support this spec yet, but it was slated for release in Chrome 54, in October of 2016, also Firefox in the later half of 2016. As of November 2016, support for WebVR is still not there in the public releases of Chrome 54 and Firefox 50. Later during the year (but not at the event) Microsoft would announce upcoming [WebVR support in Edge](https://blogs.windows.com/msedgedev/2016/09/09/webvr-in-development-edge). No word from Apple about WebVR support in Safari.

It has been recently re-factored ([version](http://blog.tojicode.com/2016/02/moving-towards-webvr-10.html) [1.0](https://hacks.mozilla.org/2016/03/introducing-the-webvr-1-0-api-proposal/)) to support the new capabilities of VR devices that have been recently released, particularly the [Oculus Rift](https://www.oculus.com/) and [HTC Vive](https://www.htcvive.com/), and a focus on [WebGL](https://en.wikipedia.org/wiki/WebGL) content. Tracked controller support -- like the controllers that come with the HTC Vive, and upcoming Oculus Touch controllers -- will be supported in WebVR through the [W3C Draft GamePad API](http://www.w3.org/TR/gamepad/).

Since WebVR is not baked into browsers yet, there is a [WebVR polyfill](https://github.com/borismus/webvr-polyfill) that works quite well, anywhere you have WebGL support -- which [includes mobile browsers](http://caniuse.com/#search=webgl) like Safari on iOS and of course Chrome on Android. There is also the concept of "Responsive VR" (like Responsive Design) through use of the [WebVR Boilerplate](https://github.com/borismus/webvr-boilerplate).

Google's use of WebVR can be seen in their [VR View](https://developers.google.com/vr/concepts/vrview) work, where you can embed VR images and videos into a web page. An example could be a [VR view in Wikipedia](https://storage.googleapis.com/vrview/examples/pano/index.html), showing Machu Picchu. You can create these VR Views yourself to embed in a web page using [Google Cardboard Camera](https://goo.gl/FDcroh) and converting them using the [Cardboard Camera Converter](https://goo.gl/2AcqfC).

Try out some WebVR examples by using the polyfill link: [https://webvr.info/samples/](https://webvr.info/samples/) (you can use Google Cardboard as well).

The development of WebVR has been driven mainly by Google and Mozilla.

![WebVR Boilerplate](/blog/uploads/2016-11/webvr-boilerplate.png)

## A-Frame (Mozilla)

Created by Mozilla VR in December of 2015, [A-Frame](https://aframe.io) is a web framework that provides a [declarative way to create VR](https://hacks.mozilla.org/2016/03/build-the-virtual-reality-web-with-a-frame/), and is a layer on top of WebGL, and [three.js](http://threejs.org). WebVR's API might be too uninviting for some, and the declarative nature of A-Frame aims to make it easier for everyone to create VR experiences.

A-Frame doesn't just have declarative markup, but it has also has extensibility through their use of the [Entity-Component-System (ECS)](https://aframe.io/docs/0.2.0/core/) pattern. For example , you can have a `car` entity, that has `engine` and `tire` components -- each of the components themselves have properties (horsepower, grip).

It has a thriving community. The component model enables a rich community of components to be shared and available for developers. For example, someone made a [WebVR controller component](https://github.com/richardanaya/aframe-webvr-controller) (HTC Vive) for A-Frame. Other interesting uses of A-Frame can be seen in their [examples](https://aframe.io/examples/) and in their [blog](https://aframe.io/blog/awoa-17/).

![A-Frame](/blog/uploads/2016-11/a-frame.jpg)

## Other Tools and Environments

Microsoft was also there talking about their enterprise and education efforts with VR, especially WebVR -- to leverage existing expertise in web technologies in enterprises and schools (just like what PhoneGap's strengths are).

[Vizor](http://vizor.io) is a web browser-based VR environment that allows you to [create](http://vizor.io/edit/), [explore](http://vizor.io/#featuredVR) and publish VR experiences.

![Vizor](/blog/uploads/2016-11/vizor.jpg)

[Unity](https://unity3d.com/learn/tutorials/topics/virtual-reality) is a cross-platform IDE that enables you to create regular games and VR games. IDEs like this can be a bridge for creating games in WebVR. Unity supports WebGL and VR, but not WebVR. A community user has bridged the gap (sound familiar?) and created a way to [export Unity games to WebVR](https://hacks.mozilla.org/2016/05/exporting-an-indie-unity-game-to-webvr/).

[AltspaceVR](http://altvr.com) is social VR, a virtual meeting space for VR users. In the video of the talk linked to above, Amber Roy walks us through how to embed WebVR (through manipulating nyan cat!) in the embedded browser component in the virtual space.

![AltspaceVR](/blog/uploads/2016-11/altspace-vr.jpg)

## What does this mean for PhoneGap?

We can embed WebVR experiences using PhoneGap, right now. The two major mobile operating systems (iOS and Android) already support WebGL -- iOS since iOS 8, and Google in Chrome. PhoneGap support for WebVR should be fine in Android 7.0 Nougat and above, anything below that will require the [Crosswalk plugin](https://crosswalk-project.org/documentation/cordova.html).

WebVR's goals are to make WebVR linkable, and embeddable everywhere there is a web browser -- and PhoneGap can provide extra value on top of that, in providing a bridge to device APIs when the WebVR content is wrapped with PhoneGap -- for apps in mobile app stores.

You can create a WebVR PhoneGap app using the template we provided (based off the WebVR Boilerplate):

    phonegap create hello com.example.hello HelloWorld --template phonegap-template-webvr

Don't forget to add the Crosswalk plugin beforehand if you are on an older Android (< 7) version:

     phonegap plugin add cordova-plugin-crosswalk-webview

Modify the `index.html` in the `www` folder to add a reference to `cordova.js` and you should be able to use PhoneGap plugins in your app.

![PhoneGap WebVR](/blog/uploads/2016-11/phonegap-webvr.jpg)

Find out more about WebVR and PhoneGap -- Joe Bowser from the PhoneGap team will be talking about [WebVR with PhoneGap](https://confoo.ca/en/yvr2016/session/webvr-getting-started-with-the-boilerplate) at [ConFoo](https://confoo.ca/en/yvr2016) in Vancouver, Canada Dec 5-7 2016.
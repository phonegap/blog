---
title: Easily Monetize PhoneGap Apps with Admob Plugins
date: 2016-08-09 00:00:00 Z
tags:
- Guest Post
- Community
author: Miquel Martin Goula
---

## Introduction

Let me introduce [AppFeel](http://appfeel.com/), a company based in Barcelona dedicated to mobile apps development, mostly focused in hybrid apps (Phonegap/Cordova). We have a great experience in PhoneGap development as can be seen by their [GitHub list of plugins](https://github.com/appfeel), among which, we can find [phonegap-admob](https://github.com/appfeel/phonegap-admob) to show Admob ads with [Phonegap Build](https://build.phonegap.com/), [cordova-admob](https://github.com/appfeel/admob-google-cordova) to show Admob ads with Phonegap/Cordova CLI projects, [cordova-plugin-analytics](https://github.com/appfeel/analytics-google) to track app events with Google Analytics or [cordova-plugin-analytics-adid](https://github.com/appfeel/analytics-google-adid) to also enable remarketing options for Google Analytics by using IDFA.

## Phonegap admob setup

Phonegap admob is a very useful plugin with [great and extensive documentation](https://github.com/appfeel/admob-google-cordova/wiki) which lets you **monetize your apps** by showing ads (banners and interstitials). To start using the plugin in a Phonegap app, place this line of code in `config.xml`:

```xml
<gap:plugin name="phonegap-admob" source="npm"/>
```

It can also be used in CLI interface:

```sh
phonegap plugin add cordova-admob
```

Or even in Cordova CLI:

```sh
cordova plugin add cordova-admob
```

To correctly show ads, the app should be designed in SPA, [single-page application](https://en.wikipedia.org/wiki/Single-page_application), so `index.html` is the only container for every screen in the app. On the contrary, every time the internal app browser loads a different page, every Phonegap plugin should be reloaded (including phonegap-admob).

First of all, the plugin needs to be configured. To do so, it should be done in your `deviceready` event:

```js
function onDeviceReady() {
    document.removeEventListener('deviceready', onDeviceReady, false);

    // Set AdMobAds options:
    admob.setOptions({
        publisherId:          "ca-app-pub-XXXXXXXXXXXXXXXX/BBBBBBBBBB",  // Required
        interstitialAdId:     "ca-app-pub-XXXXXXXXXXXXXXXX/IIIIIIIIII",  // Optional
        tappxIdiOS:           "/XXXXXXXXX/Pub-XXXX-iOS-IIII",            // Optional
        tappxIdAndroid:       "/XXXXXXXXX/Pub-XXXX-Android-AAAA",        // Optional
        tappxShare:           0.5                                        // Optional
    });
}

document.addEventListener("deviceready", onDeviceReady, false);
```

The plugin allows to integrate with [Tappx](http://www.tappx.com/en/?h=dec334d63287772de859bdb4e977fce6), a free ad exchange network. Anyway this is completely optional, and the ratio of ads requested to Tappx can be specified with tappxShare option which goes from 0 (no ads requested to Tappx) to 1 (all ads requested to Tappx).

The codes for publisherId and interstitialAdId can be obtained from [Admob](https://apps.admob.com/admob/signup) (in **Monetize area**, you should be able to create an app that you want to monetize and then create an ad unit):

![](/blog/uploads/ad-units.png)

## Banner ads

Now we are going to show banner ads. This is very easy. With this simple line of code you are going to be showing banner ads:

```js
admob.createBannerView();
```

Some options like adSize, bannerAtTop, overlap, etc. can be configured and could be placed as the first parameters of `createBannerView`. See a [complete description of options here](https://github.com/appfeel/admob-google-cordova/wiki/setOptions).

You could also specify the option `autoShowBanner` to false, in which case you should call `admob.showBannerAd(true)` when you would like to show the ads:

```js
admob.createBannerView({
    autoShowBanner: false
});

function callMeToShowBanners() {
    admob.showBannerAd(true);
}
```

If for some reason you wish to hide banner ads, you can always call `admob.showBannerAd(false)` and when you want to show them again, `admob.showBannerAd(true)`.

## Interstitial ads

Interstitial ads are a little bit tricky but nothing special at all. The easiest option is to call like this:

```js
admob.requestInterstitialAd({
    autoShowInterstitial: true
});
```

But the point here is that **interstitial ads take a while to load**. So in order to improve user experience, we are going to separate the loading process from the moment it is required to be shown. First of all, we are going to create a function that will be in charge of interstitial ads loading process. We are also going to make use of events in order to know whether we already have an interstitial ad pending to show or not. And finally we are going to have a function that will be in charge to show the interstitial:

```js
var isPendingInterstitial = false;
var isAutoshowInterstitial = false;

function prepareInterstitialAd() {
    if (!isPendingInterstitial) { // We won't ask for another interstitial ad if we already have an available one
        admob.requestInterstitialAd({
            autoShowInterstitial: isAutoshowInterstitial
        });
    }
}

function onAdLoadedEvent(e) {
    if (e.adType === admob.AD_TYPE.INTERSTITIAL && !isAutoshowInterstitial) {
        isPendingInterstitial = true;
    }
}

function onDeviceReady() {
    document.removeEventListener('deviceready', onDeviceReady, false);

    admob.setOptions({
        publisherId:          "ca-app-pub-XXXXXXXXXXXXXXXX/BBBBBBBBBB",
        interstitialAdId:     "ca-app-pub-XXXXXXXXXXXXXXXX/IIIIIIIIII",
    });

    document.addEventListener(admob.events.onAdLoaded, onAdLoadedEvent);
    prepareIntestitialAd();
}

document.addEventListener("deviceready", onDeviceReady, false);

function showInterstitialAd() {
    if (isPendingInterstitial) {
        admob.showInterstitialAd(function () {
                isPendingInterstitial = false;
                isAutoshowInterstitial = false;
                prepareInterstitialAd();
        });
    } else {
        // The interstitial is not prepared, so in this case, we want to show the interstitial as soon as possible
        isAutoshowInterstitial = true;
        admob.requestInterstitialAd({
            autoShowInterstitial: isAutoshowInterstitial
        });
    }
}
```

Then, when we want to show the interstitial ad we just need to call `showInterstitialAd()`; (let's say, when an event occured, a new screen is shown or even every 2 minutes with `setInterval(showInterstitialAd, 120000);`).

## Conclusion

Monetization is an essential part in the mobile app lifecycle, but it adds almost no value for the user. So the developer should be focused in developing great functionalities and make use of easy and fast ways to integrate monetizing strategies. PhoneGap makes it really easy by using these kinds of plugins that provide a really fast way to do so.

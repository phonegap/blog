---
title: Hipmob launches a Full In-App Helpdesk for Phonegap developers
date: 2014-02-19 08:40:04 Z
tags:
- Guest Post
- Video
author: Ayo Omojola
format: html
---

Hipmob, a powerful mobile SDK that allows mobile developers, startups, and businesses easily add a support portal to their apps, is happy to announce our newly released [PhoneGap plugin](http://www.hipmob.com/phonegap.html), and a promotion for PhoneGap developers.

We launched [Hipmob](http://www.hipmob.com/) over a year ago to solve our own problems. We were building gaming apps during YCombinator, and our rapid growth came with a metric ton of user emails. So we built Hipmob: it adds a searchable knowledgebase into your app, so your users can quickly find answers to frequent questions, and messaging (live chat or async) so you can talk to your users without them ever having to leave your app. This reduces the number of support emails, and makes it easier to communicate with your users.

Thousands of developers already use Hipmob ([see a few here](http://www.hipmob.com/gallery.html)), including several PhoneGap developers (check out [Epiq Access for iOS](https://itunes.apple.com/app/id694277147)).

![](https://phonegap.com/uploads/2014/02/hipmob.jpg)

Simply put, Hipmob makes it easy to communicate with customers inside your app. Your app users won't have to leave your app to get help, and they'll send you fewer support emails. If you sell a product or service inside your app, Hipmob is also a great way to answer questions and increase sales.

To get you started, here are links to the appropriate references:

* [Hipmob PhoneGap Reference](http://www.hipmob.com/phonegap.html)
* [Our Github Sample Project](https://github.com/Hipmob/hipmob-phonegap)

For folks who want to jump ahead to the code, you can get the source for a fully functional Phonegap app with a support portal integrated from Github at [https://github.com/Hipmob/hipmob-phonegap](https://github.com/Hipmob/hipmob-phonegap). For everyone else, we walk through the steps to getting live chat into your app below.

Getting started is pretty straightforward: you can install either the iOS or Android plugin using the standard **cordova** commands:

```sh
cordova plugin add https://github.com/hipmob/cordova-plugin-hipmob-ios.git
```

for iOS or

```sh
cordova plugin add https://github.com/hipmob/cordova-plugin-hipmob-android.git
```

for Android. The iOS plugin is only usable on an OSX computer, but the Android plugin can be used on any development computer with the Android dev tools. On some Windows computers you'll need to take extra steps to ensure the plugin is properly installed: you can clone the Hipmob Android plugin and install locally:

```sh
git clone https://github.com/hipmob/cordova-plugin-hipmob-android.git <directory location of plugin>
cd <root of application>
cordova plugin add &lt;directory location of plugin&gt;
```

Once the plugin is installed you will need to get setup at [https://manage.hipmob.com/](https://manage.hipmob.com/) and get an application ID to use with the Hipmob plugins. You can then call the plugin functions identically on both iOS and Android to open up a help desk search window:

```js
if( window.plugins && window.plugins.Hipmob ) {
  var hipmob_app_id = '<HIPMOB APPLICATION ID>';
  var Hipmob = window.plugins.Hipmob;

  Hipmob.openHelpdeskSearch(hipmob_app_id, {
    'title': 'Help',
    'query': 'Android',
    'user': '&lt;hipmob user id&gt;',
    'name': 'Femi',
    'email': 'femi@hipmob.com',
    'context': 'shopping for shoes',
    'location': 'At home'
  });
} else {
  alert('Hipmob plugin not available/ready.');
}
```

This will open a simple search window that searches through the documents indexed by Hipmob, and lets the user browse through the documents. A similar call lets your app's user open a specific help desk document:

```js
if( window.plugins && window.plugins.Hipmob ) {
  var hipmob_app_id = '&lt;HIPMOB APPLICATION ID&gt;';
  var helpdesk_article_id = '&lt;helpdesk article id&gt;';
  var Hipmob = window.plugins.Hipmob;

  Hipmob.openHelpdeskArticle(hipmob_app_id, helpdesk_article_id, {
    'title': 'Help',
    'user': '&lt;hipmob user id&gt;',
    'name': 'Femi',
    'email': 'femi@hipmob.com',
    'context': 'shopping for shoes',
    'location': 'At home'
 });
} else {
  alert('Hipmob plugin not available/ready.');
}
```

This can be used for context-sensitive help. Finally, sometimes you just want your user to be able to chat with you. Hipmob's got you covered:

```js
if( window.plugins && window.plugins.Hipmob ) {
  var hipmob_app_id = '&lt;HIPMOB APPLICATION ID&gt;';
  var Hipmob = window.plugins.Hipmob;

  Hipmob.openChat(hipmob_app_id, {
    'title': 'Help',
    'user': '&lt;hipmob user id&gt;',
    'name': 'Femi',
    'email': 'femi@hipmob.com',
    'context': 'shopping for shoes',
    'location': 'At home'
  });
} else {
  alert('Hipmob plugin not available/ready.');
}
```

At Hipmob, we’re super responsive to our developer community, and we’re always looking for feedback that helps us improve the product. If you have ideas for support or communication products you’d like to see, or you have questions or anything else about Hipmob, please just drop us a line at [ayo@hipmob.com](mailto:ayo@hipmob.com).

{% include video.html id="ZOLpeJoYdEM" %}

[Start a Hipmob free trial here](http://hipmob.com/helpdesk/hd1.html)

> Guest Post by Ayo Omojola
> Ayo Omojola is CEO & co-founder of [Hipmob.com](http://hipmob.com). Hipmob is a leading provider of CRM and customer support software to mobile businesses and app developers and is an alumnus of YCombinator (W'12). Before this, he's designed and helped develop mobile apps and services since 2008\. Reach him at ayo(at)hipmob.com, or follow me on twitter at [@ay_o.](http://twitter.com/ay_o)

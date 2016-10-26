---
title: PhoneGap Push Plugin 1.8.0
date: 2016-07-26 00:00:00 Z
tags:
- Release
- News
author: Suraj Pindoria
---

We haven't done a post regarding phonegap-plugin-push for awhile, but we have just
released version 1.8.0! Along with bug fixes and general improvements we have also
introduced support for the browser platform. To test this out you can use the PhoneGap
push template to get set up quickly.

```bash
$ phonegap create myApp --template push
```

Currently the push plugin will on work on Chrome 49+ and Firefox 46+. Once the platform
is added, you will need to serve it in order to load it from the browser.

```bash
$ phonegap platform add browser
$ phonegap serve
```

Open your browser to `localhost:{port}` where `{port}` is specified by the output of the serve
command. When the page loads it will register a subscription to push notifications and output
the devices Registration ID in the developer console. From here you can test sending a push
and watch as it is sent to the browser.

MacOS:

```bash
$  phonegap push --deviceID APA91bE1MmeTc92igNoi5OkDWUV --service gcm --payload '{ "data": { "title": "Hello", "message": "World"} }'
```

Windows:

```bash
$ phonegap push --deviceID APA91bE1MmeTc92igNoi5OkDWUV --service gcm --payload "{ \"data\": { \"title\": \"Hello\", \"message\": \"World\"} }"
```

Just replace the deviceID with the one that is output in the browser. For more in depth
documentation follow [this](http://docs.phonegap.com/tutorials/develop/push-notifications/)
guide. Give this a try and let us know what you think!

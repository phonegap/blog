---
title: Introducing Sleight
date: 2010-01-20 00:00:00 Z
categories:
- app
author: Andrew Lunny
link: http://blogs.nitobi.com/andrew/2010/11/28/introducing-sleight
status: publish
type: post
format: html
---

Some time in October I threw together _Sleight_ - a tiny little [node.js](http://nodejs.org) server for use in developing [PhoneGap](http://www.phonegap.com) apps (it's not coupled with PhoneGap, but PhoneGap's the ideal use case).

_Sleight_ is basically just an if statement: for each request to the server, if the resource is a file on the server, then serve it as the response. If it's not there, proxy a response back from some remote server. This lets you develop as though you're working on a PhoneGap app (on the `file://` protocol, where cross-origin XHRs are allowed) from an HTTP server. You can then run your app from a server locally and open it in a mobile browser, while keeping the cross-origin requests working.

Let's get a quick demo going. Create a `sleight-demo` directory, and create an `index.html` file with this text:

```html
<body>
  <div id="latest-tweet"></div>
</body>
```

```js
var server = window.location.protocol == "file:" ?
    "http://search.twitter.com" : "";

window.addEventListener('load', function () {
  function handleResponse(text) {
    var match = JSON.parse(text).results[0].text;
    document.getElementById('latest-tweet').innerHTML = match;
  }

  var url = server + "/search.json?q=phonegap";
  var req = new XMLHttpRequest();
  req.onreadystatechange = function () {
    if (this.readyState == 4) {
      if (this.status == 200 || this.status == 0) {
        handleResponse(this.responseText);
      } else {
        console.log('something went wrong');
      }
    }
  }

  req.open('GET', url, true);
  req.send();
})
```

Open that in Safari or the like from your hard drive; ensure the file is run from the `file://` protocol. Good.

Now, assuming you've installed _Sleight_, enter the following command in your `sleight-demo` directory:

```sh
$ sleight target=search.twitter.com
Listening on port 8088 @ ${insert your current timestamp here}
```

Now navigate to `http://localhost:8088/` in Safari. The tweet should still be present (or maybe there'll be a new tweet by this point). And check your Sleight log:

```sh
Static file served from: / @ timestamp
Remote request to search.twitter.com:80/search.json?q=phonegap @ timestamp
Remote request to search.twitter.com:80/favicon.ico @ timestamp
```

Much success and joy ensues. And since you're now running an HTTP server, you can easily access the page form your mobile device, so all of you PhoneGap testing can be done without any installation, or re-installation.

Right now this is all Sleight does, but there are some other, PhoneGap-specific features we'd like to add in the future - hooks for logging, debugging, and testing in particular.

Oh yeah, and you can get the _Sleight_ source code at [Github](http://github.com/alunny/sleight), as ever.

p.s. If you were hoping _Sleight_, in reference to _sleight of hand_, meant there would be any magic, I sincerely apologize. Here is the best I can manage:

[› Visit the original post](http://blogs.nitobi.com/andrew/2010/11/28/introducing-sleight)

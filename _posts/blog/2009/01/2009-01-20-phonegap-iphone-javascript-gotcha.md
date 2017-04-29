---
title: PhoneGap-iPhone-JavaScript Gotcha
date: 2009-01-20 00:00:00 Z
categories:
- app
author: Andrew Lunny
link: http://blogs.nitobi.com/andrew/2009/07/28/phonegap-iphone-javascript-gotcha
status: publish
type: post
format: html
---

We’ve recently started doing training for [PhoneGap](http://www.phonegap.com), our open-source mobile web development that’s taking the world by storm. In preparation for the training, I threw together a little Twitter client app called Pigeon (the code is [available on GitHub](http://github.com/alunny/Pigeon)) – it’s currently iPhone only but will be ported everywhere else in the near future.

PhoneGap is a great abstraction for working with different devices with a minimum of effort, but you can’t completely avoid the particularities of specific devices. I’m gonna detail some of those quirks on this blog, so users of Google can avoid my mistake. The first comes from evaluating JSON.

## Gotcha #1: Evaluating JSON

One of the great things about PhoneGap is that you can interact with remote web services through XmlHttpRequests. Unlike XHRs in a browser, which require the same origin server (an XHR from nitobi.com can’t access apple.com), XHRs in a native app can go wherever they please (you can also use this functionality in Safari on the desktop, if you’re running JavaScript from the file system). This is great for interacting with web services – and Pigeon, a Twitter app, is a perfect example of this.

Twitter has a [terrific API](http://apiwiki.twitter.com/) that lets you access huge amounts of data in a variety of formats. For JavaScript code, JSON is the most useful – rather than writing any complicated parsing code, you can just evaluate the response and access it as a JavaScript object. Here is the [public timeline in JSON](http://twitter.com/statuses/public_timeline.json).

Twitter returns two different kinds of JSON responses: objects and arrays of objects. For example, here’s the JSON representation of [this tweet](http://twitter.com/phonegap/status/2782434499):

```js
{
  "truncated":false,
  "text":"mobile orchard interviews founders of phonegap @rob_ellis and @sintaxi http://bit.ly/E0ZOG",
  "user":{
    "following":true,
    "description":"",
    "screen_name":"phonegap",
    "utc_offset":-28800,
    "favourites_count":1,
    "profile_text_color":"323232",
    "statuses_count":248,
    "profile_background_image_url":"http://static.twitter.com/images/themes/theme1/bg.gif",
    "notifications":false,
    "profile_link_color":"224467",
    "profile_background_tile":false,
    "created_at":"Sun Aug 03 23:58:00 +0000 2008",
    "url":"https://phonegap.com",
    "name":"phonegap",
    "profile_background_color":"CDCDCD",
    "protected":false,
    "verified":false,
    "profile_sidebar_fill_color":"FFFFFF",
    "time_zone":"Pacific Time (US &amp; Canada)",
    "followers_count":1852,
    "profile_sidebar_border_color":"FFFFFF",
    "profile_image_url":"http://s3.amazonaws.com/twitter_production/profile_images/61102217/icon_iphone_wo_glare_normal.png",
    "location":"Vancouver BC",
    "id":15715860,
    "friends_count":13
  },
  "in_reply_to_status_id":null,
  "in_reply_to_user_id":null,
  "created_at":"Wed Jul 22 18:24:10 +0000 2009",
  "favorited":false,
  "in_reply_to_screen_name":null,
  "id":2782434499,
  "source":"<a href=''>Tweetie</a>"
}
```

If you copy that code into a script tag and place <code>var foo =</code> before it, then foo is a JS object representing that Tweet. If you request multiple tweets from Twitter’s API, such as that public timeline linked above, you get multiple objects like this in an array. Here’s a truncated version of what that would look like:

```js
[
  {"tweet":"first"},
  {"tweet","second"},
  {"tweet","third"}
]
```

Place `var bar =` before that in your script tag, and bar is have an array of three tweets. So far so good, no?

Since this data is coming remotely, though, we can’t just stick our variable declarations in and run (well, you could, but it would kinda be a waste of time). So instead, we perform our XHR to get the data from Twitter, and then on completion we use the magic <code>eval</code> (sounds like “evil”) JS function to turn the response into a JavaScript object. Here’s some relevant code from Pigeon that gets all of your friends’ tweets, turns them into a JS array, and puts them onto the screen:

```js
var load_tweets = function(container_id, user, passw) {
  x$("#login_screen").setStyle("display", "none");
  x$(container_id).xhr("http://www.twitter.com/statuses/friends_timeline.json", {
    callback: function() {
      render_tweets(container_id, this.responseText);
    },
    headers: [{
      name: "Authorization",
      value: "Basic " + btoa(user + ":" + passw)
    }]
  });
}
var render_tweets = function(container_id, new_tweets) {
  var tweetstream = eval(new_tweets);
  var i = 0;
  for (i = 0; i & lt; tweetstream.length; i++) = "" { = "" & gt;
    x$(container_id).html("bottom",
      format_tweet({
        profile_image: tweetstream[i].user.profile_image_url,
        user_name: tweetstream[i].user.name,
        tweet_text: tweetstream[i].text
      }));
  }
}
```

The `load_tweets` function calls XUI's `xhr` function, which on its callback calls the `render_tweets` function, passing it the magic "this.responseText" string, which is the response from the Twitter API. The `render_tweets` function passes the response to `eval()`, which spits back an array that's looped through, outputing nicely formatted tweets to the container div.

So far so good, no? This works fine when Twitter is sending back an array, but fails, silently, when we receive a curly-braced object. Thankfully, it fails in Safari on your desktop too, where you can get a useful error message:

```js
var foo = eval("{'car':'dog','boat':'fish'}")
// SyntaxError: Parse error
var foo = eval("[{'car':'dog','boat':'fish'}]")
// undefined
```

Turns out, `eval()` works for arrays but nor for objects. The vagaries of the `eval()` implementation are beyond the scope of this already exhausting post: the behaviour is counter-intuitive, but is present everywhere I've tested it (Safari, Firefox, IE).

A thoughtful, conscientious developer will tell you not to use `eval()`, to instead download or implement a JSON parser that will avoid this hassle altogether, and use that instead of `eval()`. A lazy developer, who is more worried about the size of his code than performance and is getting data from a very trusted source, will use the immediate workaround:

```js
tweet_response = eval("[" + new_tweet + "]")[0];
```

… which does the job with only 15 extra characters - you could do it nine times in a tweet and still have space to say bye.

Next time: avoiding stack overflows when your callbacks' callbacks aren't calling their callbacks.

**Note**: Re-reading this while de-wordpressing my blog: it's fairly rank with errors, but I'm leaving it as is for intellectual honesty's sake, I suppose. Eval fails with curly braces because it assumes they contain a code block, rather than an object literal expression - you can wrap the JSON object in brackets to have it evaluate as an expression (to an object). Use `JSON.parse` where available natively, although it's not very reliable on the iPhone.

[› Visit the original post](http://blogs.nitobi.com/andrew/2009/07/28/phonegap-iphone-javascript-gotcha)

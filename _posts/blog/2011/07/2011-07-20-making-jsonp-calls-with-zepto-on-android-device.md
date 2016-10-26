---
title: Making JSONP calls with Zepto on Android Device
date: 2011-07-20 00:26:58 Z
categories:
- app
author: Tim Kim
status: publish
type: post
format: html
---

## Introduction

There has been a lot of posts about getting JSONP calls to work on android and the troubles thereof. From what I can tell, there's a great deal of confusion of what settings to set, the need for status codes, synch or asynch etc. So I hope in this tutorial to show that making JSONP calls is actually very easy and very do-able on android device.

Here is a link to my git repo to find all of the code necessary for this tutorial: [https://github.com/timkim/PhoneGap_zepto_jsonp_sample](https://github.com/timkim/PhoneGap_zepto_jsonp_sample)

## Step One: Review the JSONP message being sent from the server

Instead of looking at the client code right away, we're going to start right from the server perspective. In the repo, you'll find a file called simplejson.php in the server folder that serves out some data.

```php
<?php
  header('content-type: application/json; charset=utf-8');
  $data = array(1, 2, 3, 4, 5, 6, 7, 8, 9);</code></p>
  echo $_GET['callback'].'('.json_encode($data).')';</code></p>
?>
```

Basically what this file is doing is serving out json by setting the content-type to application/json - that way a client knows it's getting json back from the server when it makes a request to this file. From there, we define a simple array that contains the numbers 1-9 and then encode this number array as a json object using json_encode($data). Pretty simple so far.

The hardest thing to wrap your head around is this issue of the `$_GET['callback']` being prepended to the json encoded data. In php, the `$_GET['callback']` serves as a way to access the key/value pair in the query string from the url request string. For example, if a client requests this url: [http://nitobi.com/timkim/simplejsonp.php?callback=jsonp1](http://nitobi.com/timkim/simplejsonp.php?callback=jsonp1) the server will return `jsonp1([1,2,3,4,5,6,7,8,9])`. Notice how returned `json` is prepended with `jsonp1` when `callback=jsonp1` in our request string.

## Step Two: Making the JSONP call using zepto

<p>On our index.html page, we're going to make the ajax call to our simplejson.php file to get the data. Zepto provides a very handy ajax function aptly named ajax. For the purpose of this example, all we are going to use are the url and success parameters of the ajax function call.

```js
$.ajax({
  url:'http://nitobi.com/timkim/simplejsonp.php?callback=?',
  success:function(data){
    $('#main').html(data);
  }
});
```

One important thing to note about setting the url and jsonp call is this little trailing =? at the end of the url. Zepto auto-creates a callback function when you add the =? to the end of an url. If you look back at the previous step, you'll see jsonp1([1,2,3,4,5,6,7,8,9]) being returned. Basically, every time you make a jsonp call with zepto, it creates a new function handle by incrementing the count by one. So, the first request has the url string [http://nitobi.com/timkim/simplejsonp.php?callback=jsonp1](http://nitobi.com/timkim/simplejsonp.php?callback=jsonp1) and the second will be [http://nitobi.com/timkim/simplejsonp.php?callback=jsonp2](http://nitobi.com/timkim/simplejsonp.php?callback=jsonp2). If you want to know exactly how this function works, I suggest taking a look at the source: [https://github.com/madrobby/zepto/blob/master/src/ajax.js](https://github.com/madrobby/zepto/blob/master/src/ajax.js) lines 36-45 ish

If you want to ignore the above, the short version is put a =? at the end of your url request string and zepto will take care of the rest.

Once our json has come back from the server, the success callback will be fired. You don't have to worry about status codes, cross domain issues, making your own callback, etc. Just use this success callback! In this example, we're just going to populate a div called main with the results of our data.

Now to see what it looks like:

[![](/uploads/2011/07/screenshot.png)](/uploads/2011/07/screenshot.png)

Perfect!

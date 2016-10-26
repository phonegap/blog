---
title: Image Caching with the HTML5 Canvas
date: 2009-09-24 22:45:05 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2009/09/24/image-caching-with-the-html5-canvas/
status: publish
type: post
format: html
---

Lately I have been working on an iPhone app ( using PhoneGap of course )  and needed to implement image caching on the client with javascript.

I am already using an SQLite database in mobile safari, so I decided I could store images in Base64 in the DB.  I was able to load the binary image data using XHR, but could not correctly encode it to base64 in javascript.

Exploring another path, I found that there is a method of the [HTML5 Canvas toDataURL();](http://stackoverflow.com/questions/934012/get-image-data-in-javascript)

So I wrote this to download the image, instead of my XHR method:

```js
ImageCacheManager.prototype.fetchImage = function(url)
{
  var alias = this;
  var img = new Image();
  img.onload = function()
  {
    alias.onImageLoaded(this);
  };
  img.src = url;
}
```

Then this to handle the loaded image and cache it:

```js
ImageCacheManager.prototype.onImageLoaded = function(img)
{
  var canvas = document.createElement("canvas");
  canvas.width = img.width;
  canvas.height = img.height;
  var ctx = canvas.getContext("2d");
  ctx.drawImage(img,0,0);
  var dataURL = canvas.toDataURL();
  this.cacheImageData(img.src, dataURL);
}
```

To keep things short I have excluded the DB sections, I always check if I have an image cached already before I fetch one, and always write it to the DB when I do fetch.  If an image is retrieved from the DB it can simply be written to the img.src as is.

I foresee all kinds of uses for this, like a javascript based image editor, or a water-marking script (you can also draw text on the canvas before you pull out it's bits …)

[› Visit the original post](http://blogs.nitobi.com/jesse/2009/09/24/image-caching-with-the-html5-canvas/)

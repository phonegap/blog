---
title: PhoneGap TextMate Bundle
date: 2010-11-22 22:55:35 Z
categories:
- app
author: Anis Kadri
link: http://blogs.nitobi.com/anis/?p=73
status: publish
type: post
format: html
---

Dear TextMate users/PhoneGap developers,

I put together a little bundle for your favorite editor. You should now be able to easily get code snippets right in your editor.

You can find it [here](https://github.com/imhotep/PhoneGap.tmbundle)

Installation instructions are [here](http://manual.macromates.com/en/bundles#installing_a_bundle)

How to use:

Type `accel.wa` and press _Tab_ and you should get:

```js
function onSuccess(acceleration) {
  alert('Acceleration X: ' + acceleration.x + 'n' +
        'Acceleration Y: ' + acceleration.y + 'n' +
        'Acceleration Z: ' + acceleration.z + 'n' +
        'Timestamp: '      + acceleration.timestamp + 'n');
};

function onError() {
  alert('onError!');
};

var options = { frequency: 3000 };  // Update every 3 seconds

var watchID = navigator.accelerometer.watchAcceleration(onSuccess, onError, options);
```

Now all you have to do is modify the callbacks to suit your needs! Almost every API method should be present.

Feedback always welcome!

[› Visit the original post](http://blogs.nitobi.com/anis/?p=73)

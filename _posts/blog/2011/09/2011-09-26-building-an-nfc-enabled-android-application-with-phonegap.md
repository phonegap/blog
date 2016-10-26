---
title: Building a NFC enabled Android application with PhoneGap
date: 2011-09-26 18:24:42 Z
categories:
- Plugins
author: Kevin Griffin
status: publish
type: post
format: html
tags_old:
- nfc
- phonegap
- plugins
---

One of the most powerful things about PhoneGap is its “Plugin” architecture. If you can write it in native code, you can make it into a plugin.

Near Field Communications (NFC) is a short range, zero configuration, wireless communication. NFC transactions typically happen between a passive device (tag) and an active device (in our case an Android powered phone). The phone generates an RF field which provides enough power to read and write data from the tag. Peer-to-peer communication can also occur between two powered devices (two phones).

## Build a Project

If you don’t already have a PhoneGap Android project there a couple of ways to get started:

* [PhoneGap: Get Started Guide](http://www.phonegap.com/start#android) and
* [PhoneGap Start Project](https://github.com/phonegap/phonegap-start)

## Checkout phonegap-nfc

Once you have a project up and running you will need to get your hands on either the phonegap-nfc plugin source or distributable.

* [phonegap-nfc source](https://github.com/chariotsolutions/phonegap-nfc)
* [phonegap-nfc.js 0.2.0](https://github.com/downloads/chariotsolutions/phonegap-nfc/phonegap-nfc-0.2.0.js)
* [phonegap-nfc.jar 0.2.0](https://github.com/downloads/chariotsolutions/phonegap-nfc/phonegap-nfc-0.2.0.jar)

## Add phonegap-nfc to your project

The phonegap-nfc.jar needs to be placed in your projects lib/ directory and the phonegap-nfc.js needs to be placed in your www/assets directory.

Next you need to update you plugins.xml to include the phonegap-nfc plugin:

```xml
<plugin name="NfcPlugin" value="com.chariotsolutions.nfc.plugin.NfcPlugin"/>
```

And update your index.html to include `phonegap-nfc.js`

```html
<script type="text/javascript" charset="utf-8" src="phonegap-nfc.js"></script>
```

Lastly you need to update your AndroidManifest file with:

```xml
<uses-permission android:name="android.permission.NFC" />
<uses-feature android:name="android.hardware.nfc" android:required="true" />
<uses-sdk android:minSdkVersion="10" />
```

## Phones and Tags

Now that we have the housework out the way, we really should scan something.

At this point you’ll need some hardware to test you application. For our phone we used the [Nexus S](http://www.google.com/nexus/) (we bought ours from Amazon) and for tags we've used [Identive NFC](http://www.identivenfc.com/) and [TagAge](http://www.tagage.net/) - there are many vendors so shop around and ensure you know what you are getting when you order. Specifically make sure they are writable and can take NDEF messages.

However you can proceed without any hardware. One option is to use the [FakeTagsActivity](http://developer.android.com/resources/samples/NFCDemo/src/com/example/android/nfc/simulator/FakeTagsActivity.html) from the good Google folks, as used in their NFC Demo.

You can also look at using [Open NFC](http://www.open-nfc.org/nfcc_simu.html) to simulate NFC tags with the Android Emulator.

### A note on tags

If you can get them pre-formatted it will make your transition into the world of reading NFC tags a lot easier. Either way you are going to want to make an app to write tags too :)

## Scan some tags!

If you have some pre-formatted tags you can start by adding in a simple NDEF Listener into your application, if your tags aren’t formatted you can jump to the ‘writing’ section.

### Wait, what is NDEF?

NDEF stands for, NFC Data Exchange Format (NDEF). It is a specification put together by the NFC Forum for communicating via a defined common format. It provides specifications for transmitting things like mime type objects, plain text, ‘Smart Posters’ and URLS.

### The first listener

All interactions in the `phonegap-nfc` plugin are event based. You can register for one (or more) ‘listeners’ and the plugin will return the corresponding event when appropriate. See the README for a full list of the available listeners.

The definition of the NDEF listener looks like this:

```js
nfc.addNdefListener(callback, [onSuccess], [onFailure]);
```

For our first implementation we will just log the events. Place the following block in your existing `ondeviceready` callback.

```js
nfc.addNdefListener(
  function() {
    document.write("Found an NDEF formatted tag");
  },
  function() {
    console.log("Success.");
  },
  function() {
    console.log("Fail.");
  }
);
```

Note: We are inlining all our functions, you may want to arrange your code differently.

Not terribly useful, but a good start. In order to make the implementation slightly more useful we are going to swap out our vanilla ‘NDEF Listener’ for the ‘Mime Type Listener’. The reason we opt to use the mime listener is that it allows you to generate a 1:1 relationship between your tag and your application. If you format your tags with a ‘unique’ mime type, then only your app will start when you scan the tag avoiding the annoying ‘select which application you want to complete this task with’ screen. More importantly you won’t appear under any generic scans for Tag/NDEF, which has the potential to be annoying for users. [See the NFC video from Google IO to get a better understanding of why this is good.](http://www.youtube.com/watch?v=49L7z3rxz4Q)

The definition for the mime type listener looks like:

```js
nfc.addMimeTypeListener(mimeType, callback, [onSuccess], [onFailure]);
```

Our implementation looks like:

```js
nfc.addMimeTypeListener(
  "my/mimeType",
  parseTag,

  function() {
    console.log("Success.");
  },
  function() {
    console.log("Fail.");
  }
);
```

Note that the second argument isn’t inlined. Since we are going to be doing some work here I broke it out into it’s own named function.

```js
function parseTag(nfcEvent) {
  var records = nfcEvent.tagData;

  for (var i = 0; i < records.length; i++) {
    var record = records[i],
    p = document.createElement('p');
    p.innerHTML = nfc.bytesToString(record.payload);
    display.appendChild(p);
  }
}
```

Our `parseTag` function is not doing anything too special, it makes some bold assumptions though. Specifically that the tag was formatted in such a manner that calling `nfc.bytesToString` will return text.

This simple implementation will read a tag formatted with a specific mime type, and attempt to display the data stored on the tag.

### What happens when our app isn’t running?

One of the great things about NFC is the ability for this unique matching of mime type to application to open your app whenever the device detects a tag with our mime type. To see this in action you need and an ‘intent fitler’ to your android manifest.

```xml
<intent-filter>
  <action android:name="android.nfc.action.NDEF_DISCOVERED" />
  <data android:mimeType="my/mimetype" />
  <category android:name="android.intent.category.DEFAULT" />
</intent-filter>
```

## Write an NDEF message

We’ve talked a lot about reading specific mime types from tags, but how do we get them there? We can re-use some of the code we already have. We can set a listener for any ‘NDEF’ formatted tag, then we can write an NDEF message with our mime type to it.

Lets start with the NDEF listener again

```js
nfc.addNdefListener(
  writeTag,

  function() {
    console.log("Success.");
  },
  function() {
    console.log("Fail.");
  }
);
```

<p>Now the writeTag implementation:</p>

```js
function writeTag(nfcEvent) {
  var mimeType = "my/mimetype";
  var payload = "super secret data";
  var message = nfc.mimeMediaRecord(mimeType, nfc.stringToBytes(payload));

  nfc.write(
    [message],
    function () {
      console.log("success");
    },
    function (reason) {
      console.log("fail");
    }
  );
}
```

## In progress

The phonegap-nfc plugin is very much in its infancy, there may be bugs or things that are just flat out wrong. Our repo is always open, we love issues with examples and we love pull requests even more!

We are working on adding BlackBerry’s NFC support in OS7 to the plugin, as well as expanding the Android functionality.

## Going further

There are more complete examples we have used alongside presentations; [reader](https://github.com/don/phonegap-nfc-reader), [writer](https://github.com/don/phonegap-nfc-writer), [peer-to-peer sharing](https://github.com/don/phonegap-p2p) and [RockPaperScissors (peer-to-peer game)](https://github.com/don/rockpaperscissors) as always we appreciate feedback, code even more!

## Resources

* [phonegap-nfc plugin](https://github.com/chariotsolutions/phonegap-nfc)
* [reader](https://github.com/don/phonegap-nfc-reader)
* [writer](https://github.com/don/phonegap-nfc-writer)
* [peer-to-peer sharing](https://github.com/don/phonegap-p2p)
* [RockPaperScissors](https://github.com/don/rockpaperscissors)

Kevin is a consultant with Chariot Solutions where he spends his time solving mobile related problems. He creates mobile solutions using native platforms, PhoneGap and the web. Oh, and he likes dogs.

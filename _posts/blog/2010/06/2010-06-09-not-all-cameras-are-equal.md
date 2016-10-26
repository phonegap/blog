---
title: Not all cameras are equal
date: 2010-06-09 18:04:30 Z
categories:
- app
author: Joe Bowser
link: http://blogs.nitobi.com/joe/2010/06/09/not-all-cameras-are-equal/
status: publish
type: post
format: html
---

Recently, the way we were creating a camera and using it broke. I'm not sure why it broke, but I decided to say screw it and to use the Camera Intent in Android, because that's what you're supposed to do on Android anyway. This is what most Twitter Applications use, and since Twitter Apps are probably the most used application on Android, I figure if it's good enough for them, it's good enough for me…

Oh how wrong I was!!!

I added the new intent code, and I tested it on four phones. I tested it on the HTC EVO 4G that I received from Google IO, the Nexus One, the Motorola Milestone with the official Telus Firmware (with camera), the HTC Dream with stock Android 1.6 and the Rogers HTC Magic with Android 1.5 and the 9/11 update. Basically, everything worked but the Rogers HTC Magic. The thing is that once you use intents, you are relying on the OEMs to write a good enough Android Camera Application for you to get a picture from. This may be good for a Google blessed image, or a stable HTC phone like the EVO, but it's clear that on certain phones from certain providers, that there may be some issues.

I'm certain that there's phones in the wild that have broken cameras, and it'd be good to find out which phones have broken cameras. If people could test on these phones (with Canadian carriers next to them), that would be greatly appreciated:

* HTC Hero (Telus)
* LG EVE (Rogers)
* Motorola DEXT (Bell)
* Motorola Quench (Rogers)
* Motorola Backflip (Telus)
* Samsung Galaxy (Bell/Rogers)
* Acer Liquid E (Rogers)
* Xperia X10 (Rogers)

Those are the phones that I know are in the wild in Canada. I'm sure there's more than this in other countries, namely in the United States, but this is a good cross-section of devices from a handful of manufacturers who may have their own customized camera applications. I've exempted test devices from this post, because I don't think it's fair to take a broken firmware and say "Hey, the Camera Doesn't work!". However, the HTC Magic should work, and it's disappointing that it doesn't, since this breaks not only PhoneGap's camera capability, but anything that uses that intent. Hopefully in the future, Android cameras will be more reliable.

[› Visit the original post](http://blogs.nitobi.com/joe/2010/06/09/not-all-cameras-are-equal/)

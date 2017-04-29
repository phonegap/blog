---
title: PhoneGap Build Public Plugin Repository Shutting Down
date: 2016-10-13 10:00:00 Z
categories:
- build
tags:
- PhoneGap Build
author: Brett Rudd
---

We announced the deprecation of the public repository on PhoneGap Build in this this 
[blog post](https://phonegap.com/blog/2015/09/04/public-plugin-deprecation-on-build/) 
from September, 2015. That was over a
year ago and in that time no public plugins (including core Cordova plugins) have been added to or updated in that
repository. So we are happy to announce that this public repository will be **removed on 
November 15th, 2016**!

**This includes all public plugins AND Cordova / PhoneGap core plugins.**

Users will still be able to upload private plugins and **these plugins will be the only plugins available from the 
PhoneGap Build (source=pgb) repository.**

As part of the process of removing this repository we have added reminders to apps that are including public
plugins from the PhoneGap Build repository.  Please be sure to update these apps to use plugins
from npmjs.com or git repositories before November 15th, 2016, as after this time those apps will not be built.

To help users we are updating plugins with deprecation notices with the plugins location on npm. If you 
know a plugin's location on npm then please submit a suggestion on the bottom of the plugin details page.

For more information read the [documentation](http://docs.phonegap.com/phonegap-build/configuring/plugins/).

As usual, if you have questions or issues, [don't hesitate to let us know](https://forums.adobe.com/community/phonegap/build), talk to us on twitter at @phonegapbuild or yell at me at @brettrudd

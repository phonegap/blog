---
title: PhoneGap Xcode 4 Template (beta)
date: 2011-05-05 23:57:23 Z
categories:
- app
author: Shazron Abdullah
link: http://blogs.nitobi.com/shazron/2011/05/05/phonegap-xcode-4-template/
status: publish
type: post
format: html
---

![](http://blogs.nitobi.com/shazron/wp-content/uploads/2011/03/apple-xcode-icon.png)[Download the beta1.2 package here](http://blogs.nitobi.com/shazron/wp-content/uploads/2011/05/PhoneGapInstaller_Xcode4_beta1.2.pkg.zip).

View the screencast below (best in full-screen, in HD).

## Xcode 4 template specs are undocumented and buggy. So, there are issues:

* We cannot automatically include the "www" folder in the template - the user has to add it in manually (a quick drag and drop). I added in checks and warnings if users try to run the app without adding this in.
* Some files, like .h and the -Info.plist file, are included in the 'Copy Bundle Resources' build phase by the template. No biggie during run-time, but for those with OCD they will want to remove these from the Build Phase (if only to get rid of the warning).
* Because Xcode 4 does not expand tildes (~), I cannot add a reference to the PhoneGap.framework in the user's home folder, so I added it to a shared location /Users/Shared which has r+w permissions for everyone (the common folder /Library/Frameworks needs admin privileges). It was added here so users without admin privileges can still use PhoneGap.framework, and by extension, the Xcode 4 Template.

## RELEASE NOTES

* beta1 - Initial release
* beta1.1 - Bug fix for [issue #81](https://github.com/phonegap/phonegap-iphone/issues/81) (moved framework from /Users/Shared/Library to /Users/Shared/PhoneGap)
* beta1.2 - Made /Users/Shared/PhoneGap writable to everyone

[› Visit the original post](http://blogs.nitobi.com/shazron/2011/05/05/phonegap-xcode-4-template/)

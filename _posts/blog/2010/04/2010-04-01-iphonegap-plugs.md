---
title: iPhoneGap Plugs
date: 2010-04-01 16:57:29 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2010/04/01/iphonegap-plugs/
status: publish
type: post
format: html
---

Okay, in your phonegap application in XCode, ( Without EVER having to touch the PhoneGapLib )

1. right click the plugins folder and select Add/NewFile/ObjectiveCClass
1. Call your new class : TestPlug
1. Paste the following code into the .m + .h files:

  ```objc
  // In the .h file …..
  # import
  # import "PhoneGapCommand.h"
  @interface TestPlug : PhoneGapCommand {
  }
  *   (void)doit:(NSMutableArray_)arguments withDict:(NSMutableDictionary_)options;
  @end
  ```

  ```objc
  // in the .m file

  # import "TestPlug.h"

  @implementation TestPlug

  *   (void)addThemUp:(NSMutableArray_)arguments withDict:(NSMutableDictionary_)options

  {

  NSUInteger argc = [arguments count];

  int total = 0;

  for(int n = 0; n < argc; n++)

  {

  total += [[ arguments objectAtIndex:n] intValue];

  }

  NSString* retStr = [ NSString stringWithFormat:@"alert("%d");",total];

  [ webView stringByEvaluatingJavaScriptFromString:retStr ];

  }

  @end
  ```

1. In your JS code, somewhere after deviceready, call your command like this.

  ```js
  PhoneGap.exec("TestPlug.addThemUp",1,2,3,4);
  Build and run!
  ```

Note the structure of the PhoneGap.exec call

1. a command name : `TestPlug`
1. a method name : `addThemUp`
1. a variable length list of arguments

Next time, I'll get into passing objects via the 'options' object.

If you have a compelling plug-in you want to share, you can [fork my repo](http://github.com/purplecabbage/PhoneGap-Plugins) for plugins and send me a pull request.

If your plugin makes sense on multiple devices, and it is implemented with standards in mind, it may end up in PhoneGapLib.

[› Visit the original post](http://blogs.nitobi.com/jesse/2010/04/01/iphonegap-plugs/)

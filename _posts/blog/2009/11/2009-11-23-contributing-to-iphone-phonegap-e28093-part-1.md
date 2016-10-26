---
title: Contributing to iPhone PhoneGap – Part 1
date: 2009-11-23 17:42:15 Z
categories:
- app
author: Shazron Abdullah
link: http://blogs.nitobi.com/shazron/2009/11/23/contributing-to-iphone-phonegap-part-1/
status: publish
type: post
format: html
---

There has been a major re-factoring of the iPhone PhoneGap codebase, to better enable users to get a current version of PhoneGap to use in their projects without mucking about in the core PhoneGap code.

You can view the code here: [http://github.com/phonegap/phonegap/iphone](http://github.com/phonegap/phonegap/iphone)

The README has more details, and I will elaborate on it more here, especially on how contributors can add to the code.

## PhoneGapLib/javascripts/core

This is where you will add/modify your javascript code for PhoneGap core. You can add more javascript files here, but make sure you update the "PhoneGapLib/Makefile" file to include the newly added javascript file. For adding the file in the Makefile, the pattern should be obvious.

## PhoneGapLib/Classes

This is where you will add/modify your Objective-C code for PhoneGap core. You can add more Objective-C files here, but make sure you add it to the PhoneGapLib Xcode project also.

## PhoneGapLib/javascripts/phonegap.js

This is dynamically generated, and is generated whenever PhoneGapLib is built. You can update this file by running "make" in the PhoneGapLib folder, but generally it should be called in your application that includes PhoneGapLib (which the PhoneGap-based Application Xcode template does).

I will walk you through how to add a new command, by adding Application Preferences support. Download the files [here](http://blogs.nitobi.com/shazron/wp-content/uploads/2009/11/PhoneGap_Preferences.zip).

### Preferences.h

```objc
@interface Preferences : PhoneGapCommand {
}
- (void) boolForKey:(NSMutableArray*)arguments withDict:(NSMutableDictionary*)options;
// other functions here

@end
```

Note that the class inherits from PhoneGapCommand. The class name you use here is important, since you will be referring to it in javascript.

To 'expose' a function to javascript, it must have the signature from the example 'boolForKey' method above (first argument is a NSMutableArray, the second argument is a NSMutableDictionary).

Let's now look at the javascript command to access the function above.

### preferences.js

```js
function PreferencesManager() { }

var g_Preferences = new PreferencesManager();
PreferencesManager.sharedPreferences = function() {
    return g_Preferences;
}

PreferencesManager.prototype.boolForKey = function(key, callback) {
    PhoneGap.exec("Preferences.boolForKey", key, GetFunctionName(callback));
}
```

The important line is the "PhoneGap.exec" line. The first argument to PhoneGap.exec is in the form of `<classname>`. `<methodname>`(refer to `Preferences.h` to see the corresponding function which should be obvious). The next arguments to `PhoneGap.exec` are two strings, which will be passed into the `boolForKey` method in the `NSMutableArray` which is the first argument. If an object (json object) is passed in as an argument to `PhoneGap.exec`, that data will be passed into the `boolForKey` method in the `NSMutableDictionary` which is the second argument.

### _Preferences.m_

```objc
- (void) boolForKey:(NSMutableArray*)arguments withDict:(NSMutableDictionary*)options
{
    NSUInteger argc = [arguments count];
    if (argc < 2) { // no key and/or callback - just return, no point in continuing
        return;
    }

    NSString* key =  [arguments objectAtIndex:0];
    NSString* callback = [arguments objectAtIndex:1];

    NSUserDefaults *userDefaults = [NSUserDefaults standardUserDefaults];
    BOOL value = [userDefaults boolForKey:key];
    NSString* retVal = value ? @"true" : @"false";

    NSString* jsString = [[NSString alloc] initWithFormat:@"%@('%@', %@);", callback, key, retVal];
    [webView stringByEvaluatingJavaScriptFromString:jsString];
    [jsString release];
}
```

In the command itself, you can parse the arguments and options, and do whatever you need to do for your command. You can optionally write javascript back, using the method above, or the helper:

```objc
[super writeJavascript:@"alert('foo')"]
```

**Next:** Adding your code to PhoneGapLib.

[› Visit the original post](http://blogs.nitobi.com/shazron/2009/11/23/contributing-to-iphone-phonegap-part-1/)

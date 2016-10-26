---
title: Debugging PhoneGap & JavaScript
date: 2011-05-18 20:10:33 Z
categories:
- app
author: Hiedi Utley
status: publish
type: post
format: html
tags_old:
- debugging
- phonegap
- phonegap training
---

If you have ever written any JavaScript and tried to get it working on a mobile phone then spent hours banging your head against the wall because it just doesn't work, this post is just for you. Today, we will be looking at ways to troubleshoot, diagnose, and debug your mobile web project. While I will be focusing on debugging interactions with PhoneGap, the strategies outlined here are really applicable to any JavaScript or mobile web project. Since I have been focusing mainly on iOS development, this post will discuss the debugging of JavaScript and PhoneGap within an iPhone application but the same ideas should work for Android and other platforms as well.

## Pre-requisites:

* Mac computer with [Developer Tools (Xcode)](http://developer.apple.com/xcode/) installed and up to date.
* If deploying to an iOS device, an [Apple Developer membership](http://developer.apple.com/programs/ios/).
* PhoneGap [installation and configuration for iOS](http://www.phonegap.com/start#ios).
* PhoneGap API Usage. See my [PhoneGap Tutorial Series for iOS](http://hiediutley.com).

## Where to get the Code?

To demonstrate the troubleshooting and debugging strategies outlined below, I will using the HelloPhoneGap project that I created for my [PhoneGap Tutorial Series](http://hiediutley.com). You can get the entire source for my sample project “HelloPhoneGap” from github here: [https://github.com/hutley/HelloPhoneGap](https://github.com/hutley/HelloPhoneGap)

## Common Problems

Over the course of putting together various applications, I have undoubtedly made many mistakes and spent many hours trying to figure out what went wrong. I have misplaced quotes, brackets, mistyped JSON and struggled with writing well-formed JavaScript that "looked right to me." I have misspelled method names, overwritten global variables, and forgotten to "install" my PhoneGap plugins. I have also tried to use PhoneGap methods in inappropriate locations and sometimes couldn't figure out why the feature works on my phone but doesn't work in the simulator. After all of those hours of trial and error, I would like to share some of the strategies that I used to help figure out my mistakes.

### Tip #1 - JavaScript Syntax Validation

So you wrote some JavaScript, added it to your page, wrapped it in PhoneGap, launched it in the simulator, waited patiently for a bit, clicked your mouse, and nothing happened. Huh? No errors, nothing. What could possibly be the problem? Well, there are many possibilities but the most likely is that you have malformed script. When running in a webView the JavaScript engine isn't very forgiving when it comes to mistakes and it doesn't bother to tell you about them either. Your page may render and the html may look pretty but if you missed a bracket somewhere you won't get a nice little red icon or a full suite of debugging tools to help you figure it out. When running on the simulator or even on your phone, you do not have the same tools that you would have if you were running in a desktop browser. So, what to do?

Depending on your development tools, you may or may not have decent support for JavaScript. If you are writing an iPhone app, you are most likely using XCode for your development. You probably have nice color coding and some not-so-smart code completion but if you want to write well formed JavaScript it doesn't really help all that much. What you can do is use a tool called JSLint to validate your code and point out those not so obvious syntactical errors.

#### There are a couple of ways run JSLint:

* **[JSLint.com](http://www.jslint.com/)** -- this website allows you to cut and paste your code into a form and it will validate your code
* **[JSHint.com](http://www.jshint.com/)** -- some people may feel that JSLint.com is a little too restrictive, if you are in this camp then you could also try using [JSHint.com](http://jshint.com/).
* **[SproutCore Bundle for TextMate](https://github.com/sproutit/sproutcore-tmbundle)** -- the nice folks at SproutCore have built a free bundle for TextMate that you can use to run JSLint right from within TextMate. Just install the bundle and run the "Validate Syntax" command. The bundle uses the [JavaScriptCore.framework library from Apple](http://developer.apple.com/library/mac/#documentation/Carbon/Reference/WebKit_JavaScriptCore_Ref) to run the JSLint scripts. The bundle can also "beautify" your script which is pretty handy as well.

JSLint can handle standalone script files as well as html files with script tags but there are a few limitations:

* All tag names must be in lower case.
* All tags that can take a close tag (such as) must have a close tag.
* All tags are correctly nested.
* The entity < must be used for literal '<'.

If you use TextMate, you can make sure that your HTML code is compliant prior to running JSLint by running the "HTML Tidy" command first.

### Tip #2 - JavaScript and HTML inspection

After making sure that you have well-formed JavaScript and you are convinced that can't possibly be the problem, the next step is ... debug! Oh, wait....there isn't really a JavaScript debugger available for the iPhone webView! Now what?? Well, [Patrick Mueller](http://pmuellr.blogspot.com/) has released an awesome tool - **Weinre** - that will allow you to interact with your webView remotely. You can inspect and edit the DOM, CSS, view log messages and even run JavaScript on the fly. It's the closest thing to an actual debugger for the mobile web that I have seen to date and while it takes a bit of effort to get set up and running, it's well worth it.

You can download [Weinre from github](https://github.com/pmuellr/weinre) and detailed instructions for installing and using it can be found [here](http://pmuellr.github.com/weinre/). The Weinre server app provides the tools to interact with client WebKit browsers. In order to make this happen you must set up and run the Weinre server and then add a script tag to each page of your web app that you wish to inspect and interact with.

The client side Weinre script uses AJAX to establish a connection and communicate with the Weinre server and allow the on demand inspection and editing of the DOM, CSS, and JavaScript. Jonathan Stark, author of Building Apps with HTML, CSS, and JavaScript, has put together a nice screen cast of Weinre in action - you can [view it here](http://jonathanstark.com/blog/2011/03/19/remote-debugging-for-mobile-web-apps/).

Once everything is up and running, you can use the Weinre tools to check that PhoneGap has been initialized and that you are using the correct PhoneGap API with the proper parameters. You can also inspect the DOM and your CSS, dynamically make changes and see how they may impacts your mobile site in real time.

Now, just so you don't make the same mistake that I did -- don't forget to remove the Weinre script from your pages when your are done debugging your pages. I lost hours one day when my app was suddenly hanging until I realized that I had forgotten to remove the script and my app was timing out looking for the Weinre server that no longer existed.

### Tip #3 - JavaScript Debugging in the Desktop

Now that you have verified that your script is well-formed and had a chance to inspect your site with Weinre, you may still have a problem and really only debugging will do. Well, there is always the poor man's debugger: "alert("made it here!");", but that's not very useful if you are using a lot of JavaScript or are dependent upon third-party libraries like JQTouch or SenchaTouch to do most of the heavy lifting for you. So, what else is there to do? Debug your app using your favorite browser based tool set of course! (I used Safari and Web Inspector....)

I know what you are thinking! It's a mobile browser! How am I supposed to debug it! The answer is that you aren't. You are going to debug your HTML, CSS, and JavaScript app in a **desktop** browser. The trick is to remove any dependencies that you have on PhoneGap before debugging. There are a couple of ways to go about this but the basic gist is to use some sort of mechanism to replace the PhoneGap calls with something else - a PhoneGap "shim" if you will. Several people have made their versions available out on github with varying degrees of capability.

#### PhoneGap "shims"

* [https://gist.github.com/476358](https://gist.github.com/476358) -- this snippet comes to us from Jesse MacFayden (@purplecabbage) and allows calls to be made to PhoneGap without causing JavaScript errors. With a little editing I was able to show an alert with the details of the phonegap command that would have been executed. To see the edited version - open the PhoneGapShim1.js in HelloPhoneGap project. I tested it out using the camera.html and the geolocation.html files in Safari.
* [https://github.com/alunny/stopgap](https://github.com/alunny/stopgap) -- this snippet basically just wipes out the PhoneGap object and fires the ondeviceready event. This might be useful if you don't rely on PhoneGap for all that much beyond display and don't care about testing your interaction with the PhoneGap device APIs.

Overall, the shims that I found were a little lacking but there is nothing stopping you from rolling your own. With a little more manipulation, the snippet from [@purplecabbage](http://twitter.com/purplecabbage) could be easily extended to provide a more robust framework to mock out PhoneGap and simulate device interactions.

That's all for now! Stay tuned for future posts and don't forget to check out my [PhoneGap Tutorial Series](http://hiediutley.com)!

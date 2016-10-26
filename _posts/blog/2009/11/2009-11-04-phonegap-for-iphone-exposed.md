---
title: PhoneGap for iPhone exposed
date: 2009-11-04 15:32:30 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2009/11/04/phonegap-for-iphone-exposed/
status: publish
type: post
format: html
---

Earlier this week I attended the Apple iPhone Developers Tech Talks in Seattle. The event was free and by invite only and you had to have an app in the app store, or be very close to having one to be invited. This meant that the content of the talk could be technical without losing anyone, and we had an informative deep dive into technical things like OpenGLES, Device Audio, and UIKit functionality best practices. I learned a lot over the day about what to avoid, and how to optimize iPhone applications.

As a PhoneGap developer, user and evangelist, I made it my duty to talk to everyone I could about PhoneGap and guage the level of interest from the Apple dev community. After speaking to a couple people at Apple, it became clear that they are very much aware of PhoneGap, but have very little understanding of what it does or how it works. I have decided to dig into these questions to make sure that there are no misconceptions about the project.  PhoneGap is entirely opensource, but not everyone has the time read a bunch of code. ( if only …)

## PhoneGap Under the Hood

PhoneGap aims to provide a consistent interface to device functionality across multiple platforms to enable rapid application development via well known technologies, namely HTML / JavaScript / CSS.

At it's core, PhoneGap is nothing more than a spec listing JavaScript accessible calls that an application programmer can use to make applications. Each device ( iPhone, Android, BlackBerry, … ) has it's own specific implementation, and the tools and processes you use to build, test and deploy/submit your app will vary for each. So again, PhoneGap is a JavaScript accessible API implemented on multiple devices.

All implementations render their user interface using HTML and CSS in a web browser control of some sort. Most modern devices support rich rendering features ( HTML5, CSS3 ) so it is a relatively simple to design, and layout your application with your existing skills, tools, and even existing graphical assets.

The typical PhoneGap application is a packaged version of a webpage/website that runs from the phone. What this means is that all html/css/js files are bundled into the application and run from the file:// protocol. A common misunderstanding is that the application is loaded over the web, which is definitely NOT the way we recommend users write their apps, and (to my knowledge) NOT the way typical PhoneGap based applications are architected. In this case you would be writing a mobile-optimized website and will likely not be approved for app store submission.

In some cases PhoneGap applications have a server component that delivers data via an HTTP API, usually json or xml using XMLHttpRequest. PhoneGap itself does not provide any server communication functionality, so app developers must roll their own server access layer.

### So How Does PhoneGap Work?

Every device implementation has it's own specific means of accessing device functionality, so I will be focusing on the iPhone implementation. The iPhone implementation is probably the most misunderstood, and most used, plus it is where I have spent the most time.

#### How does JavaScript call Objective-C code?

In order for a developer's application code (js) to access device functionality they will include the file phonegap.js in their (html) application. The file phonegap.js defines the entire API and contains the key functionality for device communication. All device functionality that PhoneGap exposes is done via the navigator object in JavaScript.

For example, to access Accelerometer functionality, you would call JavaScript methods on the navigator.accelerometer object.

In order for phonegap.js to send a request to the device it simply sets the location of the page based on the following protocol:

`gap://CommandHandler.method?arg1Name=arg1Value&amp;arg2Name=arg2Value`

* `gap://` - This is a phonegap request and not a request to load a new page.
* `CommandHandler` - This is a subset of device functionality that contains methods.  An example would be Accelerometer or Notification
* `method` - Each CommandHandler defines it's own methods
* `arguments` - a URL encoded list of arguments that are passed to the method ( varies based on the method ) Note that phonegap.js will URLEncode the parameters for you.

and here's a concrete example:

`gap://Notification.alert?message=Hello&amp;title=My%20App%Name&amp;buttonLabel=OK`

This will call the Notification objects alert method, passing it a message,title, and the text to display on the button.

So, upon receiving the command, Objective-C code will take over and perfom the requested command.

#### So How Does Objective-C call my JS code?

Some calls from JS require a callback mechanism to let the JS code know when the command has completed, if it succeeded and so on. The majority of this is handled for the developer in phonegap.js. Objective-C code will call stringByEvaluatingJavascriptFromString() to pass data back into the js code. The mechanism for each command is defined in phonegap.js, so the developer will simply pass a function callback that phonegap.js will call once the command has returned data.

Here is a concrete example:

In my application, I want to access the accelerometer, so I define a callback function :

```js
function onAccelData(accelObj)
{
  // accelObj has properties x,y,z that you can use to see the
  // current state of the accelerometer so presumably you
  // would do something with that data here.
}

function onAccelFail()
{
// accelermeter functionality is not available,
// do something else ...
}
```

In order recieve the data, I need to make a call to the js Accelerometer object :

`navigator.accelerometer.watchAcceleration(onAccelData, onAccelFail);`

Now, your callback is going to be called repeatedly with updated accelerometer data, that your application can use as you see fit. Since this is not intended to be a blog post about how to use the accelerometer, I will stop there. You should know also that the accelerometer supports stopping as well, and you can also specify how often you want to be updated.

So that, in a nutshell, is the entire iPhone implementation of PhoneGap. Note, there is no voodoo or magic sauce, just 2 data transfer mechanisms and a protocol between them.

Hopefully this will give better perspective and help anyone who has to answer the question: What is PhoneGap?

Remember that PhoneGap is completely opensource so if you want a deeper look under the hood, you are completely free to do so.

If you want to use PhoneGap, you can git it here :[http://github.com/phonegap/phonegap](http://github.com/phonegap/phonegap)

To read more, have a look at [www.phonegap.com](http://www.phonegap.com)

I invite your questions, comments, criticism, accolades, beers!

[› Visit the original post](http://blogs.nitobi.com/jesse/2009/11/04/phonegap-for-iphone-exposed/)

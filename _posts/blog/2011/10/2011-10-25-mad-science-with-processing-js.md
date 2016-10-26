---
title: Mad Science with Processing.js
date: 2011-10-25 23:16:05 Z
categories:
- app
tags:
- App
- Guest Post
author: Colene Chow
status: publish
type: post
format: html
---

Let's build a perfect scenario: You're sitting in a dim subway station and a train goes zooming past you. Attached to the side of the train is a tall, narrow strip of LCD's that are processing and displaying single columns of pixels of an image in a loop. As the train moves by the loop of columns are displaying at a rate fast enough that your eye stitches all the pieces of this image together to form a holograph, visible to the naked eye for a fraction of a second.

Let's take that to the next level: You have many strips placed on the side of the train that each fire a frame of an animation in sequence and now your eye sees a stop-motion holographic animation. This will be a huge leap forward in the world of art and advertising! Did I mention it's all written in HTML and JavaScript?

I'm Alex Smith. By day, I'm a Web Developer at Caltech/NASA Jet Propulsion Lab and by night, a JavaScript junkie. What you just read is my dream and it's almost here.

[![](/uploads/2011/10/6210385942_1e5a1e9d76_m.jpg)Poptart cat holograph made with 8bitapp Hellagraph Edition for iPad](/uploads/2011/10/6210385942_1e5a1e9d76_m.jpg)

**What it started as:** I commute on the metro train to JPL most days of the week and often write some really fun code to pass the time. Roughly eighteen months ago, I was doing a quick study with canvas and space invaders. Being the nerd that I am, I began daydreaming about applying space invaders to persistence of vision/light painting and decided to see what Processing.js could do with PhoneGap. A few months later, I released 8bitapp for iOS/Android which makes old school 8bit text/space invader light paintings that can be captured with a coordinating webcam app that I put together. At this point, the software was literally making space invaders in an 8x10 grid. After some revelations and stress testing, I figured out I could apply the same concept to images. In October 2011, 8bitapp: Hellagraph Edition for iPad was released with which users can create holographs (with added depth) from their own photos, paintings via 8bit paint mode, or over 450 old school video game characters. And just to be clear, this is not the trick of moving an image behind 2 black boxes in the foreground. This is actually processing an image, pixel for pixel (with user-adjustable depth/opacity), that allows the user to display holographs on either an X or Z axis perspective.

**What I am turning it into:** Persistence of vision is the phenomenon of the eye by which an afterimage is thought to persist for approximately one twenty-fifth of a second on the retina. I can currently make a holograph process in ~1 second with an old dualcore linux laptop. The software scales to any device and any screen (a double bonus of developing with web), so there is no downtime moving the application to a new machine/bigger screen. The last piece of the puzzle: the addition of more processing power to generate a much larger holograph (think: 10 feet tall) in a fraction of that original second that becomes visible to the human eye.

[![](/uploads/2011/10/6063065551_28e1e0a280_m.jpg)Light Paintings made with 8bitapp Hellagraph Edition for iPad](/uploads/2011/10/6063065551_28e1e0a280_m.jpg) I recently created a [Kickstarter site](http://www.kickstarter.com/projects/alexsmith/ten-foot-holographs-visible-to-the-naked-eye) to raise money to help me acquire this added processing power. Your support, whether it merely be a re-post to your facebook/twitter/etc would be more than appreciated. This project not only offers a new futuristic medium for art and advertising media, it sheds some much deserved light on examples of non-traditional things being done with HTML/JS and hopefully inspires other developers to write more JS. Processing.js has enabled highly creative programming for the web and I've been consistently impressed by it. Since discovering its power with my holograph app, I have been using it a lot more in my work at JPL. Currently, I am finishing up a web app which produces HTML5 bar charts, graphs, and other metrics for 17 years worth of JPL authored publications that are mapped throughout the JPL Org charts. To break the data down for you…I had a pool of 36K publications which had over 62K total authors who collaborated over 340K times in the course of 17 years. After finishing the core metrics functionality, I wanted to make some type of visualization of the collaboration data. I loved what mooWheel did with HTML5 and mooTools back in the day but it took ~10 minutes to fully display 5000 author collaborations. So one fateful day I ended up engineering my own version in Processing.js that chugged through the data in ~2.5 minutes, POW! (my original presentation link with a few videos in it can be [viewed here](http://prezi.com/p-j9qr9f-f4i/code-as-artjpl-artspace-talk-by-alex-smith/). the awesome video is a capture from a 27" Cinema HD running Chrome, zoomed out as far as possible - in normal resolution this visualization could easily fill an entire wall!)

[[![](/uploads/2011/10/phonegap-pacman_03.gif)](/uploads/2011/10/phonegap-pacman_03.gif)](/uploads/2011/10/phonegap-pacman_02.gif)

**What do I see in the near future for HTML/JS?** I think once there is a little more processing power, computer vision (see openCV) plugged into PhoneGap would make for a perfect storm of new interfaces and applications. Let's face it: as our processing speeds are increasing by leaps and bounds the idea of using web for larger/faster mobile projects becomes feasible. In a recent test, my crazy data intensive 8bitapp: Hellagraph Edition performed an estimated 200-300% quicker across all levels on an iPad2 VS original iPad1\. What I had thought was going to be the future power of HTML/JS is nearly already here.

Aside from the awesome new stuff going on in the browser, applying HTML and JS to mobile by itself feels like a complete rebirth of the web as an application platform VS a publishing platform. Doesn't the idea that you can write everything once and distribute it to every device, regardless of screen size and OS sound amazing?

Things you should look into: Processing.js, [Sketch Pad](http://sketchpad.cc), three.js, toxiclibs.js, iScroll, Lawnchair, openCV, and mongoDB

-Alex Smith

**More info about Alex:** Kickstarter: [http://www.kickstarter.com/projects/alexsmith/ten-foot-holographs-visible-to-the-naked-eye](http://www.kickstarter.com/projects/alexsmith/ten-foot-holographs-visible-to-the-naked-eye) Flickr: [http://www.flickr.com/photos/22949238@N05/](http://www.flickr.com/photos/22949238@N05/) Web: [http://8bitapp.com](http://8bitapp.com) Vimeo: [http://vimeo.com/user5266894/videos](http://vimeo.com/user5266894/videos) 8bitapp Hellagraph Edition: [http://itunes.apple.com/us/app/8bitapp-hellagraph-edition/id467900125?mt=8](http://itunes.apple.com/us/app/8bitapp-hellagraph-edition/id467900125?mt=8) Sketchpad: [http://studio.sketchpad.cc/sp/padlist/edited-by?editorId=971](http://studio.sketchpad.cc/sp/padlist/edited-by?editorId=971) Twitter: [@8bitapp](http://twitter.com/8bitapp) Email: alex [ a t ] 8bitapp [ d o t ] com

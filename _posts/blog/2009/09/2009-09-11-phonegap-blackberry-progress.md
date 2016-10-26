---
title: PhoneGap BlackBerry Progress
date: 2009-09-11 18:35:30 Z
categories:
- app
author: Fil
link: http://blogs.nitobi.com/fil/2009/09/11/phonegap-blackberry-progress/
status: publish
type: post
format: html
---

Hey everyone,

It's been a busy past two weeks in the [PhoneGap](http://www.phonegap.com) world, especially concerning the BlackBerry branch. We (Nitobi) have put a lot of work into this branch for the past week or two because we've got clients who are asking for BlackBerry support for the slew of new mobile applications we're developing. It's exciting because these kind of requirements really push the need for expanding the source code and making it better.

I wanted to share with everyone a couple of problems that we've encountered recently while working on these projects, and the solutions I employed to solve these problems. For reference, you can find my GitHub repository containing the latest PhoneGap BlackBerry code [here](http://github.com/filmaj/phonegap/tree/master).

First, we had quite a serious on-device rendering issue that didn't come up whilst testing with the BlackBerry simulator. Basically, scrolling would cause the HTML page and all related assets being rendered to 'tear' up as you scroll. Picture to provide a better explanation:

![Initial rendering / tearing issue we experienced.](http://www.nitobi.com/fil/BB-render.jpg)

Initial rendering / tearing issue we experienced - just after load on the left, after scrolling down and then up on the right.

Warning: BlackBerry code and JDE references ahead. Proceed with caution.

Since then I have solved the problem by calling invalidate() on the application's Screen's Field objects, and then invoking Screen.doPaint(). One issue still stands that we currently can only do this in a [Timer Task](http://java.sun.com/j2se/1.4.2/docs/api/java/util/TimerTask.html) that runs every x milliseconds, so intermittent tearing is still an issue. I tried to resolve this by executing the same invalidate / doPaint code in a custom VerticalFieldManager class extension, that hooked in the redraw code on scrolling events. However, this approach just didn't work. If anyone has any ideas on how to implement this more elegantly, don't hesitate to contact me or post a comment - I would love to solve this properly.

Second issue I fixed just today, actually, was a pain-in-the-ass requirement for BlackBerry PhoneGap applications to use a special URI when referencing content that is stored locally on the device. For example, up to this point if your main entry page had an  tag that referenced a .png file in the same directory as the main entry page, you would have to set the src attribute of the  tag to `data:///<absolute folder="" path="">/mypng.png`. This wasn't a show-stopper, but it did break the mantra of "write once, deploy to all platforms" that PhoneGap strives to uphold (because, for example, PhoneGap iPhone supports relative and absolute paths within your HTML/CSS/JS).</absolute>

My solution to this problem was to use a big hash table to store the absolute paths of various resources being loaded, and using the referrer IDs of these resources as the key. Then when we load in requested resources, we check if the referring ID is stored in the hash and build up the absolute path (which we need on the native BlackBerry side to grab the resource data) appropriately. I'm nervous about this approach because I can easily see this causing memory issues down the road - too big of a hash table, or keys being too large.

One mitigating option is, instead of using the entire referrer ID (which can get quite big - essentially it's the Base64 encoding of the referring resource), hash that down to, say, an MD5 hash, and then use that as a key. That should save some space. Currently, the hashing is done on all resources being loaded, which is obviously overkill. Images don't need to be hashed, for example.

Questions, comments, ideas, suggestions, please, post away! PhoneGap is an open-source, community-based project, so "just fork it" !

[› Visit the original post](http://blogs.nitobi.com/fil/2009/09/11/phonegap-blackberry-progress/)

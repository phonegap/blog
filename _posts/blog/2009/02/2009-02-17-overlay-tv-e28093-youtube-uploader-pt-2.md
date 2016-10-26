---
title: Overlay.tv – YouTube Uploader Pt.2
date: 2009-02-17 17:15:43 Z
categories:
- app
author: Jesse MacFadyen
link: http://blogs.nitobi.com/jesse/2009/02/17/overlaytv-youtube-uploader-pt2/
status: publish
type: post
format: html
---

Integration with Overlay's services was somewhat easier. They have a published API but unfortunately for this project, it is intended for use on other websites, so it did not make sense in a client application.

Overlay also has a flash movie that they use in their pages to support viewing, creating and editing overlays. The flash movie is an AS2 movie, so I was not able to load it directly, but instead ended up creating an HTML control and dynamically modifying the flashvars to get at the functionality we needed. ( BTW I love the HTML control in Air! ) The Flash movie already implemented 100% of overlay's functionality, so I was very glad to be able to use it directly.

Working closely with Overlay, I was given instructions on how to authenticate a user and get xml back. Â For getting the list of the current user's overlays weÂ consumed just grabbed the user's rss feed.

So go check out the [Overlay.tv YouTube uploade](http://overlay.tv)r and start making some overlays!.

Your feedback is welcomed.

Cheers,
Jesse

[› Visit the original post](http://blogs.nitobi.com/jesse/2009/02/17/overlaytv-youtube-uploader-pt2/)

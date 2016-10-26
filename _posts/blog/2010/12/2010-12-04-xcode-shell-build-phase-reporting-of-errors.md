---
title: Xcode shell build phase, reporting of errors
date: 2010-12-04 02:00:05 Z
categories:
- app
author: Shazron Abdullah
link: http://blogs.nitobi.com/shazron/2010/12/04/xcode-shell-build-phase-reporting-of-errors/
status: publish
type: post
format: html
---

[![](http://blogs.nitobi.com/shazron/wp-content/uploads/2010/12/xcode.png)](http://blogs.nitobi.com/shazron/wp-content/uploads/2010/12/xcode.png)Found this useful information, regarding Xcode error reporting for shell build phases. For example, if we were to include [JSLint](http://www.jslint.com/) in PhoneGap iPhone, we could format the errors this way below so code where the errors occur are easily editable:

> In shell build phases you can write to stderr using the following format:

**<filename>:<linenumber>: error | warn | note : <message>n</message></linenumber></filename>**

It's the same format gcc uses to show errors. The filename:linenumber part can be omitted. Depending on the mode (error, warn, note), Xcode will show your message with a red or yellow badge.

If you include an absolute file path and a line number (if the error occurred in a file), double clicking the error in the build log lets Xcode open the file and jumps to the line, even if it is not part of the project. Very handy.

[› Visit the original post](http://blogs.nitobi.com/shazron/2010/12/04/xcode-shell-build-phase-reporting-of-errors/)

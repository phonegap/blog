---
title: XUI Sweeter then ever.
date: 2009-11-05 12:01:04 Z
categories:
- app
author: silentrob
link: http://blogs.nitobi.com/rob/index.php/2009/11/05/xui-sweeter-then-ever/
status: publish
type: post
format: html
---

With so much buzz around the office about PhoneGap, I figured I would chime in too, call it a spite driven blog post.

Last week I decided to add some sugar to XUI our answer to a light weight JavaScript framework. Since XUI really doesn't need any new functionality it is really about progressively enhancing the existing code and project.

One area of the code I felt was particularly lacking was how XUI dealt with FORMS, and specifically how we could make XHR handle forms automatically. So lets start by looking at an example of how it worked before.

```js
// This will insert data.html into #some_div
$('#some_div').xhr('/data.html');
```

When this code runs, it will see that the XHR function has no options, and send the resulting responseText back to the DIV (blowing out the existing content - innerHTML)

```js
$('#some_div').xhr('/data.html', function() { alert("XHR Fired"); });
```

By making a simple change and passing in a function as the second parameter, you get the responseText back in the callback, this circumvents the responseText from being passing back to the calling node, making it arbitrary.

```js
$('#some_form').xhr(function() { alert("XHR Fired"); });
```

```html
<form id="some_form" action="/data.html" method="post">
  <input type='text' name='foo' value='bar' />
</form>
```

With the new changes from my last commit you now have both. In this case, the XHR function checks to see if node is a form, and then uses that data to construct the XHR request, action, method and form properties are all taken into account. Once the XHR has completed, it will call the callback function.

To learn more about XUI visit [XUI](http://xuijs.com)

Check out the code here [http://github.com/silentrob/xui](http://github.com/silentrob/xui)

Thanks.

[› Visit the original post](http://blogs.nitobi.com/rob/index.php/2009/11/05/xui-sweeter-then-ever/)

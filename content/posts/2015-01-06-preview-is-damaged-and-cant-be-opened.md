---
id: 4189
title: '&#8220;Preview&#8221; is damaged and can&#8217;t be opened.'
date: '2015-01-06T20:21:52+00:00'
author: 'Stephen Darlington'
excerpt: 'A simple solution to a bizarre problem.'
layout: post
guid: 'http://www.zx81.org.uk/?p=4189'
aliases: ['/computing/opinion/preview-is-damaged-and-cant-be-opened.html']
categories:
    - Opinion
---

> “Preview” is damaged and can’t be opened. You should move it to the Trash.

!["Preview" is damaged.](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2015/01/Screen-Shot-2015-01-06-at-11.20.25-300x149.png?resize=300%2C149)

This was the rather surprising error message that I’ve been getting when I try to open a PDF from the Finder since I upgraded to OS X Yosemite. It’s bad enough when you get an error message, but one suggesting that you delete a frequently used app is inconvenient to say the least!

Since I found it, I’ve been using a workaround: start Preview.app and open the file manually.

[But there’s a better answer](https://twitter.com/tonirogel/status/547134060452384770). Apparently it just has a duff “quarantine” attribute set. To get rid of it and get things back to normal simply do the following in a Terminal window:

```
/Users/stephend $ cd /Applications 
/Applications $ xattr -l Preview.app
com.apple.quarantine: 0006;53563f06;Acorn;
/Applications $
```

If you see the same thing, proceed to the next step:

```
/Applications $ sudo xattr -d com.apple.quarantine Preview.app
Password:****
```

And that’s all. Now opening a PDF from the Finder should work. It’s bizarre.

I raised Radar 19384558 with Apple. Please dupe if you see the same thing. Thanks to Gus Mueller (developer of Acorn) for [the support](https://twitter.com/acornapp/status/552536108563963904).

***Update**: It seems that a couple of other apps also have the same, incorrect attributes:*

```
/Applications $ xattr -l *.app Utilities/*.app | grep Acorn       
Mail.app: com.apple.quarantine: 0006;53563f06;Acorn;
iPhoto.app: com.apple.quarantine: 0006;53563f06;Acorn;
```

*I have also removed those tags, though I’ve not seen any problems with them so far.*
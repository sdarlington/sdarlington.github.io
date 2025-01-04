---
id: 4204
title: 'Double Trouble'
date: '2015-01-28T13:01:58+00:00'
author: 'Stephen Darlington'
excerpt: 'Fixing a broken Wordpress plugin turns out to be harder than I was expecting.'
layout: post
guid: 'http://www.zx81.org.uk/?p=4204'
aliases: ['/blog/double-trouble.html']
categories:
    - Blog
tags:
    - development
    - flickr
    - plugin
    - wordpress
---

One of the great things about WordPress is the community and the number of great plugins that can do amazing things with little effort.

But all that code, as any good developer will tell you, is a liability. How do you pick a plugin that not only meets your requirements now, but will both continue to do so? WordPress advances. APIs change. Plugins need love too.

Many moons ago I settled upon [Flickr Gallery](https://wordpress.org/plugins/flickr-gallery/), a plugin that allows you to import [Flickr](http://www.flickr.com/people/stephendarlington/) images just by adding a short-code to posts. I thought there was value in keeping all my public photos in one place and, at that time, WordPress had poor media management facilities. The plugin seemed popular and well supported.

[Flash forward](http://www.imdb.com/title/tt1441135/) to 2015 and, well, it doesn’t work. It hasn’t been updated for nearly five years and where I should see pictures I only see blanks.

But I’m a developer. How hard can it be to fix?

Groan! Have I ever said how much I hate web development?

Anyway… two hours later I find that there are not one but two problems. I find this after fixing the first problem in a server running on my local machine but find that it still doesn’t work here.

The first problem is that Flickr now requires SSL access to its API. In code terms, open *phpFlickr.php* and change the following lines:

```
 var $rest_endpoint = 'http://api.flickr.com/services/rest/';
 var $upload_endpoint = 'http://api.flickr.com/services/upload/';
 var $replace_endpoint = 'http://api.flickr.com/services/replace/';
```

To:

```
 var $rest_endpoint = 'https://api.flickr.com/services/rest/';
 var $upload_endpoint = 'https://api.flickr.com/services/upload/';
 var $replace_endpoint = 'https://api.flickr.com/services/replace/';
```

I found the cause of the second problem when I realised that none of the flickr code was getting called. It turns out that I have the Jetpack plugin and that *also* uses the “flickr” shortcode, though the syntax for using it is slightly different.

(I find it odd that there’s no error or warning flagging the conflict. This took far longer to track down than it needed to.)

I tried disabling that option in the [Jetpack](https://wordpress.org/plugins/jetpack/) plugin but that didn’t work. In the end, I added the following code to *flickr-gallery.php*, just before the “add\_shortcode(‘flickr’…” line:

```
if (shortcode_exists('flickr')) {
    remove_shortcode('flickr');
}
```

Very much cheating… but it does work.

I’m trying to figure out if there’s a way of distributing the change in a more user-friendly format.
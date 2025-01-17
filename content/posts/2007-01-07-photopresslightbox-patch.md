---
id: 275
title: 'Photopress/Lightbox Patch'
date: '2007-01-07T19:16:27+00:00'
author: 'Stephen Darlington'
excerpt: 'Like the "zoom" effect that you see when you click a picture here? Use Wordpress for your blog? You can download the plugin here!'
layout: post
guid: 'http://www.zx81.org.uk/news/photopresslightbox-patch.html'
aliases: ['/computing/software/photopresslightbox-patch.html']
categories:
    - Software
tags:
    - Computing
    - Software
    - wordpress
---

Ever since I moved over to using the [WordPress](http://wordpress.org/ "Wordpress CMS") content management system to host this website I have been using a relatively small number of plugins. One of my most used is [Photopress](http://familypress.net/photopress/ "Photopress photo gallery for WordPress") which you can see in use almost everywhere you see a picture.

However, late last year I realised how much one, small part of the functionality irritated me. You could either view a full size picture in a page on its own, but I’d never managed to create a template that worked well for both portrait and landscape images. Or you could have each image pop up in another window. I wasn’t keen on that either.

I eventually decided to “[scratch an itch](http://www.sourcextreme.org/index.php/Scratch_a_Personal_Itch "Scratching a Personal Itch")” and implement option number three. I’d found and liked the “zoom” effect provided by the [Lightbox](http://www.huddletogether.com/projects/lightbox2/ "Lightbox Javascript library") JavaScript library, and so decided to use that.

I did offer the patch to the author of Photopress, but I have heard nothing from him so find my changes here.

You’ll need to follow the following few steps to do the same with your own site:

1. Disable the Photopress plugin if you already have it installed
2. Download the Lightbox Javascript library and install it on your webserver. I put it in *wp-content/lightbox*[^1]. Remember where you put it as you’ll need it again in a couple of steps
3. Download and install the plugin. If you don’t have Photopress, try [this full version](/wp-content/uploads/2007/01/photopress-095sd.zip "Patched Photopress (Full Version)"). If you already have Photopress 0.9.5, you can download either [the only file that’s changed](/wp-content/uploads/2007/01/photopressphp.txt "Patched Photopress (Changed file)") or [this patch file](/wp-content/uploads/2007/01/photopressphppatch.txt "Patched Photopress (Patched File)")
4. Activate the plugin
5. Go to the Photopress Options screen. Look at the bottom of the screen. Here you can enable/disable the Lightbox effect and point Photopress to the Lightbox Javascript routines
6. Also make sure that you have switched off the “Link to Album” feature[^2]
7. You’re done

Please let me know how you get on. Hope you like it!
[^1]: You’ll need to keep the same directory structure as in the LightBox ZIP file. For example, you should see three directories “css”, “images”  
    and “js” Inside the “lightbox” directory on the webserver.
[^2]: Thanks to Roman Seibel for figuring this out.

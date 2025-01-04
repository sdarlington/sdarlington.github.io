---
id: 290
title: 'About this domain'
date: '2007-02-09T16:23:42+00:00'
author: 'Stephen Darlington'
layout: page
guid: 'http://www.zx81.org.uk/about/about-this-domain/'
---

ZX81.org.uk is now on its third major version. The first iteration — HTML files edited in a text editor — didn’t last very long as it was a deliberate stop-gap measure while I prepared the second.

Version two was very long lived, lasting from around 2000 to 2006. In this iteration I had one text file for each page on the site. Every file was in the form of a [Perl](http://www.perl.com/ "The Swiss army chainsaw of scripting languages") variable with a specific name, such as:

`$title = "About this domain";`

I then used a Perl script to generate the real HTML, automatically generating breadcrumbs and other visual niceties that were impossible to reliably maintain with a more manual system. The text files were stored in the same hierarchy as the website and a Makefile built the whole site locally. I’d then use my mirror program to upload the updated files to my ISP’s webserver.

It was a fine system in many ways. The two main problems were that I had to use my Linux box to make any updates, which was a pain as my Macs have been getting more and more use of late. Also, if I was away from home there was no way that I could add a new entry. Secondly, there was no simple way of making the site more interactive. Websites these days are pretty much expected to have the ability to interact with their readers.

After a lot of thinking I decided to move over to a proper “blogging” system. The move took several months as, while the new look was negotiable, I didn’t want to change any URLs unless I had to and all the old content needed to be imported. My *ad hoc* content management system helped here but was not 100% automated.

On a technical level it uses the [WordPress](http://wordpress.org/ "Wordpress") content management (blogging) system hosted on [TSO Hosting](https://www.tsohost.com)‘s cloud servers. I added a small number of plugins, mainly to make my life easier, and use one of the standard themes. The “circuit board” picture at the top is one of mine, of one of my old hard drives.
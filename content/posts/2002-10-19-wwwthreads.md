---
id: 131
title: 'WWWThreads 2.7'
date: '2002-10-19T17:22:55+01:00'
author: 'Stephen Darlington'
excerpt: 'Linux is famous for being a solid server platform. Stephen Darlington takes a look at a web application that you might consider using. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/linux/tps/wwwthreads-27.html'
permalink: /computing/linux/tps/wwwthreads.html
categories:
    - 'The Penguin Says'
tags:
    - Linux
    - Opinion
    - review
    - Software
    - unix
---

**Introduction**

While Linux cannot currently compete with Windows NT on the desktop (for a number of reasons that I’m not going to get into here), it has already made inroads into the server market. Many large companies use it as the OS for their web server (like [this](http://public.logica.com) machine), and many more use it on their intranet for sharing files and hosting web pages.

WWWThreads capitalizes on this framework, adding CGI programs to generate threaded discussion groups, just like Usenet but with a more appealing web front-end.

**Installation**

Installation should be fairly simple. All that’s involved is copying the files into a CGI directory on your server, alter a few parameters in one of the files and type ‘<tt>./wwwthread\_startup.cgi'</tt>.

Unfortunately it’s not quite that simple. The blame has to lie with the documentation which could best be described as minimal — a single 85 line README. The description of some of the variables that need changing is rather poor. I managed to change them to the wrong thing and only found out when I brought WWWThreads up in Netscape.

Of course, that’s when I finally managed to get it working at all! *[Apache](http://www.apache.org)*‘s first reaction was to complain about a ‘premature end of script.’ I’ve done a small amount of CGI programming, and realized that this meant that the web server wasn’t receiving a header describing the format of the data.

But why? Isn’t this supposed to be a finished program? I shouldn’t be getting run-time errors and the like? Then I remembered, my email address has an ‘@’ in it. ‘@’ is [Perl](http://www.perl.com)‘s way of saying ‘here’s an array’ and needs to be quoted to mean ‘at.’ This edited, the start screen appeared.

You could argue that it is a server side program, designed for knowledgeable people, and that I *did* manage to get it working in the end. However, all that’s needed is a little extra effort on the documentation and, maybe, a Makefile. Something like an Installation FAQ would be invaluable.

**From a user…**

Looking at the system from a web browser, things look much better.

WWWThreads has a very neat front screen. The colours have been well chosen; they look smart and well designed, but are very readable. In the top left is a logo, the top right has a menu. Below this is a list of the discussion groups that the administrator has set up. Clicking the title of the group brings up a list of the threads in that group. Clicking a thread bring up a list of posts. Clicking a post brings up that post. All very simple, standard stuff.

If you want to create a new post or reply to one that is already there, you will need to create a user for yourself. Here you’re invited to enter a user name, password, name, email, home page, occupation and hobbies. The first four are mandatory, the others optional. Clicking ‘Submit’ results in a screen (hopefully) saying that your details were added successfully. There are no other links or details on this screen, and you are forced to wait before your browser loads a new page. Annoying.

Replying to, or adding, a new post is similar. Fill in a few details, click submit and wait. There should at least be a link on this page to act as a short-cut for the impatient.

However, generally it is all well laid out, attractive and intuitive — there’s not much to write about.

**From an administrator…**

The administrative tools are good, and are web based just like the rest of the system. It allows the admin to change their password, add new discussion groups (‘Boards’), edit or delete posts, change details about the groups, archive a board, delete a board and edit users.

Most of these options are obvious, the one that might not be is the ‘archive’ option. This allows you to, in the words of the author, ‘…move all of the current posts on a board to an archive.’ This is a really good idea, and is implemented well, but does not go as far as I’d like. Some way of selecting posts by date or author, or individual posts would be useful. As would a method a more intuitive method of deleting archives (it appears as another board at the moment).

All the tools are password protected, which allows remote administration — a useful feature.

But the main thing missing is overall configuration options. What it I don’t like the look of the pages that WWWThreads produces? What if you want to fit it into your ‘house’ style? What if you don’t want to ask for hobbies or an occupation when a user registers?

The software is distributed with the GPL licence, so of course you *can* edit the HTML generated. But there is not documentation and much of the look-and-feel is hidden away in the Perl scripts. Perhaps some kind of template HTML file could be used?

**Conclusion**

WWWThreads is an odd program.

In some ways it is excellent. The design of the pages are good; the way that it remembers which posts you’ve read and those which you haven’t is useful; the archiving option is excellent, in fact most of the web based admin screens are very well done.

But then again, the installation is needlessly difficult, you can’t easily change the way that it looks, it seems not to perform particularly well (I am running the client and server on the same machine, so this might not be a fair comment) and the documentation is poor.

WWWThreads would be an ideal program to place on an Intranet server to allow people in the office to communicate more effectively. However, it’s lack of configuration options would probably make it unsuitable for an external site.
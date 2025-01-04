---
id: 124
title: 'StarOffice 4.0SP3'
date: '2002-10-19T17:22:55+01:00'
author: simeon
excerpt: 'Simeon Farrington takes a look at the latest from StarDivision, and discovers that quality doesn''t necessarily cost the earth. '
layout: post
guid: 'http://ccgi.sdarlington.plus.com/computing/linux/tps/staroffice-40sp3.html'
aliases: ['/computing/linux/tps/staroffice4.html']
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

StarOffice is a suite of Office applications for Linux, rivalling the plethora of Windows-based suites. It is available for “free” download for non-commercial use, although the download is over 43 MB for the original version, and over 53 MB for the version with all patches. Having used both original and patched versions, I suggest that it’s worth going for the larger file as a few fixes (mostly documented) have been applied. As the compressed file is so large, I used a program called ‘[wget’](http://www.netcomuk.co.uk/~simeon/wget-1.5.1.tar.gz) which allows incremental appending of files – After FMB my internet connection expired, but I was able to continue downloading from where it left off.

- StarOffice comprises of the following components:
- Star Desktop – Central browser for the Suite
- StarWriter/Web – Word processor / Web Page Editor/Browser
- StarCalc – Spreadsheet
- StarImpress – Presentation package
- StarChart – Chart creation
- StarImage – Image manipulation
- StarMath – Formula / equation editing
- StarBase – Database
- StarMail – POP3 / IMAP mail reader
- StarDiscussion – On-line Newsreader
 
It is however very different to the other suites on the market for other OSes because the whole package is fully integrated – One window for all applications; the relevant part of the suite is loaded into the window instead of each application being a separate entity.

**Setup**

Normally I would not expect to mention anything about program installation – you un-tar the file, type ./setup and away it goes. Well, in a perfect world, possibly.

StarOffice 4.0 requires a libc of at least 5.4.22. If you haven’t got this version, then the installation falls over with a meaningless message of the type *“syntax error at line 1 : token ‘|’ expected declarator; i.e. File”*?which doesn’t mention anything about libc. Further, if you are a RedHat 5 user, it probably won’t even get this far. It’s an irritation which was present in the previous release and was all the more irritating having just installed a new RedHat distribution (5.0) which only had revision 5.3.12-25!! However help is at hand, and there is all the information and fixes [here](http://www.netcomuk.co.uk/~simeon/fix.html) to get a RedHat 5.x system working. Once this is fixed, the installation works correctly, offering both network and user installations. A full installation will set you back about 130 MB.?

**StarDesktop**

The backbone to the Suite is a dual-windowed display, comprising of an “Explorer” type file manager, a main application window, and, when necessary, a “beamer” which appears to assist in news, mail and address book functions.?

All icons are displayed with images relating to the application they are associated with. However it is very easy to forget that the program is not a window manager itself, and hence cannot run executables; a couple of times I managed to display machine code in StarWriter.

**StarWriter**

I’ve always felt a word processor should be able to do all the basics well and simply before tackling the bells and whistles. Writer 4.0 bears a striking resemblance to it’s Windows counterparts, and will happily read and write MS Word 95 files, making the transition relatively easy, and enables files to be transferred between the systems.

The “Autopilot” function offers help in creating files in a similar way to the Wizards seen in many Windows products. I’ve not tended to use them as I work from my own templates. They seem to be reasonably competent although they seem to want to add in pictures at every opportunity, and you don’t really get a feel of what the finished template will look like until the Autopilot is finished.

**StarCalc**

Spreadsheets are funny beasts because no two are ever completely compatible. Again StarCalc is very reminiscent to Excel 95 in it’s appearance, and even the formulae appear rather similar. Being a heavy user of Excel at work, I tried loading some work files into StarCalc – however, many of the formulae were actually incompatible and it was only the simple ones which worked OK. However, the data files themselves were read correctly. So it’s not as compatible as Writer was with Word, which is a consideration for cross compatibility. However, it is a very powerful spreadsheet in many of the ways that Excel is in the Windows world.

**StarImpress**

This is a presentation package, equivalent to PowerPoint in MS Office. It was also the one component of the package which had me really tearing my hair out. One of the problems that appears certainly in the download version is that help files are *not* included in the original version, although this appears to be rectified in the service pack 3 version. Without the help files, Impress is rather difficult to get in to because it is no where near as intuitive as PowerPoint and I spent a lot of trying to find out how to do the most basic of operations. I also had to switch to a 16 bit colour display to display colours satisfactorily which might be a problem if your graphics card is basic.

The Autopilot was useful for templates, but unfortunately there was no way of telling what the slides would look like until it produced them.

My overall impression was a lack of flexibility in comparison to the competition. However, once you really know your way about, it may do all this. However, without a decent help function, I fear that many users will stick with other products which they know their way around.

**StarBase**

The database application is so well integrated that I almost missed it entirely, although by creating an address book I had actually used it. I found it easiest to use through the Autopilot which offered a reasonable range of preset tables, such as addresses, music and video collections, etc. I was very surprised to discover that it would not read my Access 95 files. On closer inspection I discovered it would read text, dBase, and ODBC files, although I didn’t have any such files to try them out.

**StarMath**

Offers the ability to create mathematical formulae in a similar fashion to the Equation editor contained in MS Office.

**StarImage**

My first impression was Corel Photo-Paint. My second impression was MS Windows Paint. It can display many formats but has only basic functionality. There are a handful of special effects, but other than adding titles and drawing rectangles and circles, that seems to be the lot. My advice is to stick with the GIMP.

**StarChart**

The chart function in other operating systems has been seen both as a separate entity (e.g. Corel Chart) or integrated (such as in MS Office). StarChart is a separate function within the Suite, and looks very similar to the function of inserting a graph into applications such as PowerPoint. I found it very difficult to get anywhere with this – StarChart chose it’s own display and stuck with that and although I could change the graph type, setting the correct parameters for the axes was beyond me. The help didn’t offer any useful support on this either.

**StarMail**

There are many mail readers, and my first impressions were that it works well, supporting POP and IMAP, and allowing both text and html email. However I soon changed my mind seeing how it stored email. Nearly all other mail readers I’ve come across store mail by appending text files allowing other mail readers to read and display the contents without corruption. Unfortunately the authors didn’t seem to see things this way, and each mail message is a separate entity which is unreadable by other readers. Opening mail folders created by “Pine” lead to reading a long list of text instead of discrete messages. Further if you have two messages with the same subject, one message will overwrite the other making follow-up messages very difficult. This is really the reason why I stopped using StarMail, and went back to Pine which is very simple and effective.

**StarDiscussion**

The news-reader is typical of most on-line readers I’ve tried with an option to subscribe to groups (maximum 2500) and the display can be threaded with the message list displayed in the beamer and the message in the main window. I could not however find a kill filter, and along with the fact that there is no (apparent) off-line facility, this may provide enough reasons to not use Discussion – it’s good, but doesn’t stand out from the crowd.

**Web Browser**

By typing in URLs in the tool bar, the application window will connect to remote web sites, and it follows very closely in the steps of Netscape – in fact the word “Mozilla” can be found within the options. It works pretty well, although getting the browser to choose a “save as” function was not easy, and a number of times StarOffice tried to display raw RedHat rpm files on the screen. It is possible to tweak the file-types option although I didn’t succeed on this occasion. I prefer Netscape for http and ftp as a result, however this program is showing a lot of promise here.

**Overall**

I am very impressed by StarOffice, and a few minor tweaks would quickly remove many of my complaints above. It is powerful and the complete integration of the applications is very welcome, although this makes it rather power-hungry and disk intensive. Stability seems to be significantly improved over previous releases and the only times I suffered crashes were in connection with on-line work. It is also free for non-commercial use which in an age of large, expensive heavy-weight applications is quite stunning. On the downside, the omission of the help files is a serious drawback so make sure that the version you get is the latest one (currently service pack 3), and along with the less-than-simple installation procedure (unless you are lucky enough to already have all libc revisions correct) the product risks alienating itself from many potential users, unless they really have the time to sit down and work it out.

> ***Also see [this review](/computing/linux/tps/staroffice5.html) of StarOffice 5.0.***
---
id: 307
title: 'Windows Mobile 5 on Virgin Mobile UK'
date: '2007-03-25T19:11:03+01:00'
author: 'Stephen Darlington'
excerpt: 'I had to go through hell (or Virgin Mobile UKs technical support department) to get MMS working on my Windows Mobile smart phone. Here''s what I did to save you the effort.'
layout: post
guid: 'http://www.zx81.org.uk/computing/windows-mobile-5-on-virgin-mobile-uk.html'
aliases: ['/computing/windows-mobile-5-on-virgin-mobile-uk.html']
categories:
    - Computing
tags:
    - Computing
    - mobile
    - phone
    - uk
    - wifi
---

When I got my new phone, a HTC P4350, I quickly managed to make and receive phone calls and text messages. I even connected straight to the Internet over WiFi and (slowly) over GPRS. It never occured to me that sending a MMS, a picture message, would be so complicated.

With a “Pow!” and a “Zap!” I asked their technical support people and got the answer. It works in two parts, firstly the GPRS side, which you can find in the Connections tab of the Settings screen:

[![Virgin GPRS Settings](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2007/03/page_1.jpg)](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2007/03/page_1.jpg "Virgin GPRS Settings")

(In case you can’t read them, the important settings are “goto.virginmobile.uk”, “user” (no password) and 193.30.166.3.)

Once you can make a connection to Virgin you can configure the MMS side of things, which you can find in the “Options” menu of the Messaging application:

![Virgin MMS Settings](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2007/03/page_2.jpg)

(Again, important settings are: 193.30.166.1, “http://mms.virginmobile.co.uk:8002” and “WAP 1.2”.)

And that should do the trick. Happy Multimedia Messaging!

(With thanks to Plasq’s [ComicLife](http://plasq.com/comiclife "ComicLife") for the over-the-top graphics.)
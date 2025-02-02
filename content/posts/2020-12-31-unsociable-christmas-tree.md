---
id: 67543
title: 'Unsociable Christmas Tree'
date: '2020-12-31T12:09:00+00:00'
author: 'Stephen Darlington'
excerpt: 'Christmas is usually a time for family and friends. But this tree only lights up when it sees someone it recognises.'
layout: post
guid: 'https://www.zx81.org.uk/?p=67543'
aliases: ['/computing/unsociable-christmas-tree.html']
spay_email:
    - ''
categories:
    - Computing
tags:
    - arduino
    - 'machine learning'
    - 'raspberry pi'
---

Last year I got myself a [Raspberry Pi-powered Christmas Tree](https://github.com/modmypi/Programmable-Xmas-Tree/). It has eleven LEDs, and you can program the Pi to switch them on and off.

Naturally, doing all that takes time, and last year I just didn’t have very much. I just downloaded the sample project and set it up with a random flashing pattern.

It amused me, anyway.

This year I wanted to get a little more sophisticated. I decided that it should be interactive. My first thought was a web server where people could connect using their phones and change the LED patterns. Then I thought better of it. Because of COVID we have no guests, rendering it far less interesting. Also, setting up a web server is hardly very exciting.

I wanted it to *detect* something but options were somewhat limited. The tree connects to the Pi’s pin connectors, but it didn’t leave any pins free to plug in anything else.

Next, I looked at my Arduino components. Could I do the sensing on the Arduino and the lights on the Pi? A sensible argument would be that wiring up two small computers like that would be ridiculously and unnecessarily complicated. While you wouldn’t be wrong, the whole point of this exercise is ridiculous.

In my Arduino bag of tricks, I have distance, presence, light and moisture sensors, buttons, switches and displays. I could have cobbled together *something* but while reading Twitter I got a better idea: how about I plug in a webcam and have the Pi detect faces and show different patterns depending on who is looking at it?

Luckily, other people have done most of the hard work. I based most of what follows on a blog “[How to train your Raspberry Pi for facial recognition](https://www.tomshardware.com/uk/how-to/raspberry-pi-facial-recognition).”

There are lots of steps, but they’re relatively easy to follow. It was all working fine until it asked me to build [OpenCV](https://opencv.org) from source, at which point [I ran out of disk space](https://twitter.com/sdarlington/status/1335295727036149760?s=21).

I gave up for a while.

What I’m saying is that while I was *planning* on something a little more elaborate, I ran out of time. Again.

When I came back to it, I realised that OpenCV was something that many Raspberry Pi owners were likely to use and I was surprised that I had to build my own version.

Luckily my surprise was supported by the actual Raspberry Pi software archive: if you install `python3-opencv` you get all the libraries you need, and all without all the hassle of having to build your own[^1]. As a side benefit, this removes about half of the steps in the tutorial!

The rest worked incredibly well “out of the box.” I ran it, trained it on a few unsuspecting family members and was very impressed that it worked the first time. It uses a lot of CPU on my Pi 4, so I’m not sure that it would work on any of the earlier models.

My next task was to hook in the Christmas Tree code so that the tree responds to changes in what the webcam could see. And… that’s where I ran out of time.

The interface between the facial-recognition and the tree lights is, well, *minimal*. If it finds someone it recognises, all the lights come on, otherwise, it goes dark. You can [see the code on GitHub](https://github.com/sdarlington/facial_recognition/blob/christmas-tree/facial_req.py) — only a handful of lines are mine.

It technically meets the requirements of an Unsociable Christmas Tree but is certainly less ambitious than I would have liked. Still, getting machine learning working on a Pi and connecting it to something physical was fun. Maybe *next* year I’ll get the time to bring everything together?

[^1]: In theory, installing `python3-opencv` means you can skip the whole of point 4, “Install OpenCV by running the following commands in your Terminal,” from the guide. In practice, I *tried* to build my own version of OpenCV so it’s possible that I have extra libraries installed that you also need. If I get the time, I’ll come back and try this on a default installation of Raspberry Pi OS.

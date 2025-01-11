---
id: 86012
title: 'Unsociable Christmas Tree (Part 2)'
date: '2023-12-01T10:58:00+00:00'
author: 'Stephen Darlington'
excerpt: 'Why write a quick and easy Python script when there’s an impractical alternative?'
layout: post
guid: 'https://www.zx81.org.uk/?p=86012'
aliases: ['/computing/unsociable-christmas-tree-part-2.html']
categories:
    - Computing
tags:
    - christmas
    - 'raspberry pi'
---

[Back in 2020](/computing/unsociable-christmas-tree.html)<span style="font-size: revert; font-weight: 400;"> I talked about my </span>[Raspberry Pi powered Christmas Tree](https://github.com/modmypi/Programmable-Xmas-Tree/)<span style="font-size: revert; font-weight: 400;">. Today’s blog delves into what I’ve done this year.</span>

Previously, I decided that setting up a web server on which family members could change the light patterns on the tree was too boring. At the time, I was thinking of extending the sample Python code – much as I did with the OpenCV frontend – with a simple Python-based web server.

There are a few problems with this approach. Firstly, while I’ve never set up a Python web server, I don’t necessarily feel that it would be a challenge. More of a challenge would be my web development skills, which are, for the most part, stuck in about 1997. If you want formatting using tables rather CSS, I’m your man.

I found a way to solve both problems, while also using a Raspberry Pi Zero W for something outside its intended purpose.

I decided to use the [Vaadin](https://www.vaadin.com/) Java framework for the user interface. With Vaadin you don’t need to worry about HTML and formatting, you say, for example, I want a block with a group of radio buttons and a text box, and it generates your HTML, JavaScript and backend code. You can kind of think of it as SwiftUI for the web.

I wrapped it all in [Spring Boot](https://spring.io/), because using an enterprise-grade UI library on a slow, single-core, 32-bit ARM CPU with 512Mb of memory isn’t ridiculous enough.

Jumping ahead for a second – spoiler alert – the application takes about *two minutes* to start on the Pi Zero W. It performs reasonably well once it’s started, but I think it’s fair to say that few corporations are going to be using Pi Zeros as part of their infrastructure.

It sounds bad, but the other way of looking at it is that it runs! A computer that [costs £15](https://thepihut.com/products/raspberry-pi-zero-w) is able to run 47Mb of modern Java 17 code<sup>[1](#fn1-24810 "see footnote")</sup>. It’s not practical, but it *is* pretty amazing.

Before figuring out the user interface, the first thing I needed to work on was how to get Java to talk to the LED Christmas Tree. The sample Python code uses some library code that reads and writes to the Pi’s GPIO pins. Can you even do that in Java?

It didn’t take a lot of searching around to find [Pi4j](https://pi4j.com), a Java library to do exactly that.

It took a lot of experimentation to get it working. The defaults didn’t work – no errors, it just didn’t light up the LEDs. The Pi Zero isn’t an ideal Java development platform, so I did the coding on my [MacBook](https://en.wikipedia.org/wiki/12-inch_MacBook), which also isn’t an ideal Java development environment. I was lazy, in a bad way, and didn’t properly build a test environment, instead building a JAR file on my laptop, manually copying over to the Pi and running it. I also found that Visual Studio Code isn’t as good as IntelliJ for writing Java programs.

Through a process of experimentation, I realised that I needed to use the `pigpio` backend provider<sup>[2](#fn2-24810 "see footnote")</sup>. The downside of using `pipgio` is that it requires super-user access. The alternative `LinuxFS` plugin does *not* need to be run as root, but it does not currently support access to the GPIO pins<sup>[3](#fn3-24810 "see footnote")</sup>.

Having proved that it was *possible* to flash the Christmas Tree’s lights in Java, I set out to port the Python library that came with it. The basics were pretty straight-forward. The sample code, however, uses sleep statements between the various lighting patterns, something that I didn’t want to do. I overestimated how complicated this would be and ended up simplifying my code. This is rare; I normally start super-simple and iterate.

Finally, I connected the two parts together, *et voila*, a working, Java-based program driving the Christmas Tree lights with a web interface for configuration.

| Computer | JVM | Startup time |
|---|---|---|
| Pi Zero W | openjdk version “17.0.8” | 111 |
| MacBook | openjdk version “21.0.1” | 4.2 |
| Pi 4 | openjdk version “17.0.9” | 15 |
| Pi 5 | openjdk version “17.0.9 | 5.6 |

Interestingly, the Pi Zero and the Pi 4 both start the JVM in “client” mode, while the MacBook and the Pi 5 use “server” mode<sup>[4](#fn4-24810 "see footnote")</sup>. The Pi Zero also runs in 32-bit mode. I suspect, but didn’t verify, that the difference between the 4 and 5 is at least partly down to the newer instruction set in the 5, which supports native “atomic” operations<sup>[5](#fn5-24810 "see footnote")</sup>.

Software is never completed, only abandoned. And in that spirit, there are a number of things that it would be nice to improve.

The most important aspect is that it’s currently running as root (well, my user with sudo). One perk is this is that it can trivially run on port 80. The risks of running as root on my home network are pretty low, but it’s still not a good idea. I’ll need to update the Pi library so it can access the GPIO pins as a non-privileged user. I’ll then need to figure out a clean way to have the server accessible on port 80 (a web proxy?).

Since we’re not aiming for practical, another option would be to go for the micro services approach. One service to manage the LEDs and another for the UI.

Who knows if I’ll get time for all that. Next year, maybe.

<div class="footnotes">---

1. I’m sure it used to cost less than this. The Pi Zero 2 W is now available for about the same price, but has a quad-core, 64-bit CPU. [↩︎](#fnr1-24810 "return to article")
2. “Pig-pio” is how I always think of it. [↩︎](#fnr2-24810 "return to article")
3. As I write this, I see that there’s [a new release](https://pi4j.com/about/release-notes/#2023-10-24---v240) of the Pi4j library which *does* support accessing the GPIO pins with `LinuxFS`. I’ll update the code when I get a chance. [↩︎](#fnr3-24810 "return to article")
4. Switching the Pi 5 to client mode didn’t make a huge difference. [↩︎](#fnr4-24810 "return to article")
5. At work, we benchmarked Apache Ignite on an ARM-based server, and found that it performed relatively poorly because it lacked the [Large System Extensions](https://learn.arm.com/learning-paths/servers-and-cloud-computing/lse/intro/). [↩︎](#fnr5-24810 "return to article")

</div>
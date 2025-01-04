---
id: 4619
title: 'Otto: Electronics'
date: '2017-03-09T18:20:35+00:00'
author: 'Stephen Darlington'
excerpt: 'After the relative ease of 3D printing Otto, I went about testing the electronics.'
layout: post
guid: 'https://www.zx81.org.uk/?p=4619'
permalink: /blog/otto-electronics.html
categories:
    - Blog
---

The first stage of [building a dancing, obstacle avoiding robot](https://www.zx81.org.uk/blog/new-project-otto.html) was to [build the body and legs using my 3D printer](https://www.zx81.org.uk/blog/otto-printing.html). The second was to test the electronics before assembly. This would prove to be more eventful than the printing.

I was least sure about all the electronics. They components arrived and… they sure looked okay. I didn’t think the buzzer looked quite right — it looked too big, but I figured that it even if a little lose it should make something approaching a buzzing noise.

The computer itself arrived poorly packaged, with a bunch of the pins bent. I managed to right them without breaking anything.

<figure aria-describedby="caption-attachment-4620" class="wp-caption alignleft" id="attachment_4620" style="width: 300px">[![](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2017/03/IMG_4012.jpg?resize=300%2C225&ssl=1)](https://www.zx81.org.uk/?attachment_id=4620)<figcaption class="wp-caption-text" id="caption-attachment-4620">Arduino Nano, IO Shield, obstacle detection (eyes), motors</figcaption></figure>

And talking of breaking things: I plugged in the Arduino and… nothing. Eventually I realised that I needed to install a Serial-USB device driver. The Otto download came with a CH341 (as it’s creatively called) driver so I installed it, rebooted and… well, when you see text scrolling up the screen when you boot your Mac, *either* you accidentally jabbed command-V *or* something bad is happening. In this case, the latter.

Anyway, after a fair degree of panic and dread at the idea of finding and installing another kernel driver from a random website, I [found one that seemed to work](http://www.mblock.cc/posts/run-makeblock-ch340-ch341-on-mac-os-sierra).

I tried the Arduino before bundling it into the plastic body just to make sure I had the fundamentals down. I plugged in the IO Shield and one of the motors. I press “Upload” in the Arduino app and… seemingly nothing at first. Then blinking. Then the motor started whirring rhythmically.

I picked out a few other example apps and tried those. The best one, at least in the sense that it proved that I was doing the right thing, just blinked one of the boards LEDs. It looked like it worked, so I changed the delay from one to two seconds and saw that *that* worked too.

Nice.

Now all the bit are made and shown to be more or less Known Good, it’s time to assemble Otto.
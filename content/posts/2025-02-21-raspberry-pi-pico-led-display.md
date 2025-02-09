---
date: '2025-02-21T11:22:58Z'
title: 'Raspberry Pi Pico: LED Display'
author: 'Stephen Darlington'
layout: post
categories:
    - Opinion
tags:
    - Raspberry Pi
    - hardware
    - python
---
It's been a productive weekend, at least if you consider doing unnecessary things productive.

For reasons that won't become clear any time soon, I decided that I wanted to get some of my [Arduino](https://www.arduino.cc) components working with my new [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/). Like the Arduino, but unlike other Pis, the Pico is a _microcontroller_. In practical terms -- for a programmer at least -- this means it doesn't have a "proper" operating system like Linux but it _does_ have lots of inputs and outputs, both digital and analogue.

In a fit of hubris, I decided to try to get one of the more complex components working first. I have a two-line LED display (a 1602, meaning two rows of sixteen characters) which plugs into the controller with six data lines, plus power and a variable resistor to control the brightness of the backlight.

I'd had this working with an Arduino previously, but there were two challenges this time. First, the Pico had holes where I needed pins and the Arduino kit came with working software to drive it. This time I had to add the pins myself and find or write the software.

I'm not sure that I've had to solder anything since university. I didn't do a lot then either and, when I did, I remember the smell and occasionally burning my fingers rather than the accomplishment itself.

This time I had the additional challenges of no instructor, much smaller holes to solder and varifocal glasses. I had a hard time when I started. I began with a relatively low temperature, on the assumption that it was better to start colder and get hotter than the other way around. It partially worked at the lower temperature but got dramatically easier as I increased the heat.

In the end, I managed to complete attaching all forty-three pins to the Pi without melting anything I shouldn't or fry the controller itself.

Wiring up the 1602 to the Pi was straightforward, the hardware side of the equation was now complete. Next: software.

I searched the web to see if other people had tried the same thing. Of course they had. I found many examples, but none exactly fit my requirements. The most common stumbling block was that in order to reduce the number of pins needed on the Pi, they'd used some "backpack," which, as far as I can tell, is an extra chip or two that reduces the number of wires needed.

I eventually found a [blog that looked promising](https://www.mbtechworks.com/projects/drive-an-lcd-16x2-display-with-raspberry-pi.html). It describes connecting a 1602 display to a regular Raspberry Pi _without_ any extra chips.

The Pico has similarities to the Pi, but the sample code didn't work "out of the box." The libraries that talk to the GPIO pins are different and it uses MicroPython rather than full-fat Python.

Luckily the required changes were pretty simple:

1. The original code uses the RPi.GPIO library. This was straightforward to port to using the Pico's equivalent, which is machine.Pin
2. There was a surprising omission in MicroPython, in that it's missing the `ljust` function which pads strings to given length. I was able to replace that with a format string. I'm no Python expert, I searched Stack Overflow for that

And that was pretty much it. When I put the pins in the right place and used the 5V power rather than 3.3V it Just Worked.

<script src="https://gist.github.com/sdarlington/23cb8277d4d11f7c97acf6bd014b7c76.js"></script>

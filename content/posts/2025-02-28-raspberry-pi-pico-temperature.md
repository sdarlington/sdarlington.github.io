---
date: '2025-02-28T10:23:23Z'
title: 'Raspberry Pi Pico: Temperature Sensor'
author: 'Stephen Darlington'
layout: post
categories:
    - Opinion
tags:
    - Raspberry Pi
    - Hardware
    - Python
---
[Last time](/posts/2025-02-21-raspberry-pi-pico-led-display), I talked about setting up my Pi Pico by soldering on the GPIO pins and wiring up an LCD screen. Having something work is obviously no fun. I need another challenge.

I decided to update the display to show the current temperature. I'd read that the Pico has a built-in temperature sensor, so how hard could it be?

I quickly took the sample code from the Pico website and plugged it in. It ran first time, which is quite impressive, and said that it was currently... 10º.

I don't think that's right. It's about 20ºC. It's way warmer than 20ºF. Hmm.

But I have a brain-wave. Amongst my Arduino components is a DHT11 temperature and humidity sensor. How would that work on a Pico? Is it simple to grab a new value? (No.) Are there existing libraries that I could use? Yes, though it's difficult to find who originally wrote them. I found lots of quite similar code from many different people. I'm not sure if it's public domain or if people are just really bad at giving credit.

I ended up using [this code](https://github.com/ikornaselur/pico-libs). And... it didn't work.

It _ran_ just fine but it said that it only got one value rather than eighty-four. I followed the code, tweaked a bunch of settings, tried 3.3V and 5V and nothing would make it work.

On a whim, I tried it on my Arduino where it also didn't work. I guess it's a dud.

But all was not lost. My kit came with yet another temperature sensor, this time a DS18B20[^1]. The installation of MicroPython that comes with the Pico includes all the required libraries to work with one (`import machine, onewire, ds18x20, time`). I entered some [example code](http://www.pibits.net/code/raspberry-pi-pico-and-ds18b20-thermometer-using-micropython.php) and... it didn't work.

Again?

Luckily, the answer to this was straight-forward. The Pico appears not to have enough juice to power both the display and the temperature sensor. Unplug the LCD display -- or rather the backlight -- and it correctly measured the ambient temperature. Unlike the built-in sensor, it was saying the room was about 20ºC, which is about right.

Unfortunately, I still don't know why the built-in sensor says that it's around 12ºC and I still can't display the temperature on the LCD.

[^1]: All these components have such great and memorable names.
---
id: 4151
title: 'Java and Yosemite'
date: '2014-11-04T20:44:34+00:00'
author: 'Stephen Darlington'
excerpt: 'An annoying error message takes far longer to solve than I''ve have liked...'
layout: post
guid: 'http://www.zx81.org.uk/?p=4151'
aliases: ['/computing/opinion/java-and-yosemite.html']
categories:
    - Opinion
tags:
    - apple
    - error
    - Facebook
    - mac
---

<figure aria-describedby="caption-attachment-4152" class="wp-caption aligncenter" id="attachment_4152" style="width: 300px">!["To view this web content, you need to install the Java Runtime Environment."](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2014/11/Screen-Shot-2014-11-03-at-20.42.54-300x152.png?resize=300%2C152)<figcaption class="wp-caption-text" id="caption-attachment-4152">“To view this web content, you need to install the Java Runtime Environment.”</figcaption></figure>

Ever since upgrading from OS X 10.9 to Yosemite (10.10) I’ve been getting the above error message periodically. As far as I know I have no software that needs Java to run.

[When I asked on Twitter](https://twitter.com/sdarlington/status/524830897783455744/photo/1), the most common suggestion was that it was the Adobe updater. But I don’t have PhotoShop or anything else likely installed.

I checked the system logs, but, again, nothing.

The final obvious — for a fairly broad definition of “obvious” — was in System Preferences. If you look in the “Users” pane, you can find a list of “Login items,” programs that are started when the computer boots. (I figured this wasn’t likely since the alert pops up at all time but it was worth checking.)

I *think* I found the solution but I found some interesting (if you’re geeky) new commands that I thought I’d talk about before I document the actual solution.

So the underlying system that the Mac uses to start programs periodically is called ‘launchd’ (or “launch daemon”). It’s kind of an amalgam of *init* and *cron* and a bunch of other standard Unix processes, [a concept that is controversial](http://boycottsystemd.org) in some circles. The interface, I found, isn’t terribly intuitive.

In addition to the long-running process, there’s a configuration program called ‘launchctl.’ The man page runs to several pages. ‘launchctl help’ is only slightly shorter.

I find the ‘list’ subcommand in the “legacy” section and give it a try:

```
$ launchctl list | grep -i java
- 0 com.apple.java.updateSharing
98767 0 com.apple.java.InstallOnDemandAgent
$
```

The columns are Process, Status and Label. So we can see that Apple’s Install On Demand Agent is running but not what triggered it.

There’s also a sub-command called ‘procinfo’. It’s not even “legacy” so it must be good… I certainly can’t complain about the volume of information, though I couldn’t claim to understand a good chunk of it.

Ah, but then I see ‘blame’ which the help tells me ‘Prints the reason a service is running.’ Ooh, yes please!

```
$ launchctl blame 98767
Usage: launchctl blame <service-target>
$
```

Er, so what’s a service-target?

Anyway, long story short, I find that the text in the man page isn’t entirely clear and that I need to do this:

```
$ launchctl blame pid/98767/com.apple.java.InstallOnDemandAgent
Not privileged to signal service.
$
```

So, I don’t know. (If anyone could give me a sample command I’d be grateful!)

But, after all this messing around I *did* find something. The configuration for ‘launchd’ is scattered around the filesystem in directories like ‘~/Library/LaunchAgents’. I grep’d in that directory for “java” and found a single reference to it in an application that I installed ages ago and never used. The file is called “com.facebook.videochat.stephend.plist”. I deleted it and the other binaries related to it and then restarted.

Clean so far…
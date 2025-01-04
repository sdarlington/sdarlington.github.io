---
id: 234
title: 'Installing Oracle 10g Express Edition on CentOS 4'
date: '2006-10-22T18:58:42+01:00'
author: 'Stephen Darlington'
excerpt: 'I recently tried to install Oracle 10g Express Edition on CentOS 4. Things have dramatically improved since the early days of Oracle on Linux, but here are the details.'
layout: post
guid: 'http://www.zx81.org.uk/computing/oracle/oracle-howto/installing-oracle-10g-express-edition-on-centos-4.html'
aliases: ['/computing/oracle/oracle-howto/installing-oracle-10g-express-edition-on-centos-4.html']
categories:
    - 'Oracle Howto'
tags:
    - Computing
    - database
    - Linux
    - Oracle
---

The short story is that if you have a standard configuration things should work entirely as you’d expect. That is, download the archive which, these days, comes as a RedHat “rpm” file. Become “root” and enter “rpm -ivh oracle-xe.rpm” and wait a bit. The install goes away and creates all the required users, starts up the listener and creates a default empty database.

[CentOS](http://www.centos.org "Not RedHat Linux"), for those that have not come across it, is a Linux operating system built from the same source package as RedHat Enterprise Linux but without the support contract.

The first thing to note is that the few problems that I had were probably my own fault. Hardware was the main one. At home I’ve moved almost exclusively to Macs, and the one x86 Linux machine is a Via C3 running at 533Mhz and only has 512Mb of memory, both some way below Oracle’s recommended minimum.

So I downloaded the *oracle-xe-10.2.0.1-1.0.i386.rpm* file, switched to *root* and entered *rpm -ivh oracle-xe.rpm*. And it didn’t work.

On the plus side, it told me exactly what the problem was: I didn’t have *libaio* installed. I installed it (*yum install libaio*) and tried again.

It worked!

It took a long time to create and start the database, but this is Oracle and this is an old, slow machine, and everything I have tried so far is operating correctly.

To be honest, the only problem I have found so far is that I can’t get the web admin interface working from a remote machine. If I click the button to enable the option, I get a blank page in Firefox and no luck from the Mac end. Bouncing the database (*/etc/rc.d/init.d/oracle-xe restart*) seemed not to make any difference.

If you come across any further problems (or solutions) please do add a comment below.
---
id: 137
title: 'Oracle 8i for Linux Installation HOWTO'
date: '2003-07-19T11:34:16+01:00'
author: 'Stephen Darlington'
excerpt: "With this HOWTO, and a little luck, you will be able to get \"Oracle 8i   Enterprise Edition for Linux\" installed, create a database and connect   to it from a remote machine. The main focus of this guide is RedHat   Linux 6.0 and Oracle 8.1.5, although it should work well for other   recent distributions and more stable versions of Oracle.\r\n"
layout: post
guid: 'http://ccgi.sdarlington.plus.com/news/oracle-howto.html'
permalink: /computing/oracle/oracle-howto/oracle-howto.html
categories:
    - 'Oracle Howto'
tags:
    - Computing
    - database
    - Linux
    - Oracle
    - unix
---

v1.18, 19 July 2003

With this HOWTO, and a little luck, you will be able to get “Oracle 8i Enterprise Edition for Linux” installed, create a database and connect to it from a remote machine. The main focus of this guide is RedHat Linux 6.0 and Oracle 8.1.5, although it should work well for other recent distributions and more stable versions of Oracle.

### 1. Introduction

### 1.1. What’s in here?

 Linux is well known for being difficult and, generally, user hostile. Being a bit of a Unix fan I’m not sure whether I agree with that or not.

 Oracle is similar I guess. Initially it’s difficult to get to grips with, but it’s difficult to work with any other RDBMS when you’re used to it.

 Combine the two, remember that 8i is only the second production release, and you realise that this isn’t going to be straight-forward, even if you’re familiar with both.

 I am, but I had problems. Many problems were my own stupidity or hubris, but I document them for completeness.

### 1.2. Who is this HOWTO for?

 Fundamentally this document is about installing Oracle 8i Version 8.1.5.0.0 on RedHat Linux 6.0, and any deviation from this configuration may reduce your chances of success. (I originally tried to write this guide for all types of Linux and all recent version of Oracle, but the structure was unclear and it was less useful for just about everyone.)

 For later versions of Oracle, including 9i, you have two options. I have some errata on my website <http:></http:>. You’ll find that the process is very similar to that found in this document although there are some ‘gotchas’ for each version. Generally speaking, newer version of Oracle are much easier to install than 8.1.5 and are recommended over it by just about everyone, including Oracle themselves.

 Or if you prefer there are also a number of other, more specific guides at the Linux Documentation Project (in fact there seems to be a new one there every time I check back!). If you’re installing 8i on RedHat 7.x, Krastio Atanassov and Luca Roversi’s <http: formats=""> HOWTO might be useful. For installing Oracle 9i on RedHat 8 or above, Evgueni Tzvetanov’s <http: formats=""> guide could well do the trick.</http:></http:>

 For different distributions of Linux chances of success are also good, especially if they are RedHat-like, Mandrake for example. Again, my web site may contain advice for certain troublesome distributions.

 If you want to install 8.0, I recommend you try Linux Journals guide <http:>, and if you want to install any of the previous versions you’re going to have to use the SCO version and follow Paul Haigh’s Oracle Database HOWTO <http:>.</http:></http:>

 If you’re trying to install the ‘right’ version, what level of background knowledge will you need?

 Perhaps the easiest way is if I explain a little of my background, clearly if yours is similar we’re going to be on the same wave-length. I’ve used a lot of Unix and Oracle over the last few years. At home I’ve been running Linux since 1994 and I’ve been using Solaris and HP- UX on-and-off since 1992. I first came across Oracle in 1996 and have worked with versions 7, 8 and 8i. I’m mainly a developer, but I have done DBA and sysadmin-type work.

 In summary, I can find my way around a Unix box and I know much of the Oracle terminology. You’ll need both to brave the rest of this document. But don’t worry if you have a different background, follow this guide closely and keep asking questions. The Linux community are a helpful bunch, just don’t expect an answer if you haven’t at least made an effort to solve the problem yourself.

### 1.3. New versions of this document

 Since RedHat Linux 6.x is no longer being supported and given that there will be no new releases of Oracle 8i, you can probably assume that this is the most up-to-date version of this document.

 As discussed in the previous section, there are documents in the LDP <http:> and extra sections on my website <http:></http:> that might help you get more contemporary versions of Oracle installed on newer versions on Linux.</http:>

### 1.4. Disclaimer

 You get what you pay for. I offer no warranty of any kind, implied or otherwise. I’ll help you where I can but legally you’re on your own.

### 1.5. Credits and Thanks

 This HOWTO has been written by Stephen Darlington. It couldn’t have been created without the constant stream of questions and answers on the Oracle Technology Network website and the Usenet news-groups. So thanks to the people that keep posting and sorry that I can’t credit you all individually!

 Many people have emailed me directly with hints, updates and corrections; this document would not be as useful as it is without their contribution. So thanks go to the following people: Ton Haver, Guy Cole, Iain Frerichs, Albert Braun, Steve Morando, Krill Kokoshka, Brain Slesinsky, Galen G Burk, Bill Gathen and Veres Lajos.

 I welcome any constructive feedback on this HOWTO and any general Linux or Oracle issues. However, if you have questions it’s probably better that you ask on a newsgroup or the discussion forums on my website where others can benefit from the solutions. Email me at stephen at zx81 dot org dot uk <stephen at="" dot="" org="" uk="" zx81="">.</stephen>

### 1.6. Licence

 This document is copyright 1999-2003 Stephen Darlington. You may use, disseminate and reproduce it freely, provided you:

- Do not omit or alter this copyright notice.
- Do not omit or alter the version number and date.
- Do not omit or alter the document’s pointer to the current WWW version.
- Clearly mark any condensed, altered or versions as such.

 These restrictions are intended to protect potential readers from stale or mangled versions. If you think you have a good case for an exception, ask me.

 (This copyright notice has been lifted from Eric Raymond’s Distribution HOWTO.)

 You do not need to ask me if you’d like to provide a translation, although notification would be appreciated.

### 2. Starting off

### 2.1. Overview

 In this section, we’ll set up Linux so that you’re in a position to get Oracle 8i from the CD that they sent you into your hard-disk. (If they didn’t send you a disc and you’re working from a tar-ball that you downloaded from the Internet, don’t worry. The installation process is identical.)

 The Oracle installation process begins when you’ve built your PC, installed Linux, configured it and connected it to your network.

### 2.2. Prerequisites

### 2.2.1. Your brain

 This may sound like a very silly prerequisite, but I do mean it although not necessarily in the same way you might be thinking just now. There are two main problems.

 Firstly, both Oracle and Linux change very frequently. This is a good thing in that bugs and security holes gets fixed quickly and there are always new and exciting enhancements to play with and, with luck, solve the problems we’re actually paid to solve. The bad news is that no matter how much effort I put into this document it’ll never be completely up to date.

 The onus is, therefore, on you to engage brain. Sometime Oracle change small things. The dialog used to say “OK” but now says “Okay”, or the screens are in a slightly different order, or… well, it could be any number of things. There’s no way I can keep up on all the changes like that, just like there’s no way that I can provided detailed guides for every version of Oracle running on every possible Linux distribution.

 Or it could be the big, complex things, like when RedHat Linux 7 first came out with new C libraries and a slightly non-standard C compiler. You could apply the first point here, applying your brain, reading the release notes, the RedHat website and Oracle Technet but you’d be spending more time than you need to be. The reason is problem number two: the culture clash.

 In the case of Linux, newer is better. People frequently upgrade their OS to the latest and greatest and it’s certainly not unusual to add or upgrade individual packages to something more familiar or more powerful. This is not how things are done in the world of Oracle. Companies are still running Oracle 6, software that has been available for more than ten years. (Oracle have not supported this for quite some time, so this isn’t terribly smart.) People here value stability and change, so loved by many Linux die-hards, is the complete antithesis of it.

 The trick to applying this to installing Oracle 8i on your Linux box is to read the release notes. If they recommend RedHat Linux 6, as they did for Oracle 8i 8.1.5, this is the distribution that you should use unless there’s a *very* good reason to do otherwise. The same for any other requirements they state: their hardware and software requirements have, to date, been pretty accurate.

### 2.2.2. Hardware

 I think that the most important part of the prerequisites is not to underestimate them. Oracle is a very big and complex application and you won’t get the best out of it if you skimp too much on the hardware.

 My biggest mistake was to assume that Oracle were joking when they said that you need 128Mb of RAM. I’ve installed Oracle a couple of times on Sun servers with that much, why would I need more on a CISC machine?

 Believe Oracle not my gut. My machine with 32Mb of Ram ground on for less than half an hour before I realised that it was hopeless.

 I was trying to use the bare minimum of hardware, and that’s generally a bad idea. If you can’t afford the hardware you certainly won’t be able to afford the licences!

 Things to look for on a production server are many disks, possibly RAIDed, and fast CPU’s. Database access is relatively easy to break down into smaller parallel phases so having a number of processors really does help.

 On the other hand, any machine that can run Linux and that has enough memory should be in with a chance. My other machine, the one I used for the rest of this document, is fine as a development machine. It is a Celeron 466Mhz with 128Mb of memory, an 8Gb hard disk, an Intel graphics card and a DM9102 network card.

### 2.3. Linux setup

 **2.3.1. Choice of distribution**

 Oracle seem to have done most of their development on RedHat Linux 6.0. For a fuss-free installation, using RedHat is an excellent idea. Using version 6.2 with all the patches will be the easiest. For RedHat Linux 7 and later refer to my website. Depending on how you’ve installed your operating system there may be extra steps required.

 I’ve heard horror stories about trying to get it installed on other distributions. However, as a general rule, anything *like* RedHat should also do the trick. A recent version of Mandrake should be fine and SuSE, in fact, are fairly active in supporting Oracle and have [a web page dedicated to the task](http://www.suse.com/us/solutions/partners/oracle/).

 The further you get from RedHat the more problems you can expect.

 **2.3.2. Distribution Setup**

 Now that you’ve decided on which RedHat-like distribution you’re going to use, you’ll need to work out which options to set and which of the vast number of packages need to be installed to make Oracle work.

 Firstly you need two to three times the amount of memory you have for your swap space. (You’ll need around 200Mb of memory, real or virtual, just to run the installer!) Note that contrary to popular opinion, Linux swap partitions can be larger than 128Mb.

 The arrangements of your other partitions can also be important. Make sure that the Oracle software is on a different partition to your operating system, and make sure that the Oracle data-files are on yet another partition. The idea here is to make sure that your data-files do not get fragmented. (In a live environment, you’re likely to have a number of disk with Oracle spread across them. There are a number of good books that you consult for more information on this.) Also, make sure you have *at least* 400Mb free in /tmp and that it’s not on the root filesystem.

 As for the software, I took the easy option and installed just about everything. You certainly need all the ‘base’ packages, X Windows (the installation routine is a Java GUI) and the development tools regardless of whether you intend doing any coding or not. Compared to the size of Oracle and your databases a Linux distribution is tiny, probably less than a gigabyte. It’s worth installing it all for an easy life!

 **2.3.3. Kernel parameters**

 The documentation suggests that you make changes to the Linux kernel so you can get more shared memory. Since I was only planning on running a very small database, I assumed everything would be okay and decided to go ahead with the installation anyway. The default RedHat Linux settings worked, although you may have to change them for a larger development or production system.

 Note that some people have had to recompile the kernel to get Oracle to work at all. I guess it must depend on the other software that you’re running on the same machine.

 Follow the instructions in the Oracle documentation (on the installation CD in HTML format) and the Linux Kernel HOWTO <http:> to build your new kernel.</http:>

 **2.3.4. Users and groups**

 Using LinuxConf (or whatever other method you feel comfortable with), you need to add a new group called “dba” and a new user called “oracle”, which should belong to your newly created “dba” group.

 You can make any other user a DBA by putting them in the DBA group. If you have several DBA’s this is probably a good idea for auditing purposes.

 **2.3.5. Installing the right Java Virtual Machine**

 Oracle were obviously stung by Java on their first release. All full release of 8i since 8.1.6 have included their own virtual machine so you don’t need to get your own. In fact, make sure that you remove any reference to Java you currently have (you don’t need to delete it, just remove it from your PATH and make sure that no other variable, such as JAVA\_HOME or CLASSPATH, are set). The installer is temperamental enough without adding more variables.

 If you’re installing 8.1.5, read on:

 If you check the official documentation, you’ll find that Oracle recommend the Blackdown Java Runtime Environment version 1.1.6v5. That’s what they mean. Don’t think ‘newer versions will be less buggy’ as the installer probably won’t work. And don’t think, ‘I’ll be developing software so I’ll just get the JDK,’ as that won’t work either.

 There is one caveat to using this version of the JRE: the Oracle installer seems to be hard-coded to expect the JRE executable to be at /usr/local/jre/bin/jre. While this is inconvenient, it does not mean that you have to install it there.

 I performed the following steps to get a working copy of the JRE:

1. Download the Java Runtime Environment from the Blackdown website <http:></http:>
2. Move to where you want to install the JRE:  `cd /usr/local`
3. Uncompress the archive:  `bzip2 -d -c jre-1.1.6-v5-glibc-x86.tar.bz2 | tar xvf -`
4. Create a symbolic link between where Oracle thinks it is and where it actually is:  `ln -s jre116_v5 jre`

### 2.4. Starting off questions and answers

 **2.4.1. Do I really need 128Mb RAM?**

 I would recommend that you do use 128Mb of RAM or more. I think it would be difficult to get any serious work done with less.

 However, if you disable the Java option and set all the shared memory settings to be relatively small, there’s no reason why it shouldn’t work. I’ve heard success stories with 64Mb. You’re probably not going to get away with 32Mb, though.

 There is a caveat. You may only need half of what Oracle recommends to run the thing, but to install it their number starts to make sense. I’ve heard reports of the installer using 150Mb of memory and I’ve seen it well over 120Mb myself. If you have 64Mb or less of memory, make sure you have lots of swap space and patience.

 An alternative if you absolutely can’t add more memory: install Oracle on another, bigger machine and copy across the $ORACLE\_HOME directory. You’ll need to make sure that you have all the same users and groups (preferably with the same numeric codes) and take special care with SUID executables like $ORACLE\_HOME/bin/oracle.

 **2.4.2. Does it work with Debian/SuSE/Mandrake/some other distribution?**

 Oracle specify the Linux kernel version 2.2 or above and GLIBC version 2.1 with any window manager. In theory, any distribution that meets these requirements should work.

 In practice, unless Oracle have certified you distribution they may not support it and you may have more problems trying to complete the installation. Unless you have a very good reason to do otherwise I suggest you stick to RedHat Linux 6.x with all the patches you can get hold of.

 For the record, I’ve heard success stories will all those distributions. Some, however, consistently cause problems, Slackware being the main culprit.

 **2.4.3. Does it work with GLIBC 2.2 distributions?**

 At the moment, RedHat Linux 7.x and other distributions based on GLIBC 2.2 are known to be fairly problematic. It is possible to make it work, however. To avoid “clutter” in this document I’ve included the details on my website <http: howto="">.</http:>

 **2.4.4. Does it work with development kernels?**

 There’s no obvious reason why it shouldn’t work — I used 2.3.19 for a while because it supported my network card and the stable kernel at the time didn’t — but unless there’s a pressing need it’s certainly safest to stay well clear. I switched back to the stable series as soon as the driver was included.

 **2.4.5. Does it work with Linux 2.4?**

 The current stable kernel has a number of features and performance improvements over the 2.2.x line that Oracle could benefit from. Can you use it without risking disaster? The answer is definitely “yes.”

 Generally the kernel is upwardly compatible with 2.2.x and I’ve not heard of any significant problems with any of the more recent 2.4 releases (although some of the early ones are almost certainly worth avoiding).

 **2.4.6. Does it work with Linux 2.5.x and 2.6?**

 At the time of writing, the 2.6 kernel is just enter its beta testing phase, so the same advice as for previous development kernels applies here too. Summary: no technical reason why you can’t use them, but not recommended especially in a live environment.

 **2.4.7. Where do I get Oracle from?**

 Firstly, if you’re brave, have a very fast Internet connection or inexhaustible patience (and unmetered access) you can download it from Oracle Technology Network <http:></http:>. Beware: 8.1.5 is nearly 200Mb, and 8.1.7 is nearer 500Mb.

 A better option is to get the CD. Oracle sometimes offer to send you a free development CD when you join Technet. It’s certainly worth spending some time looking round their web site for that. Alternatively, you can buy them from the Oracle Store for around $40. It includes lots of other software too and comes on 15 discs.

 **2.4.8. What if I just want to connect to an Oracle database?**

 If you have an Oracle database on another machine and just want to connect to it from another Linux machine, the process is very similar to that described here but with less of the complex stuff.

 Oracle tend not to distribute an Oracle Client CD for anything other than Windows. Instead you just use the same Oracle Enterprise CD and select the “Oracle Client” or “Oracle Developer” (not to be confused with the Oracle Developer product) when it asks what kind of installation you want.

 All the other advice, about using the correct version of Linux, the Java distribution, etc, are all just as pertinent for the client install as for the server, since the same installer is used.

### 3. The installer

### 3.1. How?

 Generally, following the documentation is a good idea. It’s not that bad and you’ll get much better support from Oracle if you have. (I ended up breaking things — and knowing it would — by following the documentation for Oracle Applications. It was the only way to get decent support.)

 This document is going to give an overview, but you should still have their documentation available.

### 3.2. What do I tell the installation program?

 As part of the installation Oracle will ask a number of questions. Generally they’re not too difficult but let’s see what I entered and why.

1. Many people make the mistake of following Oracle’s documentation and, therefore, fail at the first hurdle. Don’t execute runInstaller as it almost always fails. Instead move to install/linux on the CD and run runIns.sh while logged in as ‘oracle’.
2. It should show a title screen. Click ‘Next.’
3. It should ask you to enter the source directory of the installation files (‘jar’ file) and your Oracle installation directory. You should be able to leave the former alone. The Oracle home directory is where you want to install the software. According to the installation documentation is should be somewhere on /u01, but I ignored that and put it in /home/oracle. Oracles advice, in this respect, is usually worth following. Click ‘Next’ when you’ve entered the details.
4. Now it should ask you for the DBA group. This is the Unix group you created in the last section and is probably ‘dba’. Enter the details and click ‘Next.’
5. This time it wants you to log in as ‘root’ and run /tmp/OraInstall/orainstRoot.sh. Do as it says. (You may have to run pdksh or bash in the ‘Bourne compatibility mode’ to get it to complete successfully.) When you’re done click ‘Retry.’
6. You’re now given the option of what to install. Your best bet here is ‘Oracle Enterprise Edition,’ as this includes just about everything (table 3.1 in the Oracle documentation tells you exactly what it installs). Make sure the right radio button is selected and click ‘Next.’
7. It should now allow you to choose what you install with much finer granularity. Unless you’re particularly constrained by disk space or know exactly what you need, I’d recommend leaving it exactly as it is and clicking ‘Next.’ The Universal Installer won’t let you make any silly choices so don’t worry too much if you unselect something. You can always add it back in later.
8. For any products that you’ve asked it to install, the installer will allow you to change where it puts them. Again, only if you have a good reason to should you change it. Click ‘Next’ when you’re done.
9. It now goes away and installs all the pieces of software you asked it to. This will probably take quite a while and will use far more memory than is reasonable.
10. It should ask you if you want to create a database. Select when it does, it’s very slow (it seems to fire up another JVM, leaving X, the Oracle back-end and *two* virtual machines in memory; not good with 128Mb of memory).
11. The installer should now ask you about the network protocols that you want Oracle to support. The boxes all came up blank for me. I don’t know what’s supposed to be in there, but I clicked ‘Next’ and found that everything worked.
12. All the hard stuff is complete now. All the products you want should be installed and are ready to go. Congratulations.

### 3.3. Installing the patch

 Unfortunately, the CD that Oracle sent you was probably version 8.1.5.0.0. As with almost all first releases there are problems with that version (problems include empty files, so they’re quite serious) and a patch, to version 8.1.5.0.2 is essential. You’ll certainly need it to progress to the “Configuration” section of this HOWTO. The patch described here is a cumulative patch, i.e., it includes all the files required to move from version 8.1.5.0.0 to 8.1.5.0.2.

 The file you need is on the Oracle web site <http:> and is relatively easy to install.</http:>

1. This is probably the first of many patches, so create a directory called “patches” somewhere convenient (mine is in $ORACLE\_HOME).
2. Download the file into it.
3. Create somewhere to put the files:  `mkdir /tmp/orapatch<br></br>     cd /tmp/orapatch`
4. Uncompress the file:  `tar zvxf $ORACLE_HOME/patches/linux815patches.tgz`
5. Run the shell script that’s now in the current directory:  `./linux_815patches.sh`

 Note that it’s important not to uncompress the file in the current directory. The patch installer checks that the correct number of files are present and fails if there are not the right number. Of course, if it finds the patch archive it finds too many files!

### 3.4. Setting up your environment

 Add the following lines to your “.profile” (or whatever the equivalent is for your shell):

 `. oraenv   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME/lib`

 Quite why the Oracle installer doesn’t do this I have no idea.

 If you see “\[: integer expression expected before -lt” the next time you log in, it’s because ‘oraenv’ is expecting your ULIMIT to be an integer rather than the default ‘unlimited.’ I’ve seen no ill effects by ignoring the error, but you can fix it by setting the ULIMIT to something finite.

### 3.5. Installations questions and answers

 **3.5.1. The installation program exits with ‘CreateOUIProcess()’**

 Firstly, make sure that you’re running the right version of the JVM. I don’t know what Oracle do with their software, but it’s very dependent on the version you use.

 Secondly, it might help if, instead of running runInstaller from the root of the CD, you move into install/linux and run the runInst.sh shell script instead.

 This problem seems more common on RedHat Linux 6.1 than 6.0 and could be something to do with a newer C library.

 I’ve also heard reports that if you have the wrong version of Gnome’s usual window manager, Enlightenment, you might get this problem. Upgrade or switch to another environment such as KDE or Fvwm2.

 **3.5.2. The installer just flashes on the screen and then vanishes**

 This is not an uncommon occurrence. Usually it means that you’re running an old version of Enlightenment. Upgrading or switching to another environment should fix the problem.

 A similar problem is the installation program vanishing at some later point in the process, often around 80% of the way through. The consensus seems to be that Oracle ran out of memory. You should increase the amount of swap space your machine has, anything over 200Mb should be sufficient.

 **3.5.3. Strange Java errors when I start the installation program?**

 Which version of the Java Virtual Machine are you using? People have claimed success with other versions, but most of the problems that I had disappeared when I downgraded to JRE 1.1.6v5, the one that Oracle recommends in their documentation.

 Two other things that are worth mentioning: make sure you use the JRE and not the JDK and, secondly, you should be using “green” threads. Unless you’ve set THREADS\_FLAG to ‘native’ you almost certainly have the correct setting.

 **3.5.4. The installation program ‘Segmentation Fault’s**

 You do have GLIBC 2.1 don’t you?

 **3.5.5. Problems loading shared libraries**

 The error message that I’m talking about looks a bit like this:

 error in loading shared libraries: libclntsh.so.8.0: cannot open shared object file: No such file or directory

 This is the same as NT complaining that it can’t find a DLL. It’s very easy to fix. Simply add the following line to the end of your “.profile” if you’re using a Bourne-like shell (ask a local guru if you don’t know):

 `export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME/lib`

 Or use the following line if you’re using a CSH-like shell:

 `setenv LD_LIBRARY_PATH "$LD_LIBRARY_PATH   $ORACLE_HOME/lib"`

 I don’t use the C-Shell, so independent verification of this command would be appreciated.

 **3.5.6. Pro\*C doesn’t work**

 The answer to this took quite a bit of tracking down, although the answer *is* on the Oracle web site if you look hard enough.

 The default configuration of Pro\*C doesn’t know where to find all its libraries, so you need to tell it. After installation $ORACLE\_HOME/precomp/admin/pcscfg.cfg is empty, but it needs to contain the following:

 `sys_include=(/home/oracle/precomp/public, /usr/include,   /usr/lib/gcc-lib/i386-redhat-linux/egcs-2.91.66/include/,   /usr/include, /usr/lib/gcc-lib/i386-redhat-linux/egcs-2.91.66/include,   /usr/include)   include=(/home/oracle/precomp/public)   include=(/home/oracle/rdbms/demo)   include=(/home/oracle/network/public)   include=(/home/oracle/plsql/public)   ltype=short`

 (The first four lines above, from sys\_include to include) should all be on the same line in the file.)

 The Oracle documentation doesn’t mention this, but you also need to edit $ORACLE\_HOME/precomp/lib/env\_precomp.mk. On the line that defines CCPSYSINCLUDE, put the following:

 `CCPSYSINCLUDE=sys_include='($(ORACLE_HOME)/precomp/public,/usr/lib/gcc-lib/i386-redhat-linux/egcs-2.91.66/include,/usr/include/g++-2,/usr/include)'`

 This works for RedHat Linux 6.0, but may need tweaking for other distributions or later versions of RH.

 **3.5.7. I installed the patch but it made things worse!**

 This is tricky, barely documented by Oracle and common across all their products and installation programs. It’s about time they did something about it!

 Often what happens is as follows: you install Oracle Enterprise Edition and, as Oracle tells you, you dash off and install all the available patches. Then you decide you need the pre-compilers and install Oracle Programmer from the same CD.

 Before you installed Pro\*C your database worked, and now it doesn’t.

 The problem is that the versions of the pre-compilers that you installed were not patched and some of the Oracle server code relies on the fixes; Oracle’s installer is so stupid that it will overwrite newer version of the same code.

 The solution is not pretty. Since you can’t extract an individual file from the CD you need to install the whole thing again, this time adding Oracle Programmer before the patch.

 **3.5.8. Oracle thinks I don’t have enough disk space**

 There’s something wrong with the installation program. Assuming you *do* have enough space it will install okay.

### 4. Creating a database

### 4.1. Overview

 Hopefully you followed the advice from the previous section and didn’t create a database.

 For most people, I can probably outline the process in a couple of words: “Run ‘dbassist’.” Unless this is the first time you’ve ever run Oracle, none of the questions should really phase you.

 For completeness, I’ll document what I did but I’d best say what I was aiming for first. Bottom line: this is neither a production system nor a ‘serious’ (i.e., several people, full time) development box. I installed 8i to play around and see what was new or different from 8 and older versions.

 This means that when ‘dbassist’ offered an easy option I took it. And when it suggested using a different disk, or at least a different partition, I declined. My $ORACLE\_HOME is /home/oracle. All the data files and software are in there, all on one partition.

### 4.2. Step-by-step guide

1. 1. Bring up a command prompt and type:  `dbassist`
2. My machine tells me that “JNLS Exception: oracle.ntpg.jnls.JNLSException. Unable to find any National Character Sets.” According to Oracles 8i Patch FAQ, this is a known problem (884001) and can safely be ignored.
3. Select the “Create a database” radio button and press “Next”
4. There are two options: Typical and Custom. If you knew exactly what you were doing you probably wouldn’t be reading this and could comfortably select Custom. I’m not going to cover that. Instead I’ll assume you select “Typical” and press “Next”
5. Next it asks whether you want to copy the database from your CD or to create the data files. Whenever I tried the first option, Oracle couldn’t find my CD player (you just installed from it!). So I recommend choosing the second option. It’s not difficult, it probably just takes longer
6. It’s probably safe to select ‘Hybrid’ when it asks you what environment the database will operate in
7. Now it asks you how many users will be using your database at any given time. I put five.
8. Next it asks you what products you want to install in your new database. Again, you know what you want better than me! v
9. Oracle needs a “Global Database Name” and a “SID” now. The database name is like a fully qualified domain name (but different). If you’re the Oracle guru you’ll know what to put, if not your organisation might have some conventions. I called mine ‘dev1’ (both the SID and database name).
10. Now, do you want to create the database ‘now’ or should you let it save the information to a shell script? With 128Mb of RAM I found the former option painful.  I created the shell script, quit out of X and anything else using a lot of memory and then ran the script. Much more snappy.
11. I didn’t notice this in any of the documentation, but your database won’t work properly without it! The database that ‘dbassist’ creates is fine, but by default the user rollback segments are left off-line. (Read: non-system users can’t perform any operation that requires transactions.)  Type:
    
     `cd $ORACLE_HOME/dbs`
    
     You now need to edit a file called “init<sid>.ora” (“initdev1.ora” in my case).</sid>
    
     About half-way down the file is a commented out line looking something like this:
    
     `# rollback_segments = (r01, r02, r03, r04)`
    
     Uncomment this line (remove the hash), save the file and you’re done.
12. This is a kind of meta-step. You have a database and you should be able to start it up, but you probably don’t know what any of the system passwords are!  There are two that you need to know. The first is the SYSTEM password. This defaults to ‘MANAGER’. (It seems to be conventional to put Oracle passwords in uppercase. In fact passwords are not case sensitive.) I recommend you change it straight away by typing password at the SQL\*Plus prompt. (For people expecting an ALTER USER command, this is new to the version of SQL\*Plus supplied with 8i.)
    
     The other password that you need to know is the one for SYS. It defaults to ‘CHANGE\_ON\_INSTALL’ and you should do exactly what it says!
13. Final step. This one gets rid of the annoying ‘no profile’ warnings you get when you log into SQL\*Plus.  Log into SQL\*Plus as user ‘system’ (sqlplus system/<password>). Then type:</password>
    
     `@?/sqlplus/admin/pupbld.sql`
    
     The question-mark is an alias for the $ORACLE\_HOME directory.
14. This is an optional step used to define the default editor for SQL\*Plus (it defaults to ed so you do!). Open $ORACLE\_HOME/sqlplus/admin/glogin.sql in your favourite editor and add define\_editor=<editor name=""> to the end.</editor>

 And that’s it. You should now have an operational database that you can log into using SQL\*Plus.

### 4.3. Questions and answers

 **4.3.1. Is it really that easy?**

 Yes and no. If you’re just playing around, building a database for yourself to learn the new features of 8i, then ‘yes.’ The database the above instructions will build is complete and will work fine.

 However, if you know anything about Oracle, you will quickly realise that the default configuration is appallingly bad. If you’re making a serious, production system I recommend you use the “Custom” option.

 Even for my toy system I did some tweaking. I increased the sizes of most of the table-spaces and changed them so that they didn’t grow automatically (I hate software when it tries to be too clever).

 **4.3.2. Is it really necessary to put all the files on different disks?**

 No and it will work fine if you don’t, but I don’t recommend putting all your files on the same disk nevertheless.

 Spreading the files over a number of disks, even it’s just the data files on one and the rollback segments on another, will have a significant performance advantage. Read an Oracle DBA book if you need further information.

 **4.3.3. I can’t start dbassist**

 Caused by several zero-length files in the initial installation. Following the patch procedure will fix this problem.

 **4.3.4. I get “ORA-01034: ORACLE not available”**

 To cut a long story short, your $ORACLE\_SID is probably set incorrectly or not at all. Make sure it’s set to the same value you gave ‘dbassist’ and that it’s value is exported (i.e., export ORACLE\_SID in any Bourne compatible shell).

 **4.3.5. I get “ORA-01012: Not logged in”**

 This is a very common error, and there are a number of different things that cause it.

 Firstly you’ll want to make sure that you’re not creating a Shared Server configuration (sometimes known as MTS). Create a database using Dedicated Server and convert it later.

 If that’s not it, check your NLS\_LANG environment variable. The easiest option is to unset it. If you really want to use it, make sure that you have it exactly right. Make sure you don’t transpose any ‘1’s (one’s) for ‘l’s (the twelfth letter of the alphabet)!

 **4.3.6. Can data-files only be 1Gb in size?**

 this to be a bug as Linux has no problem with files up to 2Gb.

 Note that does not limit the size of your database to 1Gb or less. A database is made up of many table-spaces which can be made up of many data-files. Talk to your friendly DBA for more information.

 **4.3.7. Can I use raw files?**

 Recent versions of the Linux kernel allow applications to directly access the disks. Oracle is able to use this facility and can (sometimes) increase its performance.

 Technically the answer is ‘yes,’ you can use raw files. But realistically the answer is ‘no.’ The performance improvement you’ll get probably isn’t worth the administrative overhead.

### 5. Configuration

### 5.1. Overview

 Congratulations, you have Oracle running on your Linux box. You have created a database and can connect to it using SQL\*Plus.

 Of course, this is not the end of it. Ideally, you’d be able to connect to it as another Unix user or from a completely different machine. That is what this section is for.

### 5.2. Connecting as another user

 Some of the details in this section are a little sketchy as this is not a configuration that I personally use. However, performing one of the following steps should work:

1. `. oraenv`
    
     or pdksh)
2. `source coraenv`
 When running “oraenv” I get an error if I use ‘bash’, the default Linux shell. It seems not to cause any problems so don’t worry. You can always use ‘pdksh’ if it *does*a worry you.

### 5.3. Connecting from another machine

 I remember this being very complex with earlier versions of Oracle, but just seemed to work here. I’m sure that must mean that I did something wrong, forgot something I did or that there’s a massive security hole.

 This is what I remember doing:

1. Logging into Linux as user ‘oracle’
2. Make sure that “oraenv” has been executed (i.e., your $ORACLE\_HOME is set correctly)
3. Type:  `lsnrctl start`

 On your client machine all you need to do now is point it at the right machine and database instance.

 If you want more control over the process, the “Net8 Configuration Assistant” (‘netec’) should be able to help.

### 5.4. Connecting to another machine

 This used to be very difficult in many earlier version of Oracle, involving editing many text files, most of which had an fantastically complex syntax.

 But in 8i, if you’ve got your JVM working, then all you need is the “Net8 Easy Config” program. Follow these steps to allow your machine to connect to a database on another machine:

1. Start “Net8 Easy Config” by typing netec at the command prompt while logged in as ‘oracle.’
2. After a short delay while Java gets its act together, the welcome screen appears. It should be asking what you want to do. Leave the radio buttons on the left alone (the default is ‘create’) and enter the name of the database in the text box. Click ‘Next’ when you’re done.
3. Select one of the protocols it offers. Unless you know differently, this should probably be ‘TCP/IP’ which is the default. Press ‘Next.’
4. Enter the hostname (or IP address) of the remote machine. The port number probably doesn’t need changing. Press ‘Next.’
5. Select the type of database (8i or other) using the radio buttons and enter the name in the appropriate text box. Press ‘Next.’
6. You can now test that the information you’ve enter makes sense to Oracle. I found that ‘netec’ has a tendency to crash if some of the details are wrong. Press ‘Next’ when you’re sure that it all works. You can keep pressing the ‘Back’ button to go back and correct any information.
7. If you’re happy with all the information you’ve entered, you can press the ‘Finish’ button and that’s it! If you want more control over the process, you may need to use the “Net8 Assistant” — a big window with many confusing options — which can be started with the netasst command.

### 5.5. Questions and answers

 **5.5.1. I can’t start ‘netasst’**

 The problem is with a couple of zero-length files. Installing the patch should fix this problem.

### 6. Final Words

### 6.1. Useful Software

 Now that you’ve managed to get Oracle installed, you’ll want to try and use it. Although it’s possible to do everything from your server PC, it’s generally best to user the client-server facilities and use another machine to access your database.

 Naturally Oracle have a large collection of, largely, pretty good client software, however there’s not much for Linux at this time. The main useful piece of software, Oracle Enterprise Manager, usually comes with Oracle.

 But most of the best software comes from other places…


- Tool for Oracle Application Development (T.O.A.D.). This used to be free but is now owned by Quest Software <http:>. You can download a free version (if you’re prepared to do it every couple of months) or you can pay for it. When I’m using Oracle on a daily basis, this is the program I choose if I have to use a Windows desktop. It’s not as polished as some, but it does just about everything you need.</http:>
- TOra <http:></http:>. This is the closest you’ll find to a TOAD for Linux. In fact, in some ways it’s better than TOAD! The Linux version is free, but you can also buy a Windows version.
- SQLNavigator. Also by Quest Software <http:>. I’ve not really used it but it’s been highly recommended by all who have.</http:>
- OraSoft <http:>. These guys produce applications for Oracle that actually run on Linux. I’ve not used them in anger, but they look good.</http:>
- Orac <http:></http:>. Another that I’ve not used much, but has been described as a nice, configurable DBA-tool by a number of people.

### 6.2. Useful Books

 I seem to get most of my Oracle information from colleagues and books. I’m not able to give away my colleagues, but the books I recommend are as follows:

- “Oracle Essentials,” Rick Greenwald, R. Stackowiak, Jonathan Stern, O’Reilly and Associates, ISBN 1-56592-708-7.
- “Oracle 8i: The Complete Reference,” Kevin Loney and George Koch, Oracle Press, ISBN 0-07212-364-8.
- “Oracle Performance Tuning,” Mark Gurry and Peter Corrigan, O’Reilly and Associates, ISBN 1-56592-237-9.
- “Oracle Design,” Dave Ensor and Ian Stevenson, O’Reilly and Associates, ISBN 1-56592-268-9.
- “PL/SQL Programming,” Steven Feuerstein, O’Reilly and Associates, ISBN 1-56592-335-9.
- “PL/SQL Built-in Packages,” Steven Feuerstein, O’Reilly and Associates, ISBN 1-56592-375-8.
 You’ll find some more [book recommendations and reviews on my web site](http://www.zx81.org.uk/computing/opinion/).

### 6.3. Useful Internet resources

 There’s a lot of useful stuff on the web.

- Oracle Technet http://otn.oracle.com. This is Oracle’s public and free support website. Lot’s of very useful information there.
- Oracle Metalink http://support.oracle.com. Oracle’s private (you need a support contract) support website. Only slightly more useful than Technet!
- If this HOWTO hasn’t worked for you, there are a couple of other’s that you might like to try: Jesus M. Salvo, Jr.’s <http:> and Tom Bissett’s <http:></http:> slightly dated guide. Or there’s a bulletin board <http:></http:> on my website if you still need to ask questions.</http:>
- OraFaq http://www.orafaq.org. A site full of questions and answers regarding Oracle on all platforms.
- Oracle Linux mailing list (Send a mail to ListGuru@fatcity.com <listguru> with the words ‘SUBSCRIBE ORACLE- LINUX-L’ in the body.</listguru>
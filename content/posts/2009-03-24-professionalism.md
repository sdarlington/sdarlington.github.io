---
id: 1039
title: Professionalism
date: '2009-03-24T20:22:22+00:00'
author: 'Stephen Darlington'
excerpt: 'When people talk about "professionalism" is that really what they mean?'
layout: post
guid: 'http://www.zx81.org.uk/?p=1039'
permalink: /computing/opinion/professionalism.html
categories:
    - Opinion
tags:
    - computerscience
    - management
    - Programming
    - work
---

A few years ago I was subcontracted to one of the large consultancies. I was taking over from someone who was, supposedly, quite senior and the task at hand, I was told, was very hard. I should take copious notes as she wouldn’t necessarily be around afterwards to help me. Making a mistake or missing out any one step could be disastrous to the whole process. If I did everything properly each new installation would take about a week.

This turned out not to be entirely correct.

After sitting through over a week of her spelling out each and every step in excruciating detail — much of which I don’t think she really understood — I spent three days writing a shell script to automate over ninety percent of the process. I don’t mean a quick, shoddy hack either. I spent the time to gold-plate it. It was a work of art. I set it up so that you only needed to copy the one file and allowed for the user forgetting to switch FTP into binary mode ((I basically appended a tar’d and uuencoded file to the end of the shell script which it knew how to extract and decode.)).

In the end, my three days of work reduced the week long process to about an hour, and most of that was waiting for the file to transfer over the network.

I say all this not to show off. I think any engineer would have thought to do this. I note the extra refinements so you realise that it could have been done in much less than three days had I not wanted to practice my Unix-fu.

Result: I was heavily criticised for not following the proscribed process. I pointed out that my new scheme was quicker, easier and less error-prone. They countered that I had been *unprofessional* to begin a “development project without authorisation.”

What does “professionalism” mean to you?

Sometimes, I think, it’s used as an excuse to do or not do something in a particular way. “That’s not professional” is kind of a cop-out. In this case I can only assume that the real reason was that they wanted to bill a week of my time to the client for each installation. Of course they couldn’t *say* that.

Since then, every time I hear the phrase “that’s not professional” I try to drill down and find the real, underlying reason. I’m hoping that one of these days I won’t be disappointed with what I find. It hasn’t happened yet.
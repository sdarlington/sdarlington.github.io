---
id: 4225
title: 'The &#8216;D&#8217; in &#8216;DVCS&#8217;'
date: '2015-04-07T21:23:13+01:00'
author: 'Stephen Darlington'
excerpt: 'When GitHub is down, there''s no need to stop working...'
layout: post
guid: 'http://www.zx81.org.uk/?p=4225'
permalink: /computing/opinion/the-d-in-dvcs.html
categories:
    - Opinion
---

Last week, GitHub was the victim of a [days long denial of service attack](https://github.com/blog/1981-large-scale-ddos-attack-on-github-com) that meant that it wasn’t available reliably despite the hard work of their team.

What surprised me was the number of people on Twitter complaining that they couldn’t work. I was surprised because one of the key things about Git (the tool rather than the website) is that it is *distributed*, that is there is no centralised server in the way that there is with, say, Subversion. Clearly there are things you *can’t* do without GitHub – most obviously downloading new repositories – but almost everything else can be done peer-to-peer. The rest of this post explains how.

First, a couple of disclaimers. I’m not a Git expert and I’m not a server admin. There certainly are other ways of doing this. Some may even be more secure or easier in *your* environment. What I like about this approach is that it works on pretty much any machine that has git installed.

Step one: set up a Git server.

“Woah, now,” you’re thinking, “I don’t have all day!”

Turns out it’s just two commands:

```
touch > .git/git-daemon-export-ok
git daemon

```

(Assuming you’re in the folder that’s at the root of the repository you want to export.)

Then on your other PC you can enter the following command to pull or push:

```
git pull git://othermachine/Users/stephend/temp/

```

You could even clone a repo to a local server, run a git server on it and use it as a temporary ’central’ repository.

If there’s a downside it’s that it’s difficult to recommend *pushing* to a repository using this method because there’s no authentication. However, as a quick and dirty way of pulling commits between any two machines with git installed it’s pretty reliable.

(If you know git you’re probably thinking “Why not ssh?” The short version is that it’s often locked down in corporate machines and is usually not available on Windows machines. But if you *can* use it you probably should.)
---
id: 1932
title: 'Programming Is Hard'
date: '2011-01-18T18:51:08+00:00'
author: 'Stephen Darlington'
excerpt: 'Much of what a programmer does is a mystery to most people. Here I try to explain, with a simple example, some of the things that go on.'
layout: post
guid: 'http://www.zx81.org.uk/?p=1932'
aliases: ['/computing/opinion/programming-is-hard.html']
image:
    - ''
embed:
    - ''
seo_follow:
    - 'false'
categories:
    - Opinion
tags:
    - Computing
    - development
    - iphone
    - mac
    - objectivec
    - Programming
---

It’s hard to explain to someone who is not already a programmer the kinds of things that you have to do when building an application. The thing you’re trying to explain is often very abstract and the answer frequently would involve lots of code.

That’s why I thought this particular problem might make an interesting discussion. In talking about this very simple problem we can talk about the things that developers deal with every day and, hopefully, the process can be followed by most people who have used an iPhone (or, actually, any computer). You won’t be a programmer at the end but you might have a greater appreciation for what happens behind the scenes.

The basic problem can be seen in this screen shot.

[![](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2011/01/Screen-shot-2011-01-16-at-18.50.57-159x300.png?resize=159%2C300 "Log in button")](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2011/01/Screen-shot-2011-01-16-at-18.50.57.png)

The login button is a toggle. That is, if I’m currently logged in it says “Log out.” And when I’m not logged in it says “Connect,” which is “log in” in Facebook parlance. A subtlety that you might not ordinarily notice is that when the user clicks the button, the keyboard should move out of the way when it’s not needed and come back again when it is.

There are two basic cases to consider:

- When I’m not already logged in. In this case pressing the button opens the login screen and the keyboard should shift out of the way.
- When I am logged in, pressing the button just logs me straight out. In this case the keyboard can stay where it is.

Easy, eh? (That’s what I thought when I started, too.)

Let’s sketch out the code.

``

```

when the button is pressed
  if I'm not logged in then
    make the keyboard move out of the way
    log in
  else
    log out
```

This is called *pseudo code* because while a computer can’t actually execute it we’ve broken down the processing into the required basic steps. You’ll have to trust me when I say that the real code (called Objective-C) isn’t terribly different.

Not so hard.

Except… you didn’t really think it would be that easy, did you?

It turns out we’re missing one important detail from our algorithm.

One thing we do a lot when programming is use pre-existing components (standing on the shoulders of giants as Isaac Newton, or Oasis, would have it). When you write a component you’re going to come at the problem with some specific ideas of how it’s likely to be used. Hopefully these ideas are the most common ones as this will make everyone else’s life significantly easier.

In this case, our button — a pre-existing component that I didn’t write — is a clever one. It already “knows” how to log in and log out of the service. This sounds like a great time saver and it simplifies our algorithm to just this:

``

```

when the button is pressed
  if I'm not logged in then
    make the keyboard move out of the way
  else
    do nothing
```

Only, it turns out that that doesn’t work.

Why not? Well, the implicit assumption in the above pseudo-code is that it is run *first*, that is, before the instruction to log us into or out of the service. But if the button logs us out before any of my code is run then no matter whether I was logged in or not before I pressed the button, the above code will find that we’re logged out and move the keyboard out of the way.

When you’re writing a user interface you find dozens of these tiny little details getting in the way of what you’re trying to do. Any non-trivial screen will have lots of these little problems, and the worst thing? No-one will ever know. If you do your job well no user will ever see these little glitches.

Talking of which, how do we eliminate the anomaly that we’ve just found? The solution is pretty simple. At the moment we’re trusting that the button “knows” whether we’re logged in or not. Instead, we’re going to have to take responsibility for doing that as well. That adds a little bit of complexity but isn’t too scary:

- When the screen opens we need to check whether we’re logged in or not and remember that. In Objective-C we call that a “variable,” but really that just means something that we’re going to store and access again later
- Later, when the button is pressed we can use the following pseudo-code:  
    `<pre>if the value I saved says that I'm not logged in then  make the keyboard move out of the wayelse  change the stored value to "not logged in"</pre><p></p>`
- When I’ve finished logging in — remember I could press the cancel button in the log in screen — change the stored value to “logged in”

And that’s it, we’re done. We have a working version of the log in button.

The final point I’m going to make here is that I ended up discarding all the code above. It just didn’t work as well as I wanted and I ended up implementing it in a completely different way. And this really is the kind of detail that you never notice. A good chuck of any programming project is prototyping, building mock-ups and other activities that don’t directly end up in any shipping product. All this discarded work — which does, at times feel like a waste of time — is designed to make the product better.

Some people who have never programmed say things like “there’s nothing complicated there” or “[it’s only a button!](/computing/opinion/the-w-effect.html)” Hopefully this post has shown that even a simple button can be far more work that it initially seems.
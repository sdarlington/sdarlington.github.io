---
id: 4627
title: 'Otto: Assembly'
date: '2017-03-16T21:01:18+00:00'
author: 'Stephen Darlington'
excerpt: 'With the body printed, and the electronics tested, it was finally time to put everything together. Would Otto the robot dance and avoid obstacles?'
layout: post
guid: 'https://www.zx81.org.uk/?p=4627'
permalink: /blog/otto-assembly.html
categories:
    - Blog
---

With all the pieces [printed](https://www.zx81.org.uk/blog/otto-printing.html) or [purchased](https://www.zx81.org.uk/blog/otto-electronics.html), it was time to assemble [Otto](http://www.instructables.com/id/Otto-Build-You-Own-Robot-in-Two-Hours/).

Since I’d already tested the Arduino and enlarged the holes for the eyes and stepper motors, the process of putting it together was actually fairly uneventful.

<figure aria-describedby="caption-attachment-4628" class="wp-caption alignleft" id="attachment_4628" style="width: 300px">[![](https://i0.wp.com/www.zx81.org.uk/wp-content/uploads/2017/03/IMG_4014.jpg?resize=300%2C225&ssl=1)](https://www.zx81.org.uk/blog/otto-assembly.html/attachment/img_4014)<figcaption class="wp-caption-text" id="caption-attachment-4628">Putting Otto together</figcaption></figure>

Because of the small size, some parts were very fiddly but it wasn’t hard *per se*. Kudos to the people who put the instructions together!

I came across three minor problems.

First, I pushed one of the screws in too far, so that it looks as though it has a small horn. I almost did the same thing on the other side so it would, at least, look symmetrical. It’s not a big deal but *I* know it’s there! It’s not worth re-printing the head for so I’ll have to live with it.

Second, the battery pack hasn’t arrived yet so I had to run Otto only when connected to power via USB – a computer works but so did the power brick from our Amazon Fire tablet.

Finally, as I speculated, I think I ordered an incorrect part. Fortunately it was only the buzzer so it isn’t critical. I’ll probably try to fix this soon.

(The buzzer I have didn’t have polarity labels – which I’m not sure is important – and wouldn’t stay put on the end of the cables – which I know *is* a problem!)

With the robot assembled and its head snapped into place, the next thing to try was powering it up and seeing it dance and avoid obstacles.

Had I not played with the electronics separately I probably would have freaked out and assumed it wasn’t working. As I found, it takes a few seconds to download the software and reboot and, unlike before, I couldn’t see any of the lights flashing as they were all now inside Otto.

My patience paid off and he started dancing on the first try. The kids, who had lost interest during some of the more intricate fiddling around that was required earlier on, were suddenly excited again. Actually, make that kids of all ages were excited!

<iframe allowfullscreen="" frameborder="0" height="480" loading="lazy" src="https://www.youtube-nocookie.com/embed/QAmSFaTmCbU?rel=0" width="853"></iframe>

I was impressed that it worked on the first try. The dancing is pretty cool. At one stage I’m its routine it tries to stand on tip-toes and falls over every time. I suspect it would have to be very finely tuned for that ever to work. One of his legs could do with a little calibrating but it works well enough.

Next I uploaded the “obstacle avoidance” program. I found this a little less reliable than the dancing, but it did walk, then stop and tap its foot when you wave your hand in front of its eyes. Looking at the code, I wonder the buzzer adds something?

Overall, it was a great little project. “It works” is a pretty boring conclusion, but it’s true. I expected far more to go wrong. I’m happy that it didn’t.
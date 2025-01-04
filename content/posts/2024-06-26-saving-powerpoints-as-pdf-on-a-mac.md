---
id: 93914
title: 'Saving PowerPoints as PDF on a Mac'
date: '2024-06-26T17:22:00+01:00'
author: 'Stephen Darlington'
excerpt: 'Replacing one mind numbing task with another. Winning?'
layout: post
guid: 'https://www.zx81.org.uk/?p=93914'
permalink: /computing/opinion/saving-powerpoints-as-pdf-on-a-mac.html
categories:
    - Opinion
tags:
    - mac
    - PowerPoint
    - Programming
---

The background story: I’m preparing to deliver a training course. Each module of the course is in a different PowerPoint deck and, once I finished, I need to export each of them as a PDF to share with delegates. There are about twenty modules so doing this wouldn’t take *that* long but I would probably consider using the word “mind-numbing” to describe the process.

In hindsight, I’m not sure that writing VBA code to automate it was significantly less mind-numbing, but I’m sharing it here so you don’t have to.

```
Sub printAllPresentations()
  For Each pres In Presentations
      pos = InStrRev(pres.Name, ".")
      filename = pres.Path & "/" & Left(pres.Name, pos - 1) & ".pdf"
      pres.SaveCopyAs filename, ppSaveAsPDF
  Next pres
End Sub
```

The reason why this was so fraught, I think, is twofold: almost everything you search for on the web is for Windows PCs using Excel and I’m using PowerPoint on a Mac.

Most of the suggestions are to use [Presentation.ExportAsFixedFormat ](https://docs.microsoft.com/en-gb/office/vba/api/powerpoint.presentation.exportasfixedformat)which, as far as I can tell, doesn’t exist on the Mac for some reason. For a long time I tried the [Export](https://docs.microsoft.com/en-gb/office/vba/api/powerpoint.presentation.export) function, which superficially seemed similar, and the equivalent menu option appears to support PDF. The error message you get doesn’t really help, but trial and error showed that you could export each slide as a PNG or JPEG (which actually might be quite useful another time) but not what I wanted now.

Then, I thought, maybe I should just use the [PrintOut](https://docs.microsoft.com/en-gb/office/vba/api/powerpoint.presentation.printout) function, carefully using the PrintToFile option. Don’t try that at home. (If you’re in California and just got a huge stack of slides printing out next to you, sorry.)

None of this is helped by the lack of in-application help, the terrible text editor or the fact that the editor window appeared off screen and wouldn’t come back no matter what I tried. I ended up detaching my external monitor.

Overall, it’s great that I got it working but I won’t be hurrying back to play with VBA again any time soon if I can help it!

*This post was originally shared on Medium in 2018.*
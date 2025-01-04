---
id: 67755
title: 'What are Registers?'
date: '2021-02-20T19:11:00+00:00'
author: 'Stephen Darlington'
excerpt: 'When a statement about CPU hardware on Twitter is too nuanced to discuss in 280 character.'
layout: post
guid: 'https://www.zx81.org.uk/?p=67755'
permalink: /computing/opinion/what-are-registers.html
categories:
    - Opinion
tags:
    - computer
    - cpu
    - hardware
---

When people say that Twitter is a cesspool of conspiracy and abuse, I don’t recognise it based on my experience. *My* Twitter timeline is all jokes and geeky chat<sup>[1](#fn1-25478 "see footnote")</sup>, and that’s where this post takes its cue:

> [When I started learning assembler](https://twitter.com/uliwitness/status/1352972582836953088?s=21), no site ever mentioned what registers were good for. Wish it had said:
> 
> CPU talking to a RAM chip is slow, registers are a bit of memory built into the CPU in which you load numbers from RAM, do several calculations, and only THEN write back.

I said that this was a RISC-centric approach and was challenged to come up with a better definition.

It’s a harder question to answer than I initially thought. Every time I came up with a pithy definition, I thought of an exception. And with every clarification I got further and further away from 280 characters.

With no character limit, what is a register?

Wikipedia says that it’s “[a quickly accessible location available to a computer’s processor](https://en.wikipedia.org/wiki/Processor_register),” which is the definition that I was arguing against. Thanks, Wikipedia.

Nevertheless, I maintain that I’m right. Let’s dig into the definition further.

It wasn’t the “quick access” bit I didn’t like. Registers are faster than main memory<sup>[2](#fn2-25478 "see footnote")</sup>. They’re also faster than on-die caches<sup>[3](#fn3-25478 "see footnote")</sup>.

The RISC-y bit was in the second sentence: loading bits of memory, do a few calculations, write back.

To explain why that’s not always true we have to take a quick tour of CPU design history. By necessity I’ve missed out many details or made sweeping generalisations<sup>[4](#fn4-25478 "see footnote")</sup>. I don’t think this detracts from my point.

First, a quick aside: for the sake of completeness, I should point out that there’s nothing sacred about registers. There are CPU architectures that do not have them, primarily stack-based but there may be others. Let’s ignore them for now.

There have been a few waves of CPU and instruction set architecture design, and the use of registers has changed over that time.

| Processor | Registers | Instructions |
|---|---|---|
| [Intel 4004](https://en.wikipedia.org/wiki/Intel_4004)<sup>[5](#fn5-25478 "see footnote")</sup> | 16 | 46 |
| [MOS 6502](https://en.m.wikipedia.org/wiki/MOS_Technology_6502) | 5 | 56 |
| [Intel 8086](https://en.m.wikipedia.org/wiki/Intel_8086) | 8 | ?<sup>[6](#fn6-25478 "see footnote")</sup> |
| [Motorola 68000](http://fms.komkon.org/comp/CPUs/68000.txt) | 15 | 77 |
| [PowerPC](https://en.m.wikipedia.org/wiki/PowerPC) | 32 | ? |
| [ARM](https://en.m.wikipedia.org/wiki/ARM_architecture) | 31 | ? |

In The Beginning, making a CPU at all was a challenge. Getting more than a few thousand transistors on a single chip was hard! The first chips designers optimised for what was *possible* rather than to make things easy for programmers.

To minimise the number of transistors, there were few registers, and those that were present had predefined uses. One could be used for adding or subtracting (the accumulator). Some could be used to store memory addresses. Others might record the status of other operations. But you couldn’t use the address registers for arithmetic or *vice versa*.

The answer to the question “what is a register for” at this point is that it saves transistors. By wiring up the logic circuits to a single register and having few of them anyway, you could have enough space to *do* something.

As it became easier to add transistors to a slice of silicon, CPU designers started to make things easier for programmers. To get the best out of the limited hardware, many developers wrote code in assembler<sup>[7](#fn7-25478 "see footnote")</sup>. Therefore, making it easier for programmers meant adding new, more powerful hardware instructions.

The first CPUs might have had an instruction to “copy address *n* from memory into a register” and another to “add register 2 to the accumulator.” The next generation built on those foundations with instructions like “add the value at address *n* to the accumulator and write to address *m*.” The complexity of instructions grew over time.

Working on these early machines was hard partly because they had few registers and the instructions were simple. The new instructions made things easier by being able to work directly with the values in memory.

These new instructions were not magic, however. Having a single instruction to do the work didn’t make copying data from memory quicker. Developers trying to eke out the best performance had an increasingly difficult time figuring out the best combination of instructions. Is this single instruction that takes twenty cycles faster than these other three instructions that nominally does the same thing?

Around the same time, writing code in higher level languages became increasingly popular. The funny thing with compilers and interpreters is that it’s easier to write and optimise them when you use a limited set of instructions. All those esoteric instructions that were designed for *people* were rarely used when *computers* wrote the assembler code.

CPU designers figured out that they could make real-world code execute more quickly by heavily optimising a small number of instructions.

This led to completely different CPU designs, called RISC, or reduced instruction set chips. Rather than have a small number of special purpose registers and a large number of complex instructions, RISC insisted on large numbers of general purpose registers and few instructions<sup>[8](#fn8-25478 "see footnote")</sup>. The reduction in the instruction count was partly achieved by making arithmetic operations only work on registers. If you wanted to add two numbers stored in memory, you first had to load them into registers, add them together and write them back out to memory.

At this point, the answer to the question “what is a register for” changed. It became a sensible option to throw away the transistors used to implement many of the complex instructions and use them for general purpose registers. Lacking instructions that worked directly on memory, the definition of a register became “temporary storage for fast computations” — pretty much what we started with.

Since then, the original designs, with lots of instructions and a small number of registers (CISC), and the newer one, with lots of registers and few instructions (RISC), have to some extent merged. RISC chips have become less “pure” and have more special purpose instructions. CISC chips have gained more registers<sup>[9](#fn9-25478 "see footnote")</sup> and, internally at least, have taken on many of the attributes traditionally attributed to RISC chips<sup>[10](#fn10-25478 "see footnote")</sup>.

Let’s loop back to the original question. *Are* registers a bit of memory built into the CPU in which you load numbers from RAM, do several calculations, and only *then* write back?

We’ve seen how registers are not necessary. We’ve see that their importance has waxed and waned. But, if we had to distill the answer down to a single word or sentence, what would that be?

On current hardware, on most machines, much of the time, the answer is: yes, they *are* a bit of memory built into the CPU in which you load numbers from RAM, do several calculations, and only *then* write back.

Was I being pedantic for no reason?

<div class="footnotes">---

1. I appreciate that there’s an element of white, male privilege here. [↩︎](#fnr1-25478 "return to article")
2. Even on architectures like Apple’s M1 chip where the main memory is in the same package as the CPU. [↩︎](#fnr2-25478 "return to article")
3. I’m going to assume you know a fair few concepts here. My focus is more “how did we get here” than “what do these things do.” [↩︎](#fnr3-25478 "return to article")
4. While I’ve mostly done this deliberately, I’m sure I’ve done it by accident in a few places too. [↩︎](#fnr4-25478 "return to article")
5. Four bits wide! [↩︎](#fnr5-25478 "return to article")
6. It was surprisingly hard to get a count of the instructions for most of these. [↩︎](#fnr6-25478 "return to article")
7. Machine code is the list of numbers that the CPU understands. Assembler is one level above that, replacing the numbers with mnemonics. Even the mnemonics are considered impenetrable by many programmers. [↩︎](#fnr7-25478 "return to article")
8. Of all the gross simplifications in this piece, this is probably the biggest. [↩︎](#fnr8-25478 "return to article")
9. I don’t want to get into all the details here but how they’ve managed to do this without substantially changing the instruction set is both fascinating and architecturally horrifying. Rather than add new instructions to address the new registers, they have a concept called “[register renaming](https://en.wikipedia.org/wiki/Register_renaming)” where the register *names*, but not the *values*, get reused. [↩︎](#fnr9-25478 "return to article")
10. Again, without wishing to get into too much detail, modern CISC CPUs typically convert their complex instructions into more RISC-like instructions internally, and execute *those*. [↩︎](#fnr10-25478 "return to article")

</div>
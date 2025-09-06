---
title: 'From Zero to Bug Hunter: My LKMP Journey'
date: 2025-09-05 19:41:02
tags:
---

This is a note recording my experience to the linux kernel mentorship program(LKMP).

<!-- more -->

## Why Learning Linux Kernel?

After several years as a frontend engineer, I became increasingly curious about how systems work at a deeper level. I tried learning operating systems and Linux on my own, but found it quite challenging to maintain momentum without guidance. That's when a friend recommended the Linux Kernel Mentorship Program as an excellent opportunity to both learn and contribute to the kernel.

## Getting Into LKMP

Before getting into LKMP, there are prerequisite tasks that need to be completed. For me, these tasks serve as an excellent guide for a kernel newbie trying to navigate the massive kernel source code. Whether or not you're selected for the mentorship program, I strongly encourage anyone new to the kernel to complete all these tasks.

Details about how to apply, application deadlines, and prerequisites can all be found on the [Linux Kernel Mentorship Program website](https://wiki.linuxfoundation.org/lkmp). If I had to give one piece of advice, it would be to start working on the prerequisites as early as possible. Even if you complete them after the official deadline, don't give up —— just keep working on them until a mentor reviews your submissions. You never know when an opportunity might come your way.

## What I Learned From LKMP

HOW and WHERE to start reading kernel source code? That is the first question that come to mind after I download the kernel source tree. It is honestly quite intimidating at first glance. This is my first time diving deep into system programming —— before this, I am just a web developer without even a computer science degree, and I have only learned C for about three weeks.

Fortunately, I have an amazing mentor, Shuah Khan, along with kernel documentation and a supportive community to guide me through the learning process.

There are several ways can contribute to the kernel:
> 1. Fix documentation typos, grammar mistakes, and other errors
> 2. Resolve compilation warnings or build errors
> 3. Use static analysis tools (Coverity, Sparse, Smatch) to identify potential issues
> 4. Fix bugs discovered through automated testing tools like Syzbot

Through working on these types of contributions, I gain experience in several key areas, and I will discuss each in detail:

### Reading Mailing Lists

Learning to navigate the kernel mailing lists was honestly quite confusing at first. There are so many different mailing lists, and the discussions can get really fast.

But I quickly realize that lore.kernel.org became my best friend. Before I even think about working on any bug or issue, I always check the mailing lists first to see if someone already reported it or fixed it.

The search function on lore is actually pretty powerful once you figure it out. I learned to use some basic search tricks:

```
s: for searching subject lines
b: for searching the actual email content
f: to find emails from specific people
d: to search by date ranges
```

For example, if I find a compilation warning, I will search something like `s:"the-function-name"` to see if anyone already talk about it. Sometimes I find that someone already sent a patch for the exact same issue.

The threading feature is also really helpful. You can follow entire conversations about bugs and see how maintainers think about problems. It's like getting a behind-the-scenes look at how kernel development really works.

### Using b4 to Send Patches

At the beginning, I was using `git send-email` to submit patches. Even though I was already using `get_maintainer.pl` to find the right people, I still had to manually type out all the email addresses in the git send-email command like `git send-email --to=xxx --cc=xxx --cc=xxx`. It was tedious and error-prone.

Then I discover b4, and it simplifys everything! The workflow becomes much easier —— just `b4 send` and it takes care of everything. No more copying and pasting email addresses or worrying about typos in the recipient list.

### Static Analysis vs. Dynamic Analysis

Before LKMP, I honestly have no idea what static analysis or dynamic analysis means. Through using various tools during the mentorship, I finally understand the difference between these two approaches.

Since I'm still quite new to kernel development, I found myself contributing mostly to static analysis findings. The reports are easier for me to understand and fix. When Sparse flags an incorrect function annotation or Smatch finds a potential null pointer dereference, I can usually trace through the code and understand what needs to be fixed.

Dynamic analysis reports from Syzbot, however, are much more challenging for me to interpret. They often involve complex crash dumps and require deeper understanding of kernel internals to debug properly. I'm still learning how to read these reports effectively.

### Trying to Understand the Kernel Internals

One of the biggest challenges for me is learning how to actually understand what the kernel code is doing. Coming from frontend development, diving into kernel internals feels like learning a completely different language.

My approach to learning: start with simple patches, then try to understand the bigger picture. When I worked on a simple patch - like replacing a ternary operator with a helper function - I didn't just fix it and move on. Instead, I used it as a starting point to trace through the code.

For example, when I modified a function, I started tracing backwards to see how it gets called, then looked up the relevant documentation to understand what that subsystem is supposed to do. This helped me see how my small change fits into the larger kernel architecture.

But honestly, there's still so much I don't understand. The kernel is massive, and each subsystem has its own complexities. Sometimes I feel like I'm just scratching the surface, but at least now I have a method for gradually learning more about the parts I'm working on.

## What's Next?

For me, joining LKMP was just the starting point of learning the Linux kernel and entering the open source community. Through this mentorship program, I learned that although the Linux kernel is huge and complex, and it's natural to worry about whether you can fit into the community, it actually welcomes everyone who wants to learn and contribute.

Moving forward, I plan to continue learning. I want to improve my C programming skills, read more related books, and watch related webinars. LKMP gave me the confidence that I can actually understand this stuff, even though I lack knowledge of operating systems.

Most importantly, I learned that you don't need to be a expert to start contributing. You just need curiosity, patience, and willingness to ask questions when you're stuck.

## References
- [Linux Kernel Mentorship Program Website](https://wiki.linuxfoundation.org/lkmp)
- [Linux kernel Bug Fixing Mentorship Program Learning Resources](https://drive.google.com/file/d/1Nyfdy2OqSjKr0DnlhFtMx4NR6uTs4swq/view)
- [Fixing bugs in the Linux kernel with Syzbot, Qemu and GDB](https://hackerbikepacker.com/syzbot)

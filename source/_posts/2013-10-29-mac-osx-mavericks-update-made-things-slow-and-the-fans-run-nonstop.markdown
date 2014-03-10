---
layout: post
title: "Mac OSX Mavericks update made things slow and the fans run nonstop"
date: 2013-10-29 12:40
comments: true
categories: 
---

I just updated from Mac OSX 10.8 (ML) to 10.9 Mavericks and my CPU fans started to run non-stop.
I did a bit of research and came across a post on apple's forum (https://discussions.apple.com/message/23509155#23509155) which stated that people need to reset their SMC (fan control).

This fix is for the following (Early 2009) and later, all models of MacBook Air, and MacBook (Late 2009).

- Shut down the computer.
- Plug in the MagSafe power adapter to a power source, connecting it to the Mac if its not already connected.
- On the built-in keyboard, press the (left side) Shift-Control-Option keys and the power button at the same time.
- Release all the keys and the power button at the same time.
- Press the power button to turn on the computer.  

Note: The LED on the MagSafe power adapter may change states or temporarily turn off when you reset the SMC.

This fixed it for me, hope this finds it useful for others.

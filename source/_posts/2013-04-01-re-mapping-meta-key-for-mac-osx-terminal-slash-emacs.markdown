---
layout: post
title: "Re-mapping Meta key for Mac OSX (terminal / emacs)"
date: 2013-04-01 11:21
comments: true
categories:
---

[Disclaimer: This is not an April Fools day joke]

###Using Mac's meta as option is NOT an option!

After getting accustomed to the Mac, I fell in love with it but one thing have constantly been nagging me. It is the unbelivably horrific placement of the "meta/option" key.
What this means is that, to go forward/back word, you have to reach your thumb all the way halfway across your hand to where your pinky is.
Do that enough, I am pretty sure you'll have early retirement of your hands.

Anyhow I decided to finally do something about this once and for all. I can't tell you how many sleepless nights I have thinking about how to combat this option. I have even ventured into re-mapping my emacs by changing all the commands using meta with control-something. For instance, page up would be re-mapped to C-u. But this is unreasonable as years of my muscle memory still have a hard time getting adjusted and I didn't want to make up my own mapping settings for the long haul anyway.

The first time I used the Mac, I did a google marathon of how to accomplish this but everything had it's negative drawbacks. At the time, I didn't know enough of all the Mac's keyboard shortcuts so I hesitated swapping my meta with Command completely.

###The fix!
Just follow these and you should be good!

```
mkdir ~/tmp && cd /tmp
git clone https://github.com/jaequery/cmd-key-happy .
make
sudo make install
make install-rcfile
make install-plist
```

What this does is it sets up and installs this to your launchctl so that it runs on boot.
Now all your meta bindings should be using "cmd" key, except Mac's global ones, such as "cmd-space", "cmd-tab", etc ...

You can customize them to which you want excluded globall and what not by:

1. editing this file: ~/.cmd-key-happy.lua
2. and issuing ```make install-plist``` to reload

Now that is all there is to it, I hope this especially helps out greatly for those switching from PCs to Macs.

Note) When on terminal, you'll notice that paste does not work. That is because I excluded M-v into terminal section, so I can use it for page up. But paste can still be triggerd using option-v and it shouldn't cause much issue as "on terminal" you don't necessarily need to paste all that much.

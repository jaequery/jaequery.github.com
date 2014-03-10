---
layout: post
title: "My MacOSX keybindings"
date: 2013-05-29 10:48
comments: true
categories: mac, emacs
---

###My keybindings to make things easier:

1. cmd-shift-m
Maximize/Zoom window: it was done by going to Sys Pref->Keyboard->Application Shortcuts, hit the plus sign and add title as Zoom and bind to cmd-shift-m

1. cmd-shift-_
Maximize/Zoom window w/ Moom: launch Moom and then hit space to maximize

1. cmd-shift-+
Fantastical: adds new task

1. ctrl-`
Show and hides iTerm2. Set from setting it on iTerm's general preference menu)

1. cmd-opt-space
Launches finder

1. cmd-shift-p and cmd-shift-n
Switch buffers in emacs with a shortcut key to go to previous or next buffer

###Cmd-key-happy
I installed cmd-key-happy to make my cmd to act as meta while I'm in terminal/iterm2. You can get it from here: <https://github.com/aim-stuff/cmd-key-happy/blob/master/INSTALL>

Here is my .cmd-key-happy.lua file:

```
global_excludes = Set{ "shift-cmd-tab", "cmd-tab", "cmd-space", "shift-cmd-space", "shift-cmd-=", "shift-cmd-m"}
apps = {
   Terminal = { exclude = Set{ "shift-cmd-[",
                               "shift-cmd-]",
                               "shift-cmd--",
                               "cmd-c",
                               "cmd-w",
                               "cmd-1",
                               "cmd-2",
                               "cmd-3",
                               "cmd-t",
                               "cmd-n",
                               "cmd-`",
                         } },
   iTerm = { exclude = Set{ "shift-cmd-[",
                               "shift-cmd-]",
                               "shift-cmd--",
                               "cmd-c",
                               "cmd-w",
                               "cmd-1",
                               "cmd-2",
                               "cmd-3",
                               "cmd-t",
                               "cmd-n",
                               "cmd-`",
                         } },
}
```

With this I can now easily hit my meta key (e.g; cmd+f or cmd+b to go between words) instead of hitting that awkwardly placed option key

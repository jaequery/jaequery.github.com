---
layout: post
title: "Emacs power ups"
date: 2013-05-26 21:43
comments: true
categories:
---

###Navigation
1. Emacs out of the box have text navigation down quite well. But there is still one thing I missed from VIM was C-d and C-u to do a half page scroll down / up.
To add something similar, add this to your ~/.emacs file:

```
;; Faster point movement
(global-set-key "\M-\C-p"
  '(lambda () (interactive) (previous-line 5)))

(global-set-key "\M-\C-n"
  '(lambda () (interactive) (next-line 5)))
```

###Coding
1. Also to comment a block of code, just select it by marking (C-space) and to the end of the target, then press:

```
M-;
```

To un-comment just re-run it from the same selection of code that's been commented out.

###Editing
1. For the longest time to search/replace, I invoked it with M-x replace-string. It is a being long winded and I never managed to use:

```
M-%
```

Only caveat is this puts you in interactive replace, but type ! immediately afterward to replace all without the nagging prompts.

1. Code auto-formatting to make it look pretty is extremely easy with your defined tab-spacing, etc is easy. Just do:

```
C-x h
C-M \
```

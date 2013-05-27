---
layout: post
title: "Emacs power ups"
date: 2013-05-26 21:43
comments: true
categories:
---

Some thing I missed from VIM was C-d and C-u to do a half page scroll down / up.
I've found to do something similar, you can just add this to your .emacs

```
;; Faster point movement
(global-set-key "\M-\C-p"
  '(lambda () (interactive) (previous-line 5)))

(global-set-key "\M-\C-n"
  '(lambda () (interactive) (next-line 5)))
```

Also to comment a block of code, just select it by marking (C-space) and to the end of the target, then press:

```
M-;
```

To un-comment just re-run it from the same selection of code that's been commented out.

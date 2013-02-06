---
layout: post
title: "Ultimate emacs elisp for web development"
date: 2013-02-04 11:53
comments: true
categories: ide, emacs
---

Emacs out of the box doesn’t have a great php/html/js editor. So here are what you need to get it good.

- First, let’s create the elisp folder that stores all your elisps:

`mkdir ~/elisp && cd ~/elsip`

- Now download “php-mode”

`wget http://php-mode.svn.sourceforge.net/svnroot/php-mode/tags/php-mode-1.5.0/php-mode.el`

- Now download “multi-web-mode” for html/js/css

`wget https://raw.github.com/fgallina/multi-web-mode/master/multi-web-mode.el`

- Now add/update this line to your ~/.emacs file

```
(add-to-list ‘load-path “~/elisp”)
(require ‘php-mode)
(require ‘multi-web-mode)
(setq mweb-default-major-mode ‘html-mode)
(setq mweb-tags ‘((php-mode “<\?php\|<\? \|<\?=” “\?>”)
(js-mode “”)
(css-mode “”)))
(setq mweb-filename-extensions ‘(“php” “htm” “html” “ctp” “phtml” “php4” “php5”))
(multi-web-global-mode 1)
```

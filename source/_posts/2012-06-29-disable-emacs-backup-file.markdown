---
comments: true
date: 2012-06-29 23:25:00
layout: post
slug: disable-emacs-backup-file
title: disable Emacs backup file
wordpress_id: 36
categories:
- Technology
---

Edit/create a ~/.emacs file in your home directory.





(1). prevent the creation of backup files:



    
    <code>(setq make-backup-files nil) </code>




or




(2). Have it save the backup files in some other directory, where they won't bother you unless you go looking for them. I have the following in my .emacs:



    
    <code>(setq backup-directory-alist '(("." . "~/.emacs.d/backup")) backup-by-copying t ; Don't delink hardlinks version-control t ; Use version numbers on backups delete-old-versions t ; Automatically delete excess backups kept-new-versions 20 ; how many of the newest versions to keep kept-old-versions 5 ; and how many of the old )</code>

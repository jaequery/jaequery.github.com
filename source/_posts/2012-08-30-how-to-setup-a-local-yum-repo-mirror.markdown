---
comments: true
date: 2012-08-30 03:24:00
layout: post
slug: how-to-setup-a-local-yum-repo-mirror
title: how to setup a local yum repo/mirror
wordpress_id: 26
categories:
- Technology
---

I've spent some countless hours fiddling around rsync'ing many public mirrors praying it supports directory crawling.




Well those days are no more, it seems there was a utility that handles mirroring your current yum packages repos identically to be distributed to your other servers.




It's called "reposync" and rightly named. You might need to yum install yum-utils.




Now, just do:




reposync -p -v /var/www/html/yumrepos




This might take a while, especially the main OS base packages. 




Once done, you need to create metadata so it can be accessed via yum, to do so, you need to run createrepo:




createrepo -s sha /var/www/html/yumrepos/reponame_goes_here




Do this for each of the repositories you have.




Now, point your other servers to use your new proxy server for yum updates.




One thing to note is that some repositories require GPG keys, such as EPEL, so make sure you copy over your /etc/pki/rpm-gpg/* files on your repo server to your other servers.




This site has a bit more detailed instructions:




[[http://icseplus.blogspot.com/2012/08/create-you-own-repo-server.html?zx=28f949eb9f42c164](http://icseplus.blogspot.com/2012/08/create-you-own-repo-server.html?zx=28f949eb9f42c164)](http://icseplus.blogspot.com/2012/08/create-you-own-repo-server.html?zx=28f949eb9f42c164)

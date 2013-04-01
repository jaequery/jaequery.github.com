---
layout: post
title: "Running Pow and MAMP simultaneously"
date: 2013-03-12 15:28
comments: true
categories: 
---

In the pursuit of achieving the perfect web development environment on Mac, I'd need two things.

1. LAMP environment 
2. Ruby/Rails environment

For LAMP, I've settled on MAMP Pro. Although it costs a bit of money, this is by far the best way to manage your sites locally. For one, it's got a great GUI to manage your vhosts. Editing by hand can get tedious and this takes care of it. It even adds /etc/hosts entries for you to handle local name resolutions.

For Ruby, Pow has been an unbelievably efficient way of running and managing multiple ruby apps for me. All you have to do is just drop a folder in your ~/.pow and you are set as it also handles local name resolutions for you on the fly.

But getting both of them to work at the same time posed a problem but a quick SO search revealed a very cool trick:

[Setting up Pow and MAMP to work simultaneiously](http://stackoverflow.com/questions/7010104/running-pow-mamp-pro-simultaneously)
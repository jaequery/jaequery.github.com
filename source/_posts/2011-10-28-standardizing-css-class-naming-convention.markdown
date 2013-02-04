---
comments: true
date: 2011-10-28 18:49:00
layout: post
slug: standardizing-css-class-naming-convention
title: Standardizing css class naming convention
wordpress_id: 58
categories:
- Technology
---

### **A thorn in my daily coding**




I used to be a fan of using dashes in class names but I think that is kind of silly as far as how standardizations go.




I'm thinking we just stick with underscores.




This feels dirty to me:




$('#top .drop-menu') …




but this doesn't:




$('#top .drop_menu') …




### **Now when backend is also involved …**




It gets a lot more awkward when you start to have things like:




$('#something input **.first_name** .flashy-background-something')




The developers use underscores for their fields relevant to their database, hence the case with .first_name




Also on the server side, they also use underscores for their naming such as $first_name = $this->params('first_name') …




### **Now when IDE is involved …**




Having hyphens can somewhat hinder you when coding. If there is a hyphen in a word, most IDE will just highlight the portion of that. But with underscores, it'll highlight the whole word and you can copy/paste/whatever right away.




### **It's all in the eyes of the beholder**




It's all a matter of preference but when you are working with several developers, naming conventions to me goes a long way to a cleaner code.

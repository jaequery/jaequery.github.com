---
comments: true
date: 2011-12-15 18:03:00
layout: post
slug: bitcss-project-follow-up
title: bitcss project follow-up
wordpress_id: 48
categories:
- Technology
---

### First of all




I wanted to thank you all for showing your interest on this project. Especially to all the twitterers and watchers at github. It is serving me as a motivation to bring this project to life. =D




### And I been giving it some thoughts




So I been thinking a lot on how to make this really work. I'm writing this post really to clear my head a little bit.




The problem, making it work is easy. Making it work in an intuitive fashion much like jQuery, is hard. 




### Things I thought of




I have thought about a few ways of going about it but all of them have their pros and cons. I'd like to hear what you think about them.




### Option #1 - Free-style structure, just a collection of folders.




This is the simplest method. It'll be a soup of all css snippets / examples / themes out there in this one repository. I also find real value in this despite it's simplicity.




So I went ahead and started the project in this manner and created the following folders, and we can just keep adding them as the need rises:




  * /frameworks - a collection of css frameworks out there


  * /themes - a collection of css templates


  * /styleguides - a collection of css style guides



**Pros: **Simple to get going as there is almost no back-end/front-end coding required. It'll completely be ran via git and will be a repository with many different collections of css codes / examples / themes that are randomly contributed by members. 




**Cons: **There will be no way to search and cherry pick to mix/match what you want from the template. What you'll do is, just browse through many different folders, if you find something you like, you inspect the element, grab the style, and copy / paste to your site. I'm guessing this is the method most of us are already familiar with.




### Option #2 - Structured CSS naming convention




This is going to be a bit tougher, as there needs to be a strict guideline to how you style, much like the way [jquery-ui](http://jqueryui.com/docs/Theming) does it. For every elements out there, such as: modal, header, menu, etc … there will be a standard structured html to style off of.




So a simple example would be a menu:




<ul> <li> …. </li> </ul>




To apply bitcss, you'd do:




<ul class="bitcss-menu** theme1**">




<li> …. </li>




</ul>




And to use a different theme, you'd just do:




<ul class="bitcss-menu** theme2**">




<li> …. </li>




</ul>




This all sounds good in theory but this was a super simple example. For things a bit more complex, I have a hard time imagining just how practical it would be. My thoughts on this is that, it requires a strong disciplined community and will rely heavily on utilizing best practices (and I don't think anyone really knows what the best practice is). This also means that there will be some form of a design committee that will review and judge, which is something I'd like to stay away from.




**Pros: **Once there is some sort of solid guidelines down, I can see it being pretty useful. Anyone can contribute their variations of elements easily just by following the rules and will know exactly how to use/apply to their site.




**Cons: **It may require a use of SaaS (like google webfonts) to pick and choose exactly the type of style you want to use on your site. I think it can get a bit hairy as there are ton of variations for CSS, compared to fonts:




[http://bitcss.com/api/?themes:theme1](http://bitcss.com/api/?themes:theme1)[h5,button,menu],theme5[h1,h2,h3,h4,modal]




### Option #3: A database-driven stylesheet guide generator




This option means no github and it'll be on a web platform that lets you visually generate a stylesheet guide from the website.




  1. User comes to the site


  2. Clicks on "Create a stylesheet guide"


  3. User sees a stylesheet that lists all types of elements from h1 to h5, buttons to modals, etc … etc … much like [Twitter Bootstrap](http://twitter.github.com/bootstrap/) page


  4. Only difference is that, with this, you can edit the CSS properties directly by clicking on it


  5. So if a user wanted a different color scheme for the button.large, user just clicks on that button, change the color css attribute, and hit save


  6. Think of it like Firebug on a stylesheet guide from the website that saves a css file



**Pros: **No need for manifest.json and setting up git. Those two were what I would of thought can hinder it due to certain level of complexity. It also solves many of the issues of the other options.




**Cons:** The biggest drawback for me is that I'll need an entire site to develop. But I think it'll make for a cool weekend project.




### So …. my thoughts are ….




For me, I think #3 is a pretty compelling option and I get the feeling that it'll be the most simple to use and provides value right off the gate.




#1 is also something I always wanted, and it seems like it may serve a different purpose so those two can work together. I kind of wanted a folder that had a collection of many different landing page themes, that I can use whenever the need rises, etc …




#2, I get a little iffy thinking about the structures/guidelines, from my experience, it is almost impossible to follow a guideline.




So my thoughts are that, I think **#3** is the route to take. But also continue with **#1** to create and support an ever evolving css dump collection.




### Let me hear what you guys think




Well those were my thoughts, but, I'd love to hear what you guys think, feel free to leave me a comment or two.

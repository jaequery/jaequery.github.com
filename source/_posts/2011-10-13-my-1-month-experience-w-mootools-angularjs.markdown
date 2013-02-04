---
comments: true
date: 2011-10-13 18:41:00
layout: post
slug: my-1-month-experience-w-mootools-angularjs
title: My 1 month experience w/ mootools & angularjs
wordpress_id: 61
categories:
- Technology
---




### New job, new everything




So with my new job, they had an environment like I've never seen before.  
Mainly, a strict policy of, "No jQuery!" 




My initial reaction was, O_o




But something inside me wanted to venture out and try some new stuff.




### Mootools




So I've dived myself into mootools. It only took me like 1 hour to realize that it's not really a framework at all. It's almost like a set of helper methods, something I already have with my core js lib. There are some key noticeable difference in the way you select elements (where jQuery is king).   
  
In jQuery, $(….your css selectors…) can be used … even abused.




But in mootools, there is a distinction of retrieving a single element and multiple element.




For example:




In jquery, I can do this $('#tab').hide(); ,  which will go out and hide #tab  
In mootools, I can do that also with $('tab').hide();  
  
In jquery, I can also do $('.tab').hide();  which will remove all elements with a tab class.  
  
But in mootools … a big but …




I have to do $$('.tab').hide():




It may seem as it's something you can just learn to live with but man this sucks a lot. It is annoying to think this way and it hinders rapid development.




There are things that's seriously lacking in mootools. Such as append(), prepend().  
So for me to append something to body, I'd have to get the dom and replace the whole dom with some stuff added to it.




Event delegation in mootools is also quite different too, but I got used to it, so no biggie.  
  
But aside from that, mootools is alright. It's just not as powerful in terms of DOM. Mootool's helper classes are okay too, I tend to have a better collection of helpers anyway so never needed to use theirs.




###   
Angularjs & Backbonejs




It seems backbone/knockout are all the rage these days. I never bought into the hype until I was forced to work with it at my current job. And I tell you, boy, this was a beast to work with. This put a paradigm shift in terms of what I already know about web development. It took me back to the days of when I was learning Visual Basic. It is how it feels and runs. Something I always wanted the web to be but over time, I've grown accustomed to the stateless environment.  
  
So having said that, what Angularjs does is, it binds data object directly to your DOM. It takes a bit to understand it, but once you do, it's actually pretty cool.




Think of your website as a giant javascript object, where you just change the property of it, and it updates it on your website instantly.  
  
So traditionally, one would do: 




<div id='#populateme'></div>  
  
<script>  
$('#populateme').html('i am populating you');  
</script> 




But in angular:  
  
<div ng:bind="populateme"></div>   
  
<script>  
this.populateme = 'i am populating you';  
</script>   
  
You can even do methods:   
  
<div ng:bind="populateme()"></div>   
  
<script>  
this.populateme = function(){  
    return 'i am populating you from a method';  
}  
</script>  




It takes some time to get used to but I think this does somewhat help you organize your code better. I never got to a point where my code was un-readable for me to need this. Imo, it is a cool concept but it does force you / limit you to code in a specific pattern. If you are using jquery events, you'll have to use event delegation on almost everything since the DOM is generated after the site has loaded.




###   
Conclusion




There are lot of things I like and don't like but my conclusion is that: 




1) mootools is alright, there's just nothing there to get me excited about  
2) knockout/angular is cool but not really my cup of tea (yet). also it'd be problematic with SEO, so it's mainly for admin purposes.

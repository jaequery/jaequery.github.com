---
comments: true
date: 2011-10-25 05:23:00
layout: post
slug: zend-framework-2-i-am-disappointed-again
title: Zend Framework 2, I am disappointed  ... again
wordpress_id: 59
categories:
- Technology
---

As I'm just going through the changes in Zend Framework 2, I can only shake my head in utter dis-belief and agony.




While other languages such as ruby/python/node are excelling in simplicity, Zend Framework tends to go in the direction more like .NET/Java.




I know that when a person is given enough free time, they are going to "over-engineer" things simply because "you can", kind of like breaking a stone and breaking a stone again, in a repeated cycle.




It was not so long ago where I was once caught in this web of Design Patterns thinking they are the holy grail of coding. I had a year of free time to just create/re-create frameworks using multiple patterns all while trying to solve a problem that doesn't exist. It was fun and I was proud of my uber framework.




Anyhow, then I got into other languages like ruby/node and more importantly, python. It is at this period where I valued the beauty of "simplicity". Less lines of code == win. Less files == win. Less == win.




With my uber framework, it felt like a juggling act. Everytime I wanted to do something, I had to create hordes of files along with it. Sure, it kept the file clean and short but when you start to have millions of files opened, it starts to get a little exhausting mentally.




In my opinion, PHP was successful because it was "simple". Creating a web app, it really just boils down to a 3 part process. Get the request, process the request, output the request. Only thing I'd like from a framework are:




- Data layer  
- Auth / ACL  
- Controllers  
- A nice little library of helper methods




Having said this, I don't like the direction of where current PHP ORM's are going. They are meant to let you perform data commands without SQL at the expense of performance and somewhat initial learning curve. There is no win here. If you want high performance, ORM is not it. You go through SQL/Stored Procedures. Just a simple query builder should be enough for ORM, just query and get the data.




There is not much else to it. Most apps can be created fairly quickly, securely, and robustly. Without all the baggage that comes from frameworks/cms. I was only able to grasp this concept after several years, and can now reason with Rasmus Lerdorf said a few years back. Coding should be simple. Most coding can be done very simply and that OOP for PHP is quite flawed. It's like trying to get an elephant to ride a bike. 




Just look at javascript, now that is an OOP language. Not only that, it is event-driven and lets you do far more complex things that PHP can't do. 




I wish Zend developers would try to consider beautifying the language. I said this even before Zend Framework had a public 1.0 release that there are several flawed logics in it and will be a complete spagetti soup. The moment VR came out, it seems no one but me understood it is breaking the sheer logic of what the View *should* do. The separation of layout and view also was weird to me, as they should be one and the same. It is only now developers seem to be realizing this. 




So enough is enough. Enough…




It is time PHP world understands what beautifying the code can do to providing a robust/secure/fast code.




### And so




I'm starting a new kind of framework. It's called Jien Framework. Jien named after my daughter, Jiena.   
  
You can find it here:  
[http://github.com/jaequery/jien](http://github.com/jaequery/jien)




Installation guide here:  
[http://jien.jaequery.com/docs/introduction ](http://jien.jaequery.com/docs/introduction%C2%A0)

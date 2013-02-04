---
layout: post
title: "Ruby is strange and odd"
date: 2013-02-03 19:08
comments: true
categories: 
---

### Day 2 of Ruby

It's strange and I am confused by all these weird syntaxes.

Coming from PHP, I assumed at first glance:

       @name (ruby) is $name (php)

But no, because in ruby, you have several different ways of assigning a variable.

There are:

- @name (instance var)
- @@name (class var)
- name (method var)

Not to mention, "symbols" which really threw me off guard.

Anyhow, here is what I found out.

1. @name (instance var)
Instance vars are similar to $this->name in php.
So @name = $this->name.

2. @@name (class var)
Now this one is a bit tricky. Class vars probably won't ring a bell to PHP developer as in PHP, class vars are like instance vars. However in Ruby, @@name is similar to static vars.
The reason why it's that is because if you have 3-4+ instances of a class, @@name is shared by all of them. Somewhat of a singleton variable.

3. name (method var)
This is pretty straight forward. It's a var that only lives inside a method. Good for throwaway/temporary variables, such as res, total, etc ...

4. :name (symbols)
Before learning ruby, I thought this was ruby's way of PHP's $ sign. Every ruby code I see online had some :symbols and I thought ruby would be a walk in the park as long as I think to myself that is PHP's equivalent of assigning variables. But no, it's probably what threw me off the most.

You see, :symbols aren't something you can assign to. It's not a variable, it's a reference. Or, atleast that's what other ruby devs told me on freenode. I still didn't undersetand, so is this like a pointer reference I asked? And they said no. After about an hour of chatting back and forth, I came to conclusion from bits and pieces of evidence that :symbols are only used inside hashes as keys. 

So in php land:

    $users = array(
        "name" => "john",
        "name" => "mark",
    )

    foreach($users AS $user){
        echo $user['name'];
    }

But in ruby land, it's:

    users = {
        :name => "john",
        :name => "mark",
    }
    
    users.each do |user|
        puts user.name
    end


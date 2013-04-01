---
layout: post
title: "A month after switching to Macs"
date: 2013-02-09 00:10
comments: true
categories: macs
---

### The story

For most of my life, I had a deep resentment toward Macs. I always never liked their concept of trying to do something different. Back in the days, my feelings all started with their philosophy of one-button mouse. I appreciate they want to keep it simple but as a computer, it just didn't make sense to me. I grew up with things that had a lot of buttons, my favorite video games all had atleast 6 buttons to press. Heck, if they had 3 buttons when PCs had 2, I'd have given them a second look. But no, Macs were consistently pushing one-button, even to this date.

Anyhow, I've grown accustomed to PCs very much. I know almost all the keyboard shortcuts Windows has to offer, allowing me to do virtually anything instantly and seamlessly at ease. Simply put, I was quite happy and comfortable with it so switching to anything else would throw me off guard and would not be my ideal situation.

### Tried Macs (several times)

But because I also enjoy trying out new and shiny things, time and time I'd buy a Mac, try it out, and find myself totally weirded out by it. Sometimes, I tried so hard to like it, but I just was not quite as productive on a Mac than on a PC. If it wasn't a gift from my wife, I would've returned it for a full refund. Anyway, it was just collecting dust. I just had too much work to do and I absolutely require productivity.

### My PC broke hardcore

Then one day, my awesome PC just died. It was a Lenovo Thinkpad and it was just the perfect fit for me, small, compact, and dock-station ready. I'd take it wherever I go, work, home, friends, it was one thing I'd never leave my house without. Had some great memories with it and some bad. I was just overly distraught, like losing a kitten or something.

### Powering on the dusty old Mac
Since I had no other choice, I powered up my Macbook Air for me to continue working. The utter feeling of being slow and un-productive was catching up to me really fast. At this point, I already knew a most of the common keyboard shortcut commands, such as spotlight, alt-tab, cmd+shift+[ and ], and so on. But it just wasn't the same. It sucked.

As I was on a strict deadline at work, I decided I'll just have to use Mac for now and deal with PC later. I knew I had to get up to speed fast as I absolutely must be *productive*. Now at this time, I decided to try to understand what made me less productive on a Mac compared to PC.

So here are what I just didn't like about Macs:

1. No easy way to maximize window and full screen mode weirded me out. On Windows, I'd just double click on the window title. But on Macs, I had to carefully hit the green plus button.
2. Sometimes, my window would get minimized and when I cmd+tab back into it, I don't see anything. I read article that I had to also hold options and release before I get to it, which was probably the dumbest thing I have ever heard.
3. There was no Start+e equivalent to open explorer/finder. On Windows, I'd just start+e and just start typing to get to any folders/files on my PC. On Mac, closest I've come across was to just locate finder from cmd+tab, or launch finder via an app called Alfred.
4. No Zend Studio 5.5. This was almost a deal breaker right on the spot.
5. Mac keyboards aren't too friendly for emacs user. Hitting that option button for meta is quite an excercise in itself.

Since I just could not live without these, I looked hard online to see if there was anything remotely even close to how it was on PCs. And I can now safely say, I did, and boy am I glad I took that extra time to do so, as it has paid off in dividends.

1. To perform maximize window, I had to go to System Preferences -> Keyboard -> Keyboard Shortcuts -> Add, and put in "Zoom", and shortcut as "cmd+shift+m". Now this will trigger the green maximize button an any active window I'm on which is incredibly useful for me as I hate any apps/windows that floats around in a "limbo" state.

2. Now I knew there was no other way, I looked hard and there just was no supported option for having cmd+tab to work the way it did on PCs. Then fortunately I stumbled across a forum which discussed exactly same problem I was having and one person mentioned that I should install an app called: [Witch](http://manytricks.com/witch/). It wasn't free, I had just installed their trial and I was reasonably satisfied with it, as now when I switch back to any app, it'd even restore it from minimized state. Only issue I have is that it's not as responsive as native cmd+tab, there is a slight delay.

3. I searched hard and found another gold mine, cmd+option+space. It opened finder just as I used to open Explorer. One caveat, sometimes it would open it without any side panels (main folders on the left), but quickly found out that you can hit cmd+option+t to toggle the sidepanel.

4. Now this was tough, I been using ZS 5.5 for roughly close to 8+ years. It was my bread and butter when it comes to development. I had a lot of shortcut/macros to do whatever I needed and all of that was now taken away from me. But since I had no choice, I went on an IDE download spree, testing just about all the IDE's out there available for mac, including: Coda, Textmate, Sublime, Eclipse, etc ... And after a good couple hair pulling days, I managed to find something I liked, and that happened to be Aptana Studios. In fact, I found this to surpass even Zend Studio in many ways. The auto code formatting via cmd+shift+f to be awesome. And on top of it all, it was the only IDE that provided the closest to emacs as one can possibly get. My only gripe is, ctrl+s works for search but ctrl+r (reverse search) doesn't. Quite baffling to me and I hope I can find out how to get around to doing it.

5. In the beginning, I was mostly upset about how it is now too difficult for me to hit the meta key. It's almost as if I have to stretch my left thumb all the way out to where my pinky is. If you are an emacs user, you probably understand just how important it is to hit that meta key repeatedly :) But miraculously, I learned to get accustomed to it. I guess human mind really allow you to get accustomed to anything if no other given choices exists.

### I love Macs now

After taking some several weeks of changing my habits and learning some new tricks, I am now quite fond of Macs. I never really thought I will be saying this but Macs are indeed superior to PCs in just about every way. For those that wants to know why:

1. Mac's apps are just so much better and nicer. For one, Textual was a huge improvement over mIRC, mainly in the aesthetics department. Querious (db gui) is simple and elegant and suits my needs just fine. And even Mac's native apps, such as: iCal, iPhotos, and Mail just trumps anything PCs have to offer. It's almost no contest who wins here.

2. Bash being integrated to the OS is a life changer. As I'm big on linux, this itself was a huge improvement over PCs. I can now finally sleep happy and not worry about the days of putty'ing.

3. TimeMachine is too good. Backups couldn't get any simpler, point-in-time restore of any files back in time is just lovely.

4. I now fully appreciate the entire Mac keyboard shortcut eco-system. Easy to customize and not buggy like on Windows.

5. Not having to rely on Virtualbox/Vmware to launch local servers. I find brew surprisingly refreshing to use and setting up a LAMP, or RoR, or even django is extremely easy to setup on Mac.

### One big caveat about Macbook Air

If you are like me, you enjoy taking your laptop everywhere you go. And when you get to an office, you'd like to hook it up to dual-screen monitors. Surely I thought this would be a walk in the park, as with any other PC's. But no, it turned out to be quite an ordeal. Basically the problem is, in order to extend your monitor, you need to hook them from your mini displayport to the monitor. But Macbook airs only have a single mini-displayport and from my research, there aren't any mini-dp hubs as you'd have with usbs (i know some exists but they sell for $300+).

It turns out, there is an alternative, which is what they call a DisplayLink USB to DVI adapter. 

You need to buy a few things:

- Mini-dp to DVI (or vga)
- USB to DVI (or vga)

I bought them from Amazon: 

- [J-Tech Digital High Quality Mini DisplayPort to DVI Adapter female Cable](http://www.amazon.com/gp/product/B00425MQGA/) for $12.99 
- [Plugable UGA-2K-A USB 2.0 to VGA/DVI/HDMI Adapter](http://www.amazon.com/gp/product/B0038P1TP4/) for $59.95

I was quite shocked at the price of that USB adapter but then again, it's worth buying for that extra monitor. I'd have to warn though that there is a slight lag on the monitor this hooks up with as USB is not as fast as mini-displayport. But for just normal activity including browsing/email/coding, I haven't been too bothered by it.

### App recommendations

Here are few that I have and can't live without:

- [fantastical, a calendar app, gives you a nice quick hotkey to add tasks/events](http://flexibits.com/fantastical)
- [Tunnelblick, OpenVPN client](http://code.google.com/p/tunnelblick)
- [getcloudapp, uploads copy buffers to the web and returns you a shortened link, useful for screen captures](http://getcloudapp.com/)
- [omnigraffle, sweet flowchart/diagram creator](http://www.omnigroup.com/products/omnigraffle/)
- [gitx, nice little git gui client which can even be invoked from command line on working directory](http://gitx.frim.nl/)
- [textual, a near perfect irc client](http://www.codeux.com/textual/)
- [querious, nice little sql gui client](http://www.araelium.com/querious/)
- [aptana studio, imo the best IDE in the market](http://www.aptana.com/)
- [aperture, great photo viewer](http://www.apple.com/aperture/)

If you know of any other apps that I should try, feel free to let me know at @jaequery. I'm all ears.

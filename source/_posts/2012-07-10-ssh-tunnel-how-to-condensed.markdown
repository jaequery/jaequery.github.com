---
comments: true
date: 2012-07-10 04:56:17
layout: post
slug: ssh-tunnel-how-to-condensed
title: SSH Tunnel How To (condensed)
wordpress_id: 34
categories:
- Technology
---

I have a Private Cloud under firewall and I needed to run Nessus on our internal network.




Problem is, I'd have no way to access the web-gui unless I explicitly expose the port on the firewall, something I'd not want to do.




It appeared SSH Tunneling is what I needed. It sounded simple enough, but in practice, I just couldn't get my head around it.




Why? Mainly because I was on Windows w/ Linux on Virtualbox. So the whole concept of me opening a tunnel didn't make sense to me as Windows box won't have access to the tunnel.




I read there are some ways you can do it through Putty but that in itself was quite an exercise. Randomly, I was on a mac, googling for SSH tunnel and all of a sudden it all made sense. 




From terminal:




ssh -N -L 2080:internalserver1:80 root@publicserver




It'll appear as if nothing happened, as you'll get no response output.




But now, point your browser to http://localhost:2080




And you'll see that it's loading the website from internalserver. Voila.




I hope this made far clearer sense than other pages that teaches you about SSH tunneling.

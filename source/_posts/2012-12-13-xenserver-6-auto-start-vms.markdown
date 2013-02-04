---
comments: true
date: 2012-12-13 19:34:00
layout: post
slug: xenserver-6-auto-start-vms
title: xenserver 6 auto start VM's
wordpress_id: 5
categories:
- Technology
---

Citrix decided to disable auto-start VM's for their free edition startin v6, as I found this out the hard way.




i guess it's their strategy of getting you to buy their paid license, which gives you the auto-start from the GUI.




but for the rest of us, here is a quick simple way to do this, you need to manually start the VM's upon bootup of the host.




here's how:




from the host, edit /etc/rc.local, and at the end of the line, add these two:




sleep 20  
/opt/xensource/bin/xe vm-start uuid=fbd0fdec-9f69-e47f-072a-02ff854fd890




where uuid is that of your VM. you can find the uuid from xencenter on VM's general tab.




do this for each VMs you want auto started

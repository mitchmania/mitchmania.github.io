---
layout: post
title: "XenTk - A Crossplatform GUI for Citrix Xenserver"
date: 2017-10-27 21:35:00
author: Mitchell Artin
tags: xencenter xenserver tkinter python programming
category: blog
excerpt: I use Citrix Xenserver Hypervisor for all of my virtualization needs and my only complaint with it is that its client, Xencenter, is only written for Windows.  Not wanting to always dive into the command line for Xenserver administration I wanted a simple GUI that would run on my Mac OS and Linux desktops.
---
I use Citrix Xenserver Hypervisor for all of my virtualization needs and my only complaint with it is that its client, Xencenter, is only written for Windows.  Not wanting to always dive into the command line for Xenserver administration I wanted a simple GUI that would run on my Mac OS and Linux desktops.  I used the Python XenAPI with Tkinter to make XenTk.  Definitely a work-in-progress, I have only implemented the functionality that I need so far (creating VMs from templates, power cycling, getting IPs, etc.) but I definitely plan on building this out into a fully-functional tool for the open-source community.  If nothing less, it could be helpful as an example of the highly undocumented Python XenAPI.  One thing that I spent some time figuring out was the fact that when setting the RAM size in bytes of a VM, their API expects a string of the number of bytes.  Below is a screen shot of an early design.
![XenTk]({{ site.baseurl }}/assets/posts/xen_tk_1.png)
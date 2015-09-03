---
layout: post
title: "This Past Weekend's Project: Migration to Citrix Xenserver"
date: 2015-09-01 15:00:00
author: Mitchell Artin
tags: virtualization rack
category: blog
---
Every company I've worked for has used VMware vSphere for all of their virtualization needs. For the most part, I get it.  It provides them with the performance, stability, and most importantly the permissions granularity that they need.  vSphere is the optional management layer VMware offers to manage their type 1 hypervisor called ESXi.  I've used these systems to power my home network and due to ESXi's stability (and some crafty UPSes) my ESXi box's uptime has been 6 9's in the past three years!  But it wasn't always this great.

ESXi itself is actually quite plain, it hosts virtual machines.  VMware plans on the user rolling out vSphere to really add a full feature set.  So I deployed it!  At first I started with the Windows-based installer to run the software (why not Linux?!).  I realize most of my issues were probably my ignorance but after about one week it started crashing.  ESXi was stable and I still thought it was the best so I pursued other avenues, not wanting another Windows box to maintain.  VMware offers a ready-made vSphere appliance based on SUSE but deploying it cost me 70 GB on my ESXi box!  I used that for about another month then it started crashing, again probably because lack of proper maintenance.

And then I discovered Xenserver, the open-source type 1 hypervisor from Citrix.  Just the Xencenter (Windows based client to control Xenserver boxes) installer was around 50 MB.  Thats significantly better than VMware's 350 MB for their equivalent.  Out of the box Xenserver supports templates unlike ESXi which needs to be tied to vSphere infrastructure to have this functionality.  Citrix's offering even supports mounting SMB shares for disk image access.  ESXi can only mount ISOs by uploading them to a datastore or connecting them locally through their depressingly buggy console.

But my favorite feature feature of all isn't even from Citrix.  Named Xen Orchestra, it is a web-based user interface packaged into an appliance.  It is extremely easy to roll out and connects to Xenserver boxes using SSH.  This product is from a French company Vates and has several pricy software levels but I've found the free version to be very functional.  My main needs for it are getting VM consoles and rolling out VMs from templates my Linux-based machines.  After several months of testing I've moved Xenserver into my production environment and I've not looked back yet.
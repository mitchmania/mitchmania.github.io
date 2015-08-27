---
layout: post
title: "How I learned to use UUID mount points the hard way"
date: 2015-08-28 15:00:00
author: Mitchell Artin
tags: linux cameras
category: blog
---
When I first read about fstab I was probably 12 years old.  I was using the device files in the /dev directory with fdisk with success for months so I figured this success would carry over to fstab.  I looked at the UUID's the OS was using to mount its basic partitions and in my blissful ignorance of childhood went "psshh who needs that".

Years later I was designing the security camera system for my house.  I said "psshh who needs UUIDs", added my partitions to fstab using device files, and left for the summer to do an internship.  About 2 months into the internship the power went out in my house and all of the computers reset.  I had done diaster recovery tests before on my entire network and the device files never changed!  But this time was different.  I came back to my house at the end of summer to find all of my backup disks wiped clean on one particular backup node.  When this bare metal machine reset, all of the devices files shuffled around and the various scripts and programs I use just erased everything.  Thankfully I have multiple nodes to avoid catastrophe but now I always use UUIDs in fstab...

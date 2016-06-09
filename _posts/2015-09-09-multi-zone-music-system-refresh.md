---
layout: post
title: "Multi-zone Music System Refresh"
date: 2015-09-09 15:00:00
author: Mitchell Artin
tags: virtualization music r-pi networking
category: blog
excerpt: I have always been a lover of music.  So it makes sense that I'd want music in every room of my house.  My house can be separated into three main rooms, bedroom, office, and living room.  I have a stereo in each room along with an Ethernet connection and a Raspberry Pi.

---

I have always been a lover of music.  So it makes sense that I'd want music in every room of my house.  My house can be separated into three main rooms: bedroom, office, and living room.  I have a stereo in each room along with an Ethernet connection and a Raspberry Pi.

This is a simple diagram of what I'm dealing with.
![Multi-zone Music System Diagram]({{ site.baseurl }}/assets/posts/multicast_music_system.png)
A Brief Overview:
The Musicserver
I chose to create a Windows box to handle this task to keep it simple.  There are many solid media players for Windows with web-based clients.  Windows also has RDP which makes remotely logging into the box easy for any users.  This box is running on a Xenserver host.  I've connected a Creative Labs X-Fi Go! Pro USB soundcard and passed the PCI bus associated with this USB host controller in to the VM.  This means that any USB device plugged into the physical USB port on the Xenserver host will be passed directly to the VM.  This USB sound card is not critical to my project but the drivers for it create an easy audio loopback device.  This virtual audio interface is aptly named "What U Hear" and loops all the output back in to the computer.  I then use VLC to stream the input from "What U Hear" over my network.  While I'd normally criticize this solution for being relatively "hacky" it makes it easy for me to stream Pandora in sync to all my clients.  This way, anything that is playing on this host (Youtube videos, Spotify, MP3 files) is automatically broadcast on the network!  I have future plans to recreate this audio loopback device using software that does not depend on having the USB sound card plugged in.
My first iteration of this project used MP3 streams over HTTP.  Clients would connect to the server, "subscribing" them to the stream.  When multiple clients are connected, I am creating duplicate and identical streams for each.  As you can imagine, this doesn't scale.  In the past few days I moved to streaming RTP on a multicast address.  Now my music stream is broadcast to every machine on the network, regardless of whether they want it or not.  This is just another reason for me to roll-out VLANs on my home network and throw the music system in its own VLAN.

The Clients:
I love Raspberry Pis and probably own way too many of them.  They are powerful enough to decode the 320kb/s music stream without skipping and they are very affordable.  However, the onboard audio is not high quality.  I chose to connect them to Asus Xonar U3 USB sound cards because they work out of the box with the Raspbian OS and provide decent quality audio.  When I was using HTTP-based streams, I used MPD and MPC on these clients.  MPD doesn't support RTP-based streams so I moved to VLC.  The Raspberry Pi's are also powered by Power-over-Ethernet (PoE) for simplicity.  From there the USB sound cards are connected to their respective stereos via analog RCA connections.

Current Work:
Right now I'm working on a few Ansible Playbooks to control the clients.  Ansible could easily handle the situation where a Pi crashes for example.  The playbook could reboot it and reconnected it to the stream.  I will also make a playbook for setting up a new Raspberry Pi and adding it to the infrastructure.  Once I get these completed I will open-source them so make sure to check back for updates!

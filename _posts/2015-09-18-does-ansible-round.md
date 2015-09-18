---
layout: post
title: "Does Ansible Round?"
date: 2015-09-18 21:35:00
author: Mitchell Artin
tags: ansible programming
category: blog
---
Ansible collects facts about machines it connects to by default.  One of them when connecting to a RedHat 6.6 box is:

`"ansible_distribution_version": "6.6"`

This fact value is returned as type string.  When trying to use this in various inequalities (e.g. ansible_distribution_version > 6.4) you must typecast this to type int.  Typecasting in ansible is handled as follows:

`ansible_distribution_version|int`

So will this round 6.6 to 7 or will it truncate the value and return 6?

I couldn't find this issue documented anywhere (probably because everyone does it for themselves to figure it out).  Ansible does not round, it simply truncates.  6.6 \| int will return 6.

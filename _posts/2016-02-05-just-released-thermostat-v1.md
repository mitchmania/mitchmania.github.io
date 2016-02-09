---
layout: post
title: "Just Released: Thermostat V1.0"
date: 2016-02-05 19:35:00
author: Mitchell Artin
tags: open-source home-automation arduino c releases
category: blog
---
I have finally released the code for my network-based thermostat.  I have successfully used it as my sole thermostat in my house for the past three years so I am confident the majority of it is bug-free.  It also includes functionality to control light switches.  In the included screeenshot you can see I have it setup to control lights in my dining room, kitchen, etc.  With a slight copy/paste 

To build it you will need the [code on my Github](https://github.com/mitchmania/Arduino_Thermostat), an Arduino Mega 2560 (or suitable substitute with sufficient I/O pin space), an Arduino Ethernet Shield, 6 relays, 20x4 character LCD display, and DHT11 temperature sensor.  I have included a schematic of this build below.  It is network based and will return an HTML-formatted page if you visit the home-page.  Visit the /json page of the thermostat and you will get a formatted JSON response.  Both are shown below.  All requests are GET for simplicity of interfacing with the other devices and programs on my network.  I wrote in an NTP client so that the Thermostat can also display the current time on the LCD display.  It will also track time that cooling or heating systems are powered.  Each time it changes state (A/C started up, furnace shut off) it can optionally log to server.  It does this by sending a UDP packet with appropriate information to a listening server.  I used this in my house to log to a Splunk instance to keep track of my energy usage.

![Thermostat Responses]({{ site.baseurl }}/assets/posts/thermostat_responses.png)The two interfaces provided by the thermostat

![Thermostat LCD Display]({{ site.baseurl }}/assets/posts/thermostat_lcd.jpg)
LCD Display

More pictures of my build of this thermostat and its associated systems can be found on my [Home Automation](https://mitchmania.com/home-automation/) page.  I wrote the code for this thermostat in high school and therefore need to clean it up with some proper implementations of data structures.  Turns out I built a version of a queue using a string in this code before I even knew what a queue data structure was!  Many updates to come as I advance this project along with my home automation system.
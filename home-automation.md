---
layout: page
title: Home Automation
permalink: /home-automation/
---

My first project when I was a freshman in college was to create a network-connected thermostat based on an Arduino.  The code was messy but I learned a lot about networking and automation in the process.  I have included my original iteration at the bottom of this page.  After I gained more experience I wanted a more flexible development platform and redid the project in Python using a Raspberry Pi.  
<h3>Current Design</h3>
<img src="{{"/assets/img/rpi_thermostat_overview.png" | prepend: site.baseurl }}">
I used a generic 8" touchscreen LCD panel in a 3D printed case as a display.  I wrote a dead simple GUI in Tkinter that was easy to operate using a touchscreen.  I stripped a lot of unrelated functionality from the GUI that was in my original iteration below as I realized it was much less confusing.  All of the functionality that is available in the GUI is also exposed as on a REST API.  I interface with the HVAC system using the same 8-channel relay board I used with the Arduino.
<h3>First Design</h3>
At the core of any home automation system is an easy-to-use user interface.  In the center hallway of my house is my Arduino Thermostat and 24" touch panel.  This touch panel is connected to a Foxconn AMD "Book Computer" running Windows 8.1.  The program you see in the image below is my VB.Net application for user control.  It interfaces with my backend systems using mostly RESTful APIs.  It's on my To-Do list to make this program use REST API interconnects exclusively.
<img src="{{ "/assets/img/cera_diagram.png" | prepend: site.baseurl }}">
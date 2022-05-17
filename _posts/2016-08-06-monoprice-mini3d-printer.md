---
title: "Monoprice Mini3D Printer"
date: "2016-08-06"
categories: [3DPrinting]
published: true
---

[](images/monoprice.jpg)

I will start out by saying, the MonoPrice Mini3D printer is amazing and for $200 you cannot go wrong!

Don't forget to order your filament:

[https://www.amazon.com/gp/product/B00J0HC4QC](https://www.amazon.com/gp/product/B00J0HC4QC)

After you unbox and set it up, the next thing you need to do is install Cura.  Cura is a program that "slices" 3D models into parts the printer can understand.  I recommend Cura 15.04 (not the latest 2.x as it still is missing features and has bugs).

**Cura Download:**

[https://ultimaker.com/en/products/cura-software/download-request/70](https://ultimaker.com/en/products/cura-software/download-request/70){:target="_blank"}

After you install the software, open the program and ensure you setup the machine (choose Ultimaker in the wizard and then customize it) with the following settings.  Pay attention to the size of the printer area which is 120X120.  This is necessary to ensure the machine does not think it can move further that it actually can (this will cause damage to your printer).

![](images/Screen-Shot-2016-08-14-at-9.53.30-PM.png)

**Next, download a 3D model from one of the following sites:**

[http://www.3dkitbash.com/free3dmodels/](http://www.3dkitbash.com/free3dmodels/){:target="_blank"}

[http://www.thingiverse.com/thing:763622](http://www.thingiverse.com/thing:763622){:target="_blank"}

Open Cura and load the model.  Set your settings to the following:

![](images/Screen-Shot-2016-08-14-at-9.43.49-PM.png)
![](images/Screen-Shot-2016-08-14-at-9.44.00-PM.png)

Use the following code for start/end-gcode:
```
**start.gcode:**

M190 S55 ;Uncomment to add your own bed temperature line (55 deg. C for the plate) M109 S230 ;Uncomment to add your own temperature line (230 deg. C for the extruder)

G21 ;metric values G90 ;absolute positioning M82 ;set extruder to absolute mode M107 ;start with the fan off G28 X0 Y0 ;move X/Y to min endstops G28 Z0 ;move Z to min endstops G1 Z15.0 F6000 ;move the platform down 15mm G92 E0 ;zero the extruded length G1 F200 E3 ;extrude 3mm of feed stock G92 E0 ;zero the extruded length again G1 F6000 ;Fix the temp flux M301 P20 I0.02 D250 M501 M500 ;Put printing message on LCD screen M117 Printing...


**end.gcode:**
```
```
M104 S0 ;extruder off M140 S0 ;heated bed heater off (if you have it) M106 T45 ;fan to turn off when at 45deg C G91 ;relative positioning G1 E-1 F300 ;retract the filament a bit before lifting the nozzle, to release some of the pressure G1 Z+0.5 E-5 X-20 Y-20 F6000 ;move Z up a bit and retract filament even more G28 X0 Y0 ;move X/Y to min endstops, so the head is out of the way M84 ;steppers off G90 ;absolute positioning
```

To learn more about these codes check out this link:

[http://reprap.org/wiki/G-code](http://reprap.org/wiki/G-code){:target="_blank"}

Once complete, you can either print directly to the SD card (by saving the GCode to the SD card), or directly to the printer via USB. (I suggest to the SD card and then you do not need to keep you computer next to the printer the entire print).

Congrats!  You should now have a great 3D model.  :)

**Tweak sites:**

[](https://hackaday.com/2016/07/07/modding-the-monoprice-mp-mini-printer/){:target="_blank"}

 

**If you want to create your own 3D models check out the following:**

[https://www.tinkercad.com](https://www.tinkercad.com){:target="_blank"}

 

Happy Printing!

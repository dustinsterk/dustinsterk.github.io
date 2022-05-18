---
title: "Tracking airplanes in real time up to 400+ miles, with the use of RTLSDR and Coax Cable"
date: "2014-11-29"
categories: [RTLSDR]
published: true
---

![](../images/dump1090.jpg)
Here is a fun project that you can do that allows you to track airplanes in real time for less than $50.

Tools needed:

USB RTL-SDR (hardware that can capture radio waves): [http://www.amazon.com/NooElec-RTL-SDR-RTL2832U-Software-Packages/dp/B008S7AVTC](http://www.amazon.com/NooElec-RTL-SDR-RTL2832U-Software-Packages/dp/B008S7AVTC){:target="_blank"}

External Antenna Connector (optional as it includes a mini antenna with the above USB device):  [http://www.amazon.com/coaxial-cable-female-right-angle/dp/B00CKG6T9I/](http://www.amazon.com/coaxial-cable-female-right-angle/dp/B00CKG6T9I/){:target="_blank"}

Dump 1090 (software that logs the data and shows the planes in realtime on google maps): [https://github.com/antirez/dump1090](https://github.com/antirez/dump1090){:target="_blank"}

10-15 Feet of Coax Cable (any scraps will do).

 

Collinear Antenna build with coax cable (optional):

 

[Video Link](https://www.youtube.com/watch?feature=player\_embedded&v=TkUYdCPFXXs){:target="_blank"}

**Instructions:**
Install your favorite version of Linux, Dump 1090.  Plug in your USB hardware.  Execute the following:

```
./dump1090 --interactive --net

Finally open the browser and browse to http://localhost:8080 to see live traffic.
```

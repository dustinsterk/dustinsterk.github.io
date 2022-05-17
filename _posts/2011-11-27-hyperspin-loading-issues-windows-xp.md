---
title: "HYPERSPIN LOADING ISSUES – WINDOWS XP"
date: "2011-11-27"
categories: [Hyperspin]
published: true
---

![](images/logo-300x114.png)

I was having a strange problem with the arcade software HyperSpin. I had to install the hacked ATI video drivers created by Calamity for my Raedon Graphics Card to be able to use the arcade monitors [http://mame.groovy.org/WindowsATIDrivers/](http://mame.groovy.org/WindowsATIDrivers/){:target="_blank"}.

When opening Hyperspin, the process would launch but then just disappear, no error, no log created…nothing! After messing with the computer (installing .NET, flash, silverlight, everything I could think of ) I found a solution! Apparently there is a bug with HyperSpin in where if there are too many “Mode Lines” in the graphics card driver it crashes. Luckily I fixed this issue: Download a program called WinModelines [http://www.geocities.ws/podernixie/htpc/modeline-en.html](http://www.geocities.ws/podernixie/htpc/modeline-en.html){:target="_blank"} and open it on the new arcade machine. Delete the resolutions you are not using and get the list down to under 60 modes. Apply the changes and restart windows! Viola! Hopefully this is fixed in v2.0 of Hyperspin. Happy Gaming!

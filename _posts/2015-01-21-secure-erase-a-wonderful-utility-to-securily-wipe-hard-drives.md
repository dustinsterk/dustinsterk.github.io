---
title: "Secure Erase – A Wonderful Utility to Securily Wipe Hard Drives"
date: "2015-01-21"
---

[![header-acs](images/header-acs.gif)](http://104.167.119.213/wp-content/uploads/2015/01/header-acs.gif)

I was looking for a utility to wipe a stack of old hard drives that I had in my lab.  We have all heard of Dariks Boot and Nuke, but I was looking for something that was Federally approved (HIPPA, SOX, etc.).  I stumbled upon Secure Erase which was created by G.F. Hughes, D.M. Commins, and T. Coughlin ([Source](http://cmrr.ucsd.edu/people/Hughes/secure-erase.html "Source")).  From the documentation it states it is the following: “The ANSI T-13 committee which oversees the ATA (also known as IDE) interface specification and the ANSI T-10 committee which governs the SCSI interface specification have incorporated into their standards a command feature known as Secure Erase (SE).  Secure erase is a positive easy-to-use data destroy command, amounting to “electronic data shredding.”  It completely erases all possible user data areas by overwriting, including the so-called g-lists that contain data in reallocated disk sectors (sectors that the drive no longer uses because they have hard errors in them).  SE is a simple addition to the existing “format drive” command present in computer operating systems and storage system software and adds no cost to hard disk drives.  Since the Secure Erase command is carried out within a hard disk drive it doesn’t require any additional software to implement.”

Perfect!  Just what I needed.

The next step is to create a USB bootable drive (MSDOS) and then copy the HDDErase.exe to it.  I used my favorite USB creation utility ([rufus](https://rufus.akeo.ie/)) and booted up a machine with the hard drive I wanted to securely erase.  Within 60 minutes it was complete and safely destroyed!  Thanks for a wonderful utility!

You can download Secure Erase here: [HDDEraseWeb.zip](http://cmrr.ucsd.edu/people/Hughes/documents/HDDEraseWeb.zip)

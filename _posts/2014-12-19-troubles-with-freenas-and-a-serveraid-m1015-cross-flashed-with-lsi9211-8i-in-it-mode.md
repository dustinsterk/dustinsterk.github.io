---
title: "Troubles with FreeNAS and a ServeRAID M1015 cross flashed with LSI9211-8i in IT mode"
date: "2014-12-19"
categories: [FreeNAS]
published: true
---

![](../images/logo11.png)

For anyone looking to build a NAS device I highly recommend FreeNAS.  It has a variety of options but I was most interested in NFS/iSCSI for my Vmware ESXi lab.

[http://www.freenas.org/](http://www.freenas.org/){:target="_blank"}

I built a white box FreeNAS server and was having some troubles with my new M1015 SAS card.  I flashed it according to this post and I verified the firmware was correct (P16 as of the newest release).

[http://www.servethehome.com/ibm-serveraid-m1015-part-4/](http://www.servethehome.com/ibm-serveraid-m1015-part-4/){:target="_blank"}

For whatever reason the card would not recognize my drives that I had attached.  After an hour of troubleshooting I realized that there is a difference in breakout cables.  There are two types; reverse and forward cables.  You must purchase forward cables otherwise your drives will never be detected!  You can find a link to the correct cables below:

Correct:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816116097](http://www.newegg.com/Product/Product.aspx?Item=N82E16816116097){:target="_blank"}

Incorrect:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816133033](http://www.newegg.com/Product/Product.aspx?Item=N82E16816133033){:target="_blank"}

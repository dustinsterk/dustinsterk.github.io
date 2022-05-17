---
title: "Ubiquiti UniFi Access Points – Setting RSSI"
date: "2014-12-03"
---

[![UniFi](images/UniFi-300x199.png)](http://104.167.119.213/wp-content/uploads/2014/12/UniFi.png)

Minimum RSSI works by kicking wireless clients that fall below the configured RSSI threshold. RSSI is a vendor-specific value. With UniFi, RSSI & SNR are synonymous. As long as a user remains above the RSSI threshold (SNR), they won’t be kicked.

If the Minimum RSSI value is 20dB, clients whose SNR drops to 19dB, 18dB, etc. will be kicked, allowing them to find a better access point.

This is very useful if you have multiple AP’s in a smaller location.  Sure, you can adjust the “power” of each access point, but I find this setting makes it easier to fix certain machines from holding to a connection that is losing signal strength.

To set this value for each Access Point you can follow the below steps:

# Steps

* * *

Starting in v3.1.3, minimum RSSI configuration is done through _**config.properties**_ file under **each _\[UniFi base\]/data/sites/the\_site_** directory. The reason behind this decision is that (1) it is an advanced feature. (2) it requires a fine degree granularity of configuration down to each AP and each band, hence quite cumbersome if done in UI. A basic overview of the steps:

1. In controller, create (or modify) _**config.properties**_ file under each _**\[UniFi base\]/data/sites/the\_site**_ directory
2. For each needed **AP** and **band** (n/g or n/a), add a mapping line in following format:
3. config.minrssi.\[AP MAC addr\].\[ng|na\]=\[Minimum RSSI value\]

NOTE: There is **NO** '**:**' nor '**\-**' in between MAC address bytes. \[ng|na\] means 'ng' **OR** 'na', 'ng' is 2.4 GHz band and 'na' is 5 GHz band.

Trigger a **re-provision** (NOT restart) to the AP. for example, enable/disable or disable/re-enable guest portal, changing TX power of an AP, etc. If you don't want to re-provision entire network, you can only re-provision selected APs to make it effective on those APs.

config.minrssi.002712345678.ng=20
config.minrssi.dc9f22345678.ng=20
config.minrssi.002732345678.na=20
config.minrssi.002742345678.ng=20

# Example

* * *

1\. SSH to UniFi controller and change directory to UAP site:

##SSH into UAP##
ssh ubnt@<unifi\_controller\_ip\_address>
password: ubnt (default)

##Default path to UniFi default site##
Linux: /usr/lib/unifi/data/sites/default
Mac: /Applications/Unifi.app/Contents/Resources/data/sites/default
PC: C:\\Users\\_username_\\Ubiquiti UniFi\\data\\sites\\default

2\. When setting min RSSI for first time, you'll likely need to create the file **config.properties** since it doesn't exist yet. In this example, we'll use a file editor like**vi**. Then add entries for each UAP under the given site (one entry per radio band). Then save the file and quit the editor.

##Create config.properties file or simply open using vi editor##
sudo vi config.properties
\*
\*
\*

##add entries for dual-band UAP##
config.minrssi.dc9fdb700488.ng=25
config.minrssi.dc9fdb700488.na=25
\*
\*
\*

##Save and quit the editor##

:wq

3\. SSH into UAP to check that minimum RSSI is set using **ps** command.

##SSH into UAP##
ssh ubnt@<uap\_ip\_address>
password: ubnt (default)

##Check processes##
ps
830 ubnt      1568 S    /bin/stamgr -i 1 -b ng 20 -b na 20 -n 0

 

[https://community.ubnt.com/t5/UniFi-Configuration-Examples/UniFi-Set-minimum-RSSI-for-clients/ta-p/522637](https://community.ubnt.com/t5/UniFi-Configuration-Examples/UniFi-Set-minimum-RSSI-for-clients/ta-p/522637 "https://community.ubnt.com/t5/UniFi-Configuration-Examples/UniFi-Set-minimum-RSSI-for-clients/ta-p/522637")

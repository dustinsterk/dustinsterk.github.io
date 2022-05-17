---
title: "WordPress WP Mail SMTP Connection Timeout Issues – ERROR: Failed to connect to server: Connection timed out (110)"
date: "2014-09-26"
categories: [Wordpress]
published: true
---

If you have issues with sending SMTP messages from your wordpress host and have already checked the basics (username, password, firewall, ports, etc.) try to disable IPv6 on your server.

To do this add these lines below to the bottom of /etc/sysctl.conf

```
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Then run `sudo sysctl -p` or reboot the server.  Enjoy!

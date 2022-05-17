---
title: "WordPress file permissions"
date: "2015-05-14"
---

Thanks to my host CloudAtCost, I had to rebuild this entire site.  Their "migrate to Cloud Pro" is a total joke and does not migrate anything.  It instead deletes the servers that you must rebuild from scratch!  I have lost years of posts, but I was able to recover some data.

Here is the correct file permissions for Wordpress:

To set correct permissions you need to use these commands:

```
chown www-data:www-data -R *          # Let apache be owner
find . -type d -exec chmod 755 {} \;  # Change directory permissions rwxr-xr-x
find . -type f -exec chmod 644 {} \;  # Change file permissions rw-r--r--
```

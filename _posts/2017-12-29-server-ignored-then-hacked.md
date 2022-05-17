---
title: "If you ignore your server for long enough, you are going to have a bad time!"
date: "2017-12-29"
categories: [Hacked]
published: true
---
![](images/jollyroger.jpeg)

It has been quite some time since I have posted.  Life has been very busy and my ignorance with maintenance or updates on the server has finally bit me.  It looks like my entire site was overtaken by some malicious php files placed in my uploads directory.  Some basic forensics has shows that files were running a bunch of base64 decoded functions that were generating traffic to some strange sites, probably for ad revenue generation.  In any case, I had to blast my install and restore backups.  Note to self...ensure you lock down your /wp-content/uploads/ and /wp-includes/ directories with a .htaccess file and included the following:

```
<Files *.php>
    deny from all
</Files>
```

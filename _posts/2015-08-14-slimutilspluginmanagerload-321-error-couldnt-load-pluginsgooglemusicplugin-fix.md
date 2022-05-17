---
title: "Slim::Utils::PluginManager::load (321) Error: Couldn't load Plugins::GoogleMusic::Plugin Fix"
date: "2015-08-14"
categories: [LMS]
published: true
---

**I have successfully fixed the Google Music Plugin for Vortexbox 2.3 / LMS 7.9:**

See my full post here:

[http://forums.slimdevices.com/showthread.php?98526-Google-Music-Plugin/page11](http://forums.slimdevices.com/showthread.php?98526-Google-Music-Plugin/page11){:target="_blank"}

Errors include: 
```
[15-08-14 12:12:58.3474\] Slim::Utils::PluginManager::load (321) Error: Couldn't load Plugins::GoogleMusic::Plugin_ _\[15-08-14 12:14:29.7347\] main::init (368) Starting Logitech Media Server (v7.8.0, 1395395852, Fri Apr 18 13:29:51 EDT 2014) perl 5.018004_ _\[15-08-14 12:14:30.3405\] Slim::bootstrap::tryModuleLoad (285) Warning: Module \[Plugins::GoogleMusic::Plugin\] failed to load:_ _Error -- py\_eval raised an exception at /usr/lib/perl5/vendor\_perl/Inline/Python.pm line 221._ _BEGIN failed--compilation aborted at /usr/share/squeezeboxserver/Plugins/GoogleMusic/GoogleAPI.pm line 74._ _Compilation failed in require at /usr/share/squeezeboxserver/Plugins/GoogleMusic/Settings.pm line 20._ _BEGIN failed--compilation aborted at /usr/share/squeezeboxserver/Plugins/GoogleMusic/Settings.pm line 20._ _Compilation failed in require at /usr/share/squeezeboxserver/Plugins/GoogleMusic/Plugin.pm line 24._ _BEGIN failed--compilation aborted at /usr/share/squeezeboxserver/Plugins/GoogleMusic/Plugin.pm line 24._ _Compilation failed in require at (eval 962) line 1._ _BEGIN failed--compilation aborted at (eval 962) line 1._
```

**Fix:** First install pip: 
```
yum install python-pip
```

And then run the following: 
```
wget https://bootstrap.pypa.io/get-pip.py sudo python get-pip.py
```

Then I removed the broken plugin: 
```
cd /usr/share/squeezeboxserver/Plugins/ rm -rf GoogleMusic
```

Opened the plugins page and added the following repo and enabled the plugin (Google Plugin 0.4.2): http://nick7634.github.io/squeezebox-googlemusic/repository/repo.xml

Now to fix the SSL errors: 
```
_\[15-08-14 14:43:31.2259\] main::init (394) Starting Logitech Media Server (v7.9.0, 0.86.20150801git1438234070, Sat Aug 1 20:27:50 BST 2015) perl 5.018004_ _\[15-08-14 14:43:32.5819\] Plugins::GoogleMusic::Plugin::initPlugin (95) Not able to login to Google Play Music: SSLError: hostname 'android.clients.google.com' doesn't match either of '\*.google.com', '\*.android.com', '\*.appengine.google.com', '\*.cloud.google.com', '\*.google-analytics.com', '\*.google.ca', '\*.google.cl', '\*.google.co.in', '\*.google.co.jp', '\*.google.co.uk', '\*.google.com.ar', '\*.google.com.au', '\*.google.com.br', '\*.google.com.co', '\*.google.com.mx', '\*.google.com.tr', '\*.google.com.vn', '\*.google.de', '\*.google.es', '\*.google.fr', '\*.google.hu', '\*.google.it', '\*.google.nl', '\*.google.pl', '\*.google.pt', '\*.googleadapis.com', '\*.googleapis.cn', '\*.googlecommerce.com', '\*.googlevideo.com', '\*.gstatic.cn', '\*.gstatic.com', '\*.gvt1.com', '\*.gvt2.com', '\*.metric.gstatic.com', '\*.urchin.com', '\*.url.google.com', '\*.youtube-nocookie.com', '\*.youtube.com', '\*.youtubeeducation.com', '\*.ytimg.com', 'android.com', 'g.co', 'goo.gl', 'google-analytics.com', 'google.com', 'googlecommerce.com', 'urchin.com', 'youtu.be', 'youtube.com', 'youtubeeducation.com' at line 64_
```

**Fix:** Run in order: 
```
yum install gcc libffi-devel python-devel openssl-devel pip install cryptography pip install pyopenssl ndg-httpsclient pyasn1
```

Finally to fix passing in the device ID as seen here [https://github.com/hechtus/squeezebox-googlemusic/pull/83/files](https://github.com/hechtus/squeezebox-googlemusic/pull/83/files){:target="_blank"}:

**Fix:** 
```
cd /var/lib/squeezeboxserver/cache/InstalledPlugins/Plugins/GoogleMusic/ nano Settings.pm

eval { $googleapi->login($prefs->get('username'), decode\_base64($prefs->get('password')), $prefs->get('device\_id'));
```

SAVE THE FILE
```
nano Plugin.pm

eval { $googleapi->login($prefs->get('username'), decode\_base64($prefs->get('password')), $prefs->get('device\_id'));
```
SAVE THE FILE

REBOOT!

Now Vortexbox 2.3 and Logitech Media Server 7.9 will have Google Music working again!

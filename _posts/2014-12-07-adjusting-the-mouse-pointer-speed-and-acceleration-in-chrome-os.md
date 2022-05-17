---
title: "Adjusting the mouse pointer speed and acceleration in Chrome OS"
date: "2014-12-07"
---

You can adjust the trackpad/pointer settings via the GUI in Chrome OS, but I have found that the mouse speed still needs fine tuning.

Open a terminal window by pressing Ctrl+Alt+T.  At the crosh shell you can type the following command to see the usage of xset:

 xset m ?

The following output will be shown:

usage:  xset-mini option ...
    To set mouse acceleration and threshold:
         m \[acc\_mult\[/acc\_div\] \[thr\]\]    m default
    To turn auto-repeat off or on:
        -r \[keycode\]        r off
         r \[keycode\]        r on
         r rate \[delay \[rate\]\]

After playing with different settings, I have found the following command produces the most optimal feel and acceleration:

 xset m 0 0

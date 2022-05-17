---
title: "SublimeText PlainTasks Modification:  Adding pastdue / overdue and upcoming stats for date tracking"
date: "2015-07-24"
categories: [SublimeText]
published: true
---

![](../images/sublimetext-300x300.jpg)

I started using the PlainTasks plugin for SublimeText as my daily todo and work tracking list.  What a great plugin!

The one thing it was lacking in the default Stats to show in the bottom bar was the ability to track overdue, and upcoming dates.  With a simple modification to the Python script I have added just that.

Just edit the PlainTasks.py file and add the following code right after line 897 and then 926 in the file.  This will create new counters called $v (overdue), $t (due today), and $u (upcoming).

```

#Custom code (use this value to add to tags with @today to the due today counter), line 897 if i == "{{@today}}": tagToday = len(pend) 

```

```

#Overdue and due today tasks, line 926 tasks\_dates = \[\] overdue = 0 duetoday = 0 upcoming = 0 view.find\_all('(^\\s\*\[^\\n\]\*?\\s\\@(?:due)\\s\*(\\(\[\\d\\w,\\.:\\-\\/ \]\*\\))\[^@\]\*$)', 0, "\\\\2", tasks\_dates) date\_format = view.settings().get('date\_format', '(%y-%m-%d %H:%M)') tasks\_dates = \[PlainTasksCompleteCommand.check\_parentheses(date\_format, t, is\_date=True) for t in tasks\_dates\] present = datetime.now().strftime("%y-%m-%d %H:%M") #print ("Now:" + str(present)) for pastdue in tasks\_dates: pastdue = pastdue.replace('(','').replace(')','') #print ("Time Found:" + str(pastdue)) if len(pastdue) > 0: if datetime.strptime(pastdue, '%y-%m-%d %H:%M') < datetime.strptime(present, '%y-%m-%d %H:%M'): overdue = overdue + 1 elif datetime.strptime(pastdue\[:-6\], '%y-%m-%d') == datetime.strptime(present\[:-6\], '%y-%m-%d'): duetoday = duetoday + 1 elif datetime.strptime(pastdue\[:-6\], '%y-%m-%d') > datetime.strptime(present\[:-6\], '%y-%m-%d'): upcoming = upcoming + 1

msg = (msgf.replace('$o', str(pend)) .replace('$d', str(done)) .replace('$c', str(canc)) .replace('$n', str(done+canc)) .replace('$a', str(allt)) .replace('$percent', str(int(percent))) .replace('$progress', progress) .replace('$last', last) .replace('$v', str(overdue)) #New value for overdue .replace('$t', str(duetoday + tagToday)) #New value for due today (include both dates and items with @today tags) .replace('$u', str(upcoming)) #New value for upcoming ) return msg 

```

Now just edit your PlainTasks.sublime-settings User file and add the new variables. 

Mine looks like this:
```

{ "stats\_format": "$n/$a done, $v overdue, $t due today, $u upcoming: ☐$o ✔$d ✘$c, ($percent%) $progress: (Pend/Done/Canc) @critical {{@critical}}, @high {{@high}}, @low {{@low}}, @today {{@today}}", // if you want the statistics do not include the archived tasks: "stats\_ignore\_archive": true }

```

Finally you can open your TODO list and you will see the following at the bottom:

[](../images/Screen-Shot-2015-08-03-at-10.31.13-PM.jpg)

 

If you want to see what is upcoming you can install the "Filter Lines" plugin and then fold the list (from the Edit menu) by a regular expression.  I use the following to show due, critical and today tags.
```

(@+\\bcritical\*)|(@+\\btoday\*)|(@+\\bdue\*)

```

You can also add a custom keyboard shortcut in your sublime.keymap user settings, I added this one for command K, command L:

```

\[ { "keys": \["super+k", "super+l"\], "command": "fold\_to\_lines", "args": { "search\_type": "regex", "needle": "(@+\\\\bcritical\*)|(@+\\\\btoday\*)|(@+\\\\bdue\*)" } } \]

```

Happy coding!

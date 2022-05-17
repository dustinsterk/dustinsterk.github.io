---
title: "Vortexbox – Google Music Plugin – No sound"
date: "2015-05-13"
categories: [VortexBox]
published: true
---

![](images/VB.png)

I was able to setup the Google Music Plugin on my VortexBox and see all of my music in the browse nodes, but whenever I tried to play anything all I would get was ‘dead air’.

I saw the following error in the server log: Code:

```

Slim::Control::Request::execute (1888) Error: While trying to run function coderef \[Slim::Control::Commands::playlistJumpCommand\]: \[Can't call method "isa" on an undefined value at /usr/lib/perl5/vendor\_perl/Slim/Player/Squeezebox.pm line 762.\]

```

After looking around, I have stumbled across the solution to my issue: To fix, first SSH into your VB and run the following command: Code:

```

nano /usr/lib/perl5/vendor\_perl/Slim/Player/ProtocolHandlers.pm

```

Now scroll down and find the “%protocolHandlers” section and add the following line of code: Code:

```

https => qw(Slim::Player::Protocols::HTTP),

```

Now, save and exit the file. Restart your VortexBox and you should be all set.

Happy listening!

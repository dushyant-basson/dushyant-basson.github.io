---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-05-21"
slug: "ati-radeon-xpress-200m"
tags:
- linux
title: "ATI RADEON XPRESS 200M"
---

/etc/default/linux-restricted-modules-common added: `DISABLED_MODULES=""`

After upgrading to ubuntu7.04-

_On disabling the ATI driver in Restricted Driver Manager, it removed the driver:_  
```
(Reading database ... 
161526 files and directories currently installed.) 
Removing fglrx-control ... 
Removing fglrx-kernel-2.6.17-10-generic ... 
Removing xorg-driver-fglrx-dev ... 
Removing xorg-driver-fglrx ... 
Stopping atieventsd: done.
```

_On doing "sudo dpkg-reconfigure -pcritical xserver-xorg" :_  
```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; 
backup in /etc/X11/xorg.conf.20070416100138
```

_On enabling the ATI driver in Restricted Driver manager again:_  
```
Selecting previously deselected package xorg-driver-fglrx. 
(Reading database ... 161408 files and directories currently installed.) 
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx\_7.1.0-8.34.8+2.6.20.5-15.20\_i386.deb) ... 
dpkg: warning - unable to delete old directory \`/etc/ati': Directory not empty Setting up xorg-driver-fglrx (7.1.0-8.34.8+2.6.20.5-15.20) ...
```

_And after restart:_ IT WORKS!!!! :)

**Dual Monitor Support - ATI - Big Desktop** Ref.: http://ubuntuforums.org/showthread.php?t=301941  
_Added the following in /etc/X11/xorg.conf :_

```
Option "DesktopSetup" "horizontal" 
#Enable Big Desktop 
Option "Mode2" "1280x1024" 
#Resolution for second monitor 
Option "DesktopSetup" "LVDS,AUTO" 
#the types of monitors that is connected LVDS = LCD, CRT, AUTO 
Option "EnablePrivateBackZ" "yes" 
#Enable 3d support <= May Not Work 
Option "HSync2" "65" 
#This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "60" 
#This sets the refresh rate of the secondary display. 
```
_And rebooted with the other monitor plugged in. Horizontal big desktop loaded fine._

**fglrx-control** - Control panel for the ATI graphics accelerators   
To run: **fireglcontrol**

Useful ref.: http://ubuntuforums.org/showthread.php?p=1773544

---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-05-21"
slug: "broadcom-wireless-card"
tags:
- linux
title: "Broadcom wireless card"
---

Device: **BCM4318 \[AirForce One 54g\] 802.11g Wireless LAN Controller**

## If installed 'bcm43xx-fwcutter', blacklist it:  

`sudo nano /etc/modprobe.d/blacklist`  

Add: 

`blacklist bcm43xx`

## 'ndiswrapper'

'ndiswrapper' is a special Linux kernel module that allows you to use Windows network drivers (specifically, NDIS drivers) on a Linux system.

`sudo apt-get install ndiswrapper-common sudo apt-get install ndiswrapper-utils-1.9`

Then edit `/etc/modules` and add `ndiswrapper` in it.

## Unload 'bcm43xx'

`sudo rmmod bcm43xx`  

This unloads the bcm43xx driver (now the wireless interface won't be visible by iwconfig)

## Download driver

Download the windows driver:  
`ftp://ftp.support.acer-euro.com/notebook/aspire\_3020/driver/WLan%20Driver%20Broadcom%20802.11g%203.100.46.0.zip`

## Install driver

Extract and enter the directory. Run:

`sudo ndiswrapper -i bcmwl5.inf` 

*`installing bcmwl5 ... forcing parameter IBSSGMode from 0 to 2 forcing parameter IBSSGMode from 0 to 2`*

`sudo ndiswrapper -l` 

*`bcmwl5 : driver installed device (14E4:4318) present (alternate driver: bcm43xx)`*

## Load ndiswrapper module

`sudo modprobe ndiswrapper`

Then `iwconfig` will list `eth1`

Turn on the wi-fi button, then:  

`iwlist eth1 scan`

--

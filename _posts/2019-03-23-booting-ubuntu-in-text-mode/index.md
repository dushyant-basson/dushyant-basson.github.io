---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2019-03-23"
slug: "booting-ubuntu-in-text-mode"
tags:
- linux
title: "booting ubuntu in text mode"
---

### Back-up grub

`sudo cp /etc/default/grub /etc/default/grub-orig`

Edit the following in **/etc/default/grub**:

```
#GRUB\_CMDLINE\_LINUX\_DEFAULT="quiet splash"  
GRUB\_CMDLINE\_LINUX="text"  
GRUB\_TERMINAL=console
```

### Update grub

`sudo update-grub`  

Set systemd target. The **multi-user.target** unit groups many daemons and starts services such as **NetworkManager.service** and activates another target unit named **basic.target**

`sudo systemctl set-default multi-user.target`

### Check default target

`systemctl get-default`  

The above command links to: **/etc/systemd/system/default.target**

### List all target units

`systemctl list-units --type target --all`

### To reset to graphical target

`sudo systemctl set-default graphical.target`

--

---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-05-21"
slug: "fstab-messed-up-solution-tune2fs"
tags:
- linux
title: "fstab messed up - solution (tune2fs)"
---

On editing the hard-disk partitions, the UUIDs of the partitions may get changed, resulting in problems mounting the partitions (on booting up the system).

This can be fixed by getting the right UUID of the partition by the **tune2fs** command:  

`sudo tune2fs -l /dev/hda3`

Ref.: http://ubuntuforums.org/showthread.php?p=2429155

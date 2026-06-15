---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2019-03-22"
slug: "hostname-dns-resolve-osx-mac-lan"
tags:
- dns
- linux
- networking-2
- osx
title: "Resolve DNS of Hostname from OSX in a LAN"
---

This is a collection of some commands to diagnose the DNS resolution problems, from OSX in a local network having linux and mac machines.

On linux, edit: /etc/avahi/avahi-daemon.conf to set 'use-ipv6' to 'no', so avahi resolves the hostname to ipv4 address. Not sure if this affects the DNS resolution from a mac, but I set it to ipv4 anyway.

```
use-ipv6=no
```

Restart avahi-daemon on linux:

```
sudo systemctl restart avahi-daemon.service
```

Resolve mDNS/DNS hostname to IP address and vice-versa:

```
avahi-resolve-host-name onizu-asus.local
avahi-resolve-address 192.168.0.110
```

Scan for mDNS/DNS-SD services published on the local network:

```
mdns-scan
```

on OSX, run the DNS Service Discovery tool:

```
dns-sd -E
```

The domain should be listed in the output of the above command. But for me it doesn't list anything..

A system reboot works for me. The local hostname starts resolving on the mac. Not able to figure out why it stops working after a while..

--

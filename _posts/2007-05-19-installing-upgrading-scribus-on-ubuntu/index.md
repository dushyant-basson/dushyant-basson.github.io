---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-05-19"
slug: "installing-upgrading-scribus-on-ubuntu"
tags:
- linux
title: "Installing/Upgrading Scribus on Ubuntu"
---

## Add these to /etc/apt/sources.list: 
```
#Scribus - Primary repository 
deb http://debian.scribus.net/debian feisty main restricted 
deb-src http://debian.scribus.net/debian feisty main restricted 

#Scribus - Backup repository 
deb http://debian.tagancha.org/debian feisty main restricted 
deb-src http://debian.tagancha.org/debian feisty main restricted
```

## Then add the gpg-keys for these repositories:  
`sudo gpg --keyserver subkeys.pgp.net --recv-keys EEF818CF sudo gpg --armor --export EEF818CF | sudo apt-key add -`

## Update & upgrade

`sudo apt-get update` 

(might have to do this twice)

`sudo apt-get upgrade` 

This should show scribus as the package (or as one of the packages) to be upgraded. Proceed with upgrading.

## Install icc-profiles also: 

`sudo apt-get install icc-profiles`

Ref.: http://wiki.scribus.net/index.php/Getting\_Scribus\_on\_Ubuntu/Kubuntu\_up\_and\_running

--

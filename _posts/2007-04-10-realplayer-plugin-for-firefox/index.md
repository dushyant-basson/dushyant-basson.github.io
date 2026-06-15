---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-04-10"
slug: "realplayer-plugin-for-firefox"
tags:
- firefox
- linux
title: "RealPlayer plugin for Firefox"
---

## Remove 'Totem' player
**Totem** is the default player for realplayer media files in firefox. 

Remove the Totem plugin files in **/usr/lib/mozilla-firefox/plugins**: 
- libtotem-complex-plugin.so 
- libtotem-complex-plugin.xpt

`sudo rm /usr/lib/mozilla-firefox/plugins/libtotem-complex-plugin.\*`

## Install RealPlayer

Then install realplayer plugin for firefox:

Add this to **/etc/apt/sources.list**:  

`deb http://archive.canonical.com/ubuntu edgy-commercial main`

`sudo apt-get update`

`sudo apt-get install realplay`

--

---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-05-21"
slug: "upgrading-distribution-ubuntu"
tags:
- linux
title: "Upgrading Distribution - Ubuntu"
---

`sudo update-manager -c -d`

Upgraded from 6.10(edgy) to 7.04(feisty)

Total download: 700MB+

### Third party sources get disabled
> "Some third party entries in your soruces.list were disabled. you can re-enable them after the upgrade with the 'software-properties' tool or your package manager."

### Support for some applications ends 
> "Canonical Ltd. no longer provides support for the following software packages. you can still get support from the community. If you have not enabled community maintained software (universe), these packages will be suggested for removal in the next step. edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers gray-theme gtkhtml3.8 industrialtango-theme legacyhuman-theme libgtkhtml3.8-15 libjaxp1.2-java libsasl2 libstlport4.6c2 libxml-grove-perl outdoors-theme resilience-theme silicon-theme xkeyboard-config"

### Post upgrade issues - Right Alt Key not functioning properly
**Solution:**  Open **Keyboard Preferences > Layout Options** Third level choosers: Uncheck *"Press Right Alt key to choose 3rd level."*

--

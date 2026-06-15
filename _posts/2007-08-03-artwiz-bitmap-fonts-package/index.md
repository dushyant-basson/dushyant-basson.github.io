---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-08-03"
slug: "artwiz-bitmap-fonts-package"
tags:
- linux
title: "Artwiz - bitmap fonts package"
---

## Installing the package 

**Important:** Create the directory **/usr/lib/X11/fonts/misc** if it doesn't exist. If the package is installed without this directory existing, then the package may not work. In that case 'purge' the package with 'aptitude' command and then install again.  

`sudo aptitude install xfonts-artwiz`

## Enabling bitmapped fonts 

`sudo dpkg-reconfigure fontconfig-config` 

Then retain the first two options and enable bitmap fonts in the third question. 

Restart X.

Ref.: http://doc.gwos.org/index.php/HowToInstallArtwiz

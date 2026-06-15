---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-04-11"
slug: "enabling-mouse-wheel-scrolling-in-emacs"
tags:
- emacs
title: "Enabling mouse-wheel scrolling in Emacs"
---

## Temporary 

`M-: (mwheel-install)`

## Permanent 

Add the following in **.emacs** : 

`(cond (window-system (mwheel-install)))`

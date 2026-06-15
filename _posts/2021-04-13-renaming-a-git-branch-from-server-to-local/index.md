---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2021-04-13"
slug: "renaming-a-git-branch-from-server-to-local"
tags:
- git
title: "Renaming a git branch (from server to local)"
---

Recently got this useful info from [GitHub](https://github.com) on updating a git branch locally after renaming it on the server.

Assuming the branch's old name was '**main**' and it is renamed to '**master**', and its local clone exists, execute the following on local terminal:

```
git branch -m main master
git fetch origin
git branch -u origin/master master
git remote set-head origin -a
```

That should successfully complete the renaming of the branch (at the local end).

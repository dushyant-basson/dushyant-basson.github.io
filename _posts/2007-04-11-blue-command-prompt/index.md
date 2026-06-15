---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2007-04-11"
slug: "blue-command-prompt"
tags:
- linux
title: "Blue command prompt"
---

Add the following to ~/.bashrc 
```
export PS1="\\e\[1;34m\[\\u@\\h \\W\]\\$ \\e\[m "
```

Ref.: http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/ http://www.expertsrt.com/tutorials/Matt/CmdPrompt.html

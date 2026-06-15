---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2019-05-09"
slug: "removing-a-directory-from-the-git-repository-after-adding-it-to-gitignore"
tags:
- git
title: "Removing a directory from the git repository after adding it to .gitignore"
---



If a directory was added to `.gitignore` before pushing to the repository, it does not get pushed. But if the directory was already pushed, and later added to `.gitignore`, then to remove it from the repository:



```

git rm -r --cached dirToIgnore

git commit -m 'Removing the gitignored dir'

git push

```



The directory `dirToIgnore` should now be removed from the git repository.



Read on how to [use Git to deploy a project on a remote server](/blog/using-git-to-deploy-project-on-remote-server/).

---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2019-04-10"
slug: "using-git-to-deploy-project-on-remote-server"
tags:
- git
- linux
title: "Using Git to deploy a project on remote server"
---

Install **git** on the remote server (if it is not already).

On Ubuntu:

```
sudo apt-get update
sudo apt-get install git
```

Create an SSH key pair (locally):

```
ssh-keygen -C "email@domain.com"
```

Accept the default file to save the key. If a passphrase is entered, it would have to be entered every time during '`git push`'. The following two files would be created in **~/.ssh/**

**id\_rsa.pub** (public key)  
**id\_rsa** (identification)

Create an **authorized\_keys** file (if it is not present) on the remote server in **~/.ssh/** for the SSH daemon to accept the key:

```
touch ~/.ssh/authorized_keys
```

Copy the local SSH ID/key to the remote server's **authorized\_keys** in ~/.ssh/ as:

```
ssh-copy-id user@remoteServerIP
```

It would prompt for the passphrase if it was entered while generating the key (using ssh-keygen).

Create a local git repository, in a project directory (say ~/project01) that needs to be uploaded to the server. Then create a file in it to test the git transfer later:

```
cd ~/project01
git init
echo 'testing deployment via git' > example.txt 
```

On the remote server, initialise a bare repository in a directory (say ~/project01.git):

```
mkdir ~/project01.git && cd ~/project01.git
git init --bare
```

Set up a `post-receive` hook for **~/project01.git** on the remote server, to 'checkout' the git files into a remote project directory (say **~/project01**, as the local):

```
mkdir ~/project01
nano ~/project01.git/hooks/post-receive
```

Enter the following script code in this `post-receive` file:

```
#!/bin/sh
export GIT_WORK_TREE=/home/user/project01
git checkout -f master
```

Make `post-receive` executable:

```
chmod +x ~/project01.git/hooks/post-receive
```

Set up remote origin to the server (bare) repository, at the local end:

```
git remote add origin user@remoteServerIP:project01.git
```

Stage the content of the local repository and commit it:

```
cd ~/project01
git add example.txt
git commit -m "New sample file to test git transfer"
```

Push the sample file to the server, setting the remote as upstream:

```
git push --set-upstream origin master
```

The file should be available on the remote server at **~/project01** (created earlier).

_Note:_ It is recommended against using git as a deployment tool, for reasons as it does not track permissions. Read [here](http://gitolite.com/deploy.html).

Read how to [remove a directory from the git repository after adding it to .gitignore](/blog/removing-a-directory-from-the-git-repository-after-adding-it-to-gitignore/)

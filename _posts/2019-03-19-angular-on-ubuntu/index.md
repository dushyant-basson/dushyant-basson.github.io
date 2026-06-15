---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2019-03-19"
slug: "angular-on-ubuntu"
tags:
- angular
- linux
title: "angular on ubuntu"
---

check nodejs installation:

```
nodejs -v
```

check npm installation:

```
npm -v
```

```
sudo npm install -g npm@latest
sudo npm cache verify
npm -i
sudo npm install --no-optional
sudo npm init
sudo npm install -g @angular/cli
```

_Unhandled rejection Error: EACCES: permission denied, open '/home/onizu/.npm/\_cacache/tmp/b5bc4345'S: permission denie_

```
sudo chown -R $USER:$GROUP ~/.npm 
sudo chown -R $USER:$GROUP ~/.config
sudo chown -R root:YOUR_USERNAME /usr/local/lib/node_modules/
sudo chmod -R 775 /usr/local/lib/node_modules/
```

install git (if not installed):

```
sudo apt-get install git
git config --global user.email "you@example.com"
git config --global user.name "your name"
```

create workspace & app:

```
ng new my-app
```

serve app:

```
cd my-app
ng serve --open
```

the app should be available at: `http://localhost:4200/`

--

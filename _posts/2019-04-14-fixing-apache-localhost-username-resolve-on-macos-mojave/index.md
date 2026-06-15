---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2019-04-14"
slug: "fixing-apache-localhost-username-resolve-on-macos-mojave"
tags:
- osx
- apache
- httpd
- localhost
title: "Fixing Apache localhost/~username resolve on macOS Mojave"
---

Edit **/etc/apache2/httpd.conf**  

```
sudo vi /etc/apache2/httpd.conf

```

Uncomment the following lines:

```
#LoadModule vhost_alias_module libexec/apache2/mod_vhost_alias.so
#Include /private/etc/apache2/extra/httpd-vhosts.conf
#LoadModule userdir_module libexec/apache2/mod_userdir.so
#Include /private/etc/apache2/extra/httpd-userdir.conf

```

Uncomment the following in **/private/etc/apache2/extra/httpd-userdir.conf** :

```
#Include /private/etc/apache2/users/*.conf

```

Create the file **/private/etc/apache2/users/yourUserName.conf** if it doesn't exist:

```
sudo vi /private/etc/apache2/users/yourUserName.conf

```

Add the following in this file:

```
<Directory "/Users/yourUserName/Sites/">
  Options Indexes MultiViews
  AllowOverride None
  Require all granted
</Directory>

```

For running PHP, uncomment the following line in **/etc/apache2/httpd.conf** . The version of PHP in the module name may vary as per the currently installed version (7 in this case):


```
#LoadModule php7_module libexec/apache2/libphp7.so

```

Restart Apache server:

```
sudo apachectl restart

```

The local webserver should now be available at **http://localhost/~yourUserName/** , referring to the location **~/yourUserName/Sites/**

Also read about [resolving DNS of a hostname](/blog/hostname-dns-resolve-osx-mac-lan/) from OSX in a local network having linux and mac machines

---
author: "Dushyant Basson"
categories:
- uncategorized
date: "2021-02-12"
slug: "installing-mongodb-on-cpanel-whm-centos-along-with-the-php-extension"
tags:
- apache
- centos
- cpanel
- mongodb
- php-2
title: "Installing MongoDB on cPanel / WHM / CentOS along with the PHP extension"
---

## Attempts to install MongoDB on a cPanel based CentOS VPS

While trying to install MongoDB on a cPanel based CentOS server, I found the system configurations were customized by cPanel. Many commands were unavailable in bash, and some package installations were disabled in `/etc/yum.conf` (e.g., `php*` in the 'exclude' list blocked the installation of `php-devel` package, etc.). This document outlines the key steps to install MongoDB on such a system.

I referred to the official documentation on mongodb.com to install MongoDB on CentOS. At the time of writing this, the version provided in the documentation to install was 4.4.

Ref. [https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/)

1. Create a repo file in **/etc/yum.repos.d** called **mongodb-org-4.4.repo** with this content:

    ```
    [mongodb-org-4.4]
    name=MongoDB Repository
    baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/4.4/x86_64/
    gpgcheck=1
    enabled=1
    gpgkey=https://www.mongodb.org/static/pgp/server-4.4.asc
    ```

2. Install the MongoDB packages:

    `yum install -y mongodb-org`

3. Configure MongoDB to auto-start on system startup / reboot:

    `chkconfig mongod on`  

    Output:  

    `Note: Forwarding request to 'systemctl enable mongod.service'.`

4. Start MongoDB:

    `service mongod start`

    Output:

    `Redirecting to /bin/systemctl start mongod.service`

5. Install MongoDB PHP Extension

    Note that cPanel has tools like `pecl`, `phpize`, etc., located in `/opt/cpanel/ea-php74/root/usr/bin/`. Change the version in "ea-php\*" according to your PHP version. Multiple versions of PHP might be installed, so choose the version used for the project.

    To run `phpize` followed by `./configure` while compiling a package yourself, use:

    `/opt/cpanel/ea-php74/root/usr/bin/phpize && ./configure --with-php-config=/opt/cpanel/ea-php74/root/usr/bin/php-config`

    PHP extension installation with the `pecl` tool:

    `/opt/cpanel/ea-php74/root/usr/bin/pecl install mongodb`

    Ref. [https://www.php.net/manual/en/mongodb.installation.pecl.php](https://www.php.net/manual/en/mongodb.installation.pecl.php)

    Note that some references suggest installing `'mongo'` as the extension, but it's the old extension. With PHP 7, you need to install `'mongodb'` as the extension.

    A successful installation should end with:

    ```
    Build process completed successfully
    Installing '/opt/cpanel/ea-php74/root/usr/lib64/php/modules/mongodb.so'
    install ok: channel://pecl.php.net/mongodb-1.9.0
    Extension mongodb enabled in php.ini
    ```

    Info: Location of `php.ini` on cPanel:

    `/opt/cpanel/ea-*/root/etc/php.ini`

6. Restart Apache:

    `service httpd restart`

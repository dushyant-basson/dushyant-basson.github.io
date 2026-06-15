---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2021-03-06"
slug: "xdebug-3-x-configuration-for-php-apache-on-a-docker-container-debugging-via-vscode"
tags:
- apache
- docker
- php-2
- php-debugging
- vscode
- xdebug
title: "XDebug 3.x configuration for PHP/Apache on a Docker container & debugging via vscode"
---

## **XDebug configuration**

**'xdebug 3.x**' has some different configuration parameters than the older 2.x version. Here is the quick set of parameters required for xdebug to work with **Apache** running on a **Docker** container:

```
xdebug.client_host=host.docker.internal
xdebug.client_port=9003
xdebug.start_with_request=yes
xdebug.mode=debug
xdebug.discover_client_host=1
```

Note that client\_host value '`host.docker.internal`' may not work on linux.

Another important part here is the value for `'xdebug.discover_client_host`' . It must be set ON for xdebug to work with Apache. It does work with CLI with this option OFF also, but didn't seem to work with Apache without this option set to 1.

> Caveat: **xdebug.mode** as '**debug**' , the improved/formatted output of var\_dump() that xdebug gives, gets turned off. In order to have formatted var\_dump() output, **xdebug.mode** needs be set to '**develop**'. In 'develop' mode, vscode-debugger does not work. This is due to the changes in version 3 of xdebug.
> 
> UPDATE: xdebug.mode can have comma-separated multiple values as:
> 
> `xdebug.mode=develop,debug`

For the PHP-Apache Docker image I was using (php:7.4-apache), the `php.ini` was not created by default. So I copied the development-sample `/usr/local/etc/php/php.ini-development`

The xdebug config is set in a separate file: `/usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini`

## **vscode config (launch.json)**

In order to work with the vscode extension ['**PHP Debug**'](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) (by Felix Becker), a vscode configuration file (**launch.json**) needs to be created. An important parameter here is '**pathMappings**'. Here's a working example of **launch.json**:

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9003,
            "pathMappings": {
                "/var/www/html/projectDir": "${workspaceFolder}"
            }
        }
    ]
}
```

The first part in "**pathMappings**" value corresponds to the document-root in Apache on **Docker**. The latter is the corresponding local path on the host system. ${workspaceFolder} is a convenient variable translating to the location of the project containing the '**.vscode**' directory.

The other customisation is the "**port**" value ('**9003**' for xdebug 3.x), matching with the **xdebug.client\_port** value in PHP.

A useful PHP function to get the stats for xdebug is: **`xdebug_info()`**

This set up should make 'PHP Debug' extension to work in vscode by assigning breakpoints in the code. In case the debugger does not stop at the breakpoints, xdebug can be tested by setting the following parameter in launch.json:

```
"stopOnEntry": true
```

This makes the debugger to stop at the entry point of the PHP script.

Also read about [deploying a template in Visual Studio](/blog/deploying-a-template-in-visual-studio/) _(not vscode)_

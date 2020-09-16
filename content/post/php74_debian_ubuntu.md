+++
author = "Ryan Plyler"
title = "Installing PHP 7.4 for Nginx on Debian/Ubuntu Systems"
date = "2020-09-16"
description = "How to install php 7.4 on debian 10 (buster) and other debian/ubuntu variables for a LEMP stack"
tags = [
    "php",
    "php-fpm",
    "fastcgi",
    "nginx",
    "webserver",
    "configuration",
]
categories = [
    "sysadmin",
    "stacks",
    "howto",
]
series = ["LEMP Stack"]
#aliases = ["migrate-from-jekyl"]
+++

In this tutorial we'll be installing the latest `php7.4` and `php7.4-fpm` on a Debian 10 (Buster) system. Similar practices can be followed for Ubuntu Variants.

## Step 1: Update System

```
sudo apt update
sudo apt upgrade -y && sudo reboot
```

## Step 2: Add Repositories

Add the GPG key

```
sudo apt -y install lsb-release apt-transport-https ca-certificates 
sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
```

Add the repository

```
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/php.list
```

## Step 3: Add Install PHP 7.4 on Debian 10 / Debian 9 / Ubuntu

```
sudo apt update
```

```
sudo apt -y install php7.4
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils libapache2-mod-php7.4 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libbrotli1
  libcurl4 libgdbm-compat4 libgdbm6 libjansson4 libldap-2.4-2 libldap-common liblua5.2-0 libnghttp2-14 libpcre2-8-0 libperl5.28 librtmp1
  libsasl2-2 libsasl2-modules libsasl2-modules-db libsodium23 libssh2-1 perl perl-modules-5.28 php-common php7.4-cli php7.4-common php7.4-json
  php7.4-opcache php7.4-readline psmisc ssl-cert
Suggested packages:
  apache2-doc apache2-suexec-pristine | apache2-suexec-custom www-browser php-pear libsasl2-modules-gssapi-mit | libsasl2-modules-gssapi-heimdal
  libsasl2-modules-ldap libsasl2-modules-otp libsasl2-modules-sql perl-doc libterm-readline-gnu-perl | libterm-readline-perl-perl make
  libb-debug-perl liblocale-codes-perl openssl-blacklist
The following NEW packages will be installed:
  apache2 apache2-bin apache2-data apache2-utils libapache2-mod-php7.4 libapr1 libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libbrotli1
  libcurl4 libgdbm-compat4 libgdbm6 libjansson4 libldap-2.4-2 libldap-common liblua5.2-0 libnghttp2-14 libperl5.28 librtmp1 libsasl2-2
  libsasl2-modules libsasl2-modules-db libsodium23 libssh2-1 perl perl-modules-5.28 php-common php7.4 php7.4-cli php7.4-common php7.4-json
  php7.4-opcache php7.4-readline psmisc ssl-cert
The following packages will be upgraded:
  libpcre2-8-0
1 upgraded, 36 newly installed, 0 to remove and 7 not upgraded.
Need to get 15.0 MB of archives.
After this operation, 76.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
```

## Step 4: Install Common PHP packages

```
sudo apt-get install php7.4-{bcmath,bz2,intl,gd,mbstring,mysql,zip,curl}
```

## Step 5: Install PHP7.4-fpm

This is the fastcgi service that allows you to use PHP with Nginx. This tutorial,
covers setting up and Nginx site powered by php. (Coming soon)

Disable Apache2

```
sudo systemctl disable --now apache2
```

Install php7.4-fpm

```
sudo apt-get install nginx php7.4-fpm
```

You're all set! The unix socket for php7.4-fpm should be located at `/var/run/php/php7.4-fpm.sock`
Checkout the Nginx configuration guide of this series on installing and configuring a LEMP stack to run your PHP powered sites!

**Credits**

The bulk of this content comes from  the editors at [https://computingforgeeks.com/how-to-install-latest-php-on-debian/](https://computingforgeeks.com/how-to-install-latest-php-on-debian/)





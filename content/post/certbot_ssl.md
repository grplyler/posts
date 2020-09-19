+++
author = "Ryan Plyler"
title = "Adding Free SSL/TLS Certificates with Certbot & NGinx"
date = "2020-09-19"
description = "Let's encrypt is a global initiative to secure web traffic offering free SSL/TLS certificates. Learn how to use lets encrypt with NGinx"
tags = [
    "ssl",
    "tls",
    "html",
    "letsencrypt",
    "dns",
    "subdomains"
]
categories = [
    "webmaster",
    "sysadmin"
]
draft = true
+++

If you haven't already heard, [Lets Encrypt](https://letsencrypt.org) is a non-profit
certificate authority providing over `250 million` TLS certificates that power and secure
the web. Lets Encrypt has some pretty big sponsors and donors, including:

* Cisco
* Google
* Mozilla 
* Github 
* IBM
* Redhat
* and many more

This blog uses Let's Encrypt TLS certficates too! So without further ado, lets
walkthrough setting up and nginx subdomain-based virtual host, and then slap a
TLS certificate on it for some extra street cred.


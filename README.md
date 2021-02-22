# Self-Hosting Security Dashboard for YunoHost

[![Integration level](https://dash.yunohost.org/integration/REPLACEBYYOURAPP.svg)](https://dash.yunohost.org/appci/app/REPLACEBYYOURAPP) ![](https://ci-apps.yunohost.org/ci/badges/REPLACEBYYOURAPP.status.svg) ![](https://ci-apps.yunohost.org/ci/badges/REPLACEBYYOURAPP.maintain.svg)  
[![Install REPLACEBYYOURAPP with YunoHost](https://install-app.yunohost.org/install-with-yunohost.svg)](https://install-app.yunohost.org/?app=REPLACEBYYOURAPP)

*[Lire ce readme en français.](./README_fr.md)*

> *This package allows you to install REPLACEBYYOURAPP quickly and simply on a YunoHost server.  
If you don't have YunoHost, please consult [the guide](https://yunohost.org/#/install) to learn how to install it.*

## Overview
There is no security without proper monitoring. SHSD aims to provide a synthetic overview of the security status of accounts and devices in a self-hosting context. It is tailored to users who can deploy self-hosting solutions (such as Yunohost or Sandstorm) or who have an account (mail address) on such hosting, without requiring expert security knowledge.

**Shipped version:** 0.1.3

## Screenshots

![](https://github.com/dynamid/shsd/blob/master/doc/screenshot.png)


There is no security without proper monitoring. SHSD aims to provide a synthetic overview of the security status of accounts and devices in a self-hosting context. It is tailored to users who can deploy self-hosting solutions (such as Yunohost or Sandstorm) or who have an account (mail address) on such hosting, without requiring expert security knowledge.

Progressively, it will present a couple of very simple indicators on account usage and local devices.

Some examples of what we aim to detect :

* An account compromised through the compromission of a low-security device such as a smartphone
* A local device infected with MIRAI

Some examples of what we explicitely **do not** aim to detect :

* APTs :-)

SHSD typically targets SOHO networks with less than 10 devices and less than 10 accounts.

# What is SHSD currently doing ?

On this very early stage, SHSD monitors usage of mail accounts to detect accounts compromission :

* It parses the dovecot-imap log in /var/logs/mail.log
* It stores the IPs from which each account has been authenticated
* For each IP, GeoIP is used to retrieve the associated AS and geolocation (with variable precision)
* It renders the authentications geolocations on a map

It is aimed to be watched by the final users :

* Each user should use SHSD as its default homepage (rather than a typically blank page)
* Each user can see from where his account has been used
* If some points are in a strange area (a foreign country or an anormal ISP for instance), user should detect this unusual pattern and then ask the hoster/forums. It may mean that the account has been used by a third-party
* SHSD focus on the detection part, the remediation is out of our scope. We think that the global community on forums is quite efficient for remediation as soon as problems are detected.

 In a nutshell, SHSD tries to leverage users' unconscious reactions confronted with some change on a page which is usually quite static.


## Links

 * Report a bug: https://github.com/YunoHost-Apps/shsd_ynh/issues
 * App website: Link to the official website of this app.
 * Upstream app repository: https://github.com/dynamid/shsd
 * YunoHost website: https://yunohost.org/

---

## Developer info

Please send your pull request to the [testing branch](https://github.com/YunoHost-Apps/shsd_ynh/tree/testing).

To try the testing branch, please proceed like that.
```
sudo yunohost app install https://github.com/YunoHost-Apps/shsd_ynh/tree/testing --debug
or
sudo yunohost app upgrade shsd -u https://github.com/YunoHost-Apps/shsd_ynh/tree/testing --debug
```


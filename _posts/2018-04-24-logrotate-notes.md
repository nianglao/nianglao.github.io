---
layout: post
title:  "Cron and Logrotate"
date:   2018-04-24 00:39:01 +0800
categories: misc
---

# Crons

There are two kinds of cron job: **cron** and **anacron** on Linux.

**anacron** run with a frequency specified in days. It's configuration under */etc/anacrontab*. Cron jobs under */etc/cron.daily*, */etc/cron.weekly*, */etc/cron.monthly* are triggered by *anacron*. *START_HOURS_RANGE* defines the *anacron* start time period.

# Logrotate

**logrotate** is always triggered by **anacron** with */etc/cron.daily/logrotate*. Logrotate default config is */etc/logrotate.conf*. In default config, *include /etc/logrotate.d* means all config under */etc/logrotate.d* will be included. 

Logrotate will rotate logs according to configuration and refering to log file status in */var/lib/logrotate/logrotate.status*. The first time **logrotate** runs, it will init log file status in */var/lib/logrotate/logrotate.status*.

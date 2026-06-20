---
layout: post
title: Configure Private DNS on Debian
slug: configure-private-dns-debian
date: 2026-06-19 23:30
#lastmod: YYYY-MM-DD HH:MM
excerpt: Here is a straight forward method to configure private dns on Debian.
tags: [debian, dns]
code: true
---
Today, I installed Linux Mint Debian Edition on one of computers at home. After installation, I wanted to configure private DNS on it. However, it did not work as it was suppose to.

At first, I added my configs in `/etc/resolv.conf`. This was suppose to work after restarting, but it did not. This was because `systemctl` overrode `resolv.conf` as soon as I restarted it.

I realised that `systemd-resolved` never came pre-installed on Debian. I installed `systemd-resolved`, created `/etc/systemd/resolved.conf` with my configs, and restarted `systemd-resolved.service`.

And, that was all. 

All set up, and happy networking!

### Steps to Configure Your Private DNS on Debian

- Install systemd-resolved `sudo apt install systemd-resolved`
- Create resolved.conf `sudo touch /etc/systemd/resolved.conf`
- Add configurations
- Restart systemd-resolved `sudo systemctl restart systemd-resolved.service`

You are good to network now.

---
layout: post
title: No Input Output Audio Device Detected on Fedora
slug: no input output audio device detected
date: 2024-09-29 16:05
#lastmod: YYYY-MM-DD HH:MM
excerpt: I lost audio connection to D-bus while finding an alternate media player to Celluloid on Fedora.
image: '/images/failed-to-connect-to-bus-no-medium-found.webp'
categories: [Technology]
tags: [fedora]
---
<span class="dropcap">I</span> have been testing KDE recently. This is my [third time trying KDE]({{site.url}}/kubuntu/) to see if I could switch from Gnome to Plasma. I am running Gnome and Plasma side by side. At first, I thought the default dragon player would be enough, and I won't have to go through any problems.

## Simplicity Comes at a Cost
I was wrong. The dragon player didn't work, even though all the media codecs were available. When you [enable third party repositories](https://docs.fedoraproject.org/en-US/workstation-working-group/third-party-repos/) during the initial setup, then it is not about multimedia codecs. They are just a bunch of proprietary software that includes Skype and Spotify. So, if you do not enable the third party repositories, it won't matter, anyway.

To enable medica codecs, you must configure [rpm-fusion repositories](https://rpmfusion.org/Configuration#Command_Line_Setup_using_rpm) and install the required media codecs. You will also need to `swap ffmpeg-free` with the regular ffmpeg.

When you have finished installing the [Fedora KDE spin](https://fedoraproject.org/spins/kde/), you will find out that the dragon player doesn't play anything except some audios. In my case, I had already removed Celluloid and installed the KDE's dragon player. Not a good move, right?

## The Trial Begins
I realised that something was missing. I installed the Celluloid back, but the dragon was still not playing any videos. I went on installing and uninstalling mpv, haruna, vlc, as well as checking my media codecs. Everything was happening so fast that I didn't realise that the entire audio connection to Dbus was lost. 

Once I settled down with Haruna and played a video music file, the video was playing fine, but there was no audio. I checked the system tray and the audio icon was disabled. It was showing **no input output audio device detected** error. I ran the `systemctl` command immediately to find out what went wrong with the wireplumber.

```shell
$ systemctl --user status wireplumber.*
```
The above command returned me the `Failed to connect to bus: No medium found` status. I had ruined my audio system connection to `dbus` by now. I simply ran `dnf install` command for the `dbus` to see if I am missing any components.

```shell
$ sudo dnf install *dbus*
```
## There it was!
Above hack showed me that I somehow installed and swapped `wireplumber` with `pipewire-media-session`. I removed pipwire's jack audio connection from @System and installed the `dbus kit` from @fedora updates. After that I restarted `wireplumber.service`

```shell
$ sudo dnf remove pipewire-jack-audio-connection-kit-1.0.8-1.fc40.x86_64
$ sudo dnf install jack-audio-connection-kit-dbus-1.9.22-5.fc40.x86_64
$ sudo systemctl --user restart wireplumber.service
```
And voila! Everything came back to normal.

Now a little about the dragon player. It depends on VLC's ffmpeg plugin, as it uses a few VLC features, so it won't work unless you install `vlc-plugin-ffmpeg` on your Fedora system. I am not sure that would be the only thing you will need. 

![Celluloid media player running on Fedor KDE]({{site.url}}/images/fedora-kde-celluloid-running.webp){:loading="lazy" width="600" height="auto"}_GTK Based Celluloid Running on Fedora KDE_

I am back to using Celluloid. It's a GTK based media player, but Qt framework annihilates it very well. 

---
<small>⭐ Cover image by <a href="https://pixabay.com/users/mjh_shikder-21129657/">mjh_shikder</a> on Pixabay.</small>

---

---
layout: post
title: FreeBSD Graceful Shutdown Due to Power Loss
slug: freebsd-shutdown
date: 2025-07-01 23:01
lastmod: 2025-07-03 16:44
excerpt: BIOS has little power to override operating system settings. Therefore, BIOS cannot trigger the shutdown if ACPI is set to NONE.
#image: /assets/images/freebsd-power-off.webp
categories: [technology]
tags: [FreeBSD, unix, computers]
# sticky: true
# hidden: true
---
Since June of this year, I have been [using FreeBSD]({% post_url 2025-06-26-using-freebsd %}). As soon as I began using the
OS on my primary machine, it presented me with my first problem to solve right away. The issue was not something I expected as a Fedora user.

My computer has a buggy BIOS, and we experience power outages in my area during the summer.
In FreeBSD, `hw.acpi` doesn't care about these two factors. It always comes with some
defaults. One of them is that `hw.acpi` triggers a graceful shutdown when the user
presses the power button.

## The Outage
Yesterday, we experienced a sudden power outage. Instead of switching to battery,
FreeBSD gave me a minute to save everything and fainted before I could
hit `:q`. 

The battery was still charging, and it had 46% capacity. I was thankful that it gave me a minute to think.
I visited the [FreeBSD forums](https://forums.freebsd.org/) to find out if someone had experienced something
similar.

The most [similar question](https://forums.freebsd.org/threads/how-do-i-make-my-power-button-do-nothing-with-acpi-disabled.362/) I found on the forums was from 2008. The only common thing between me and the OP was our buggy BIOS. Now I had questions in my mind. Why would the system give me a minute before shutting down?

FreeBSD somehow couldn't read the battery level. The system software assumed that the battery level was critically low and immediately triggered the `S5` state. Why it couldn't read the battery level properly is something to investigate. For now, I needed to save the computer from a similar shutdown.

## The S5 State
I simply changed the `hw.acpi.power_button_state` to `NONE`, and voila! It just
worked. I unplugged the power cable from my laptop, and it simply switched to
battery, showing me the remaining time. The S5 state is the default suspend state in
FreeBSD. It means if the user presses the power button, FreeBSD turns off the machine nicely.
This was the reason I got a minute.

To make the change permanent across logins, I entered the following line in my
`/etc/sysctl.conf`:

{% highlight shell linenos %}
echo "hw.acpi.power_button_state=NONE" >> /etc/sysctl.conf
{% endhighlight %}

This disabled the power button, and now it does nothing when pressed. This was something I
needed anyway.

---
<small>⭐ Cover image by <a href="https://www.pexels.com/photo/usb-hub-type-c-dock-adapter-4195406/">Karolina Grabowska</a> on Site.</small>

---

---
title: "State of Droidian Week 19 2021"
date: 2021-05-11T10:25:40+02:00
draft: false
featured_image: /img/posts/2/p1.png
images:
- /img/posts/2/p1.png
---

Hey!

Although with some delay, finally it's time to post about the recent developments around Droidian!

<!--more-->

Summary
------------

* Initial camera support
* power-management and next steps
* Middleware updates
* New release, keep reading ;)


Initial camera support
--------------------------

Erfan has been hard at work to implement some basic camera support in `libaperture`.

This is still in early stages - the view is rotated and not accelerated. Still, it's an awesome sight!

<blockquote class="twitter-tweet" data-theme="dark"><p lang="en" dir="ltr">Say cheese to <a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a> camera ✌️<br>(Coming soon to repos)<br>Thanks to amazing team <a href="https://twitter.com/eugenio_g7?ref_src=twsrc%5Etfw">@eugenio_g7</a> <a href="https://twitter.com/r3vnn?ref_src=twsrc%5Etfw">@r3vnn</a> <a href="https://twitter.com/erikinkinen?ref_src=twsrc%5Etfw">@erikinkinen</a> <a href="https://t.co/UklQMfejT5">pic.twitter.com/UklQMfejT5</a></p>&mdash; Erfan Abdi ➐ (@Khode_Erfan) <a href="https://twitter.com/Khode_Erfan/status/1386580535984726017?ref_src=twsrc%5Etfw">April 26, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

You can get camera support support with a simple dist-upgrade, or by flashing the latest rootfs or a recent nightly.


Some basic power management stuff
---------------------------------------------

Eugenio has been looking at making the whole stack aware of the wakelock-centered, opportunistic sleep as commonly found in Android devices.

Some shy first steps have been made with the introduction of [`stated`](https://github.com/droidian/stated), 
The job of `stated` is to keep track of the current device state and set up wakelocks when required. It also enables `autosleep` so that the device can go into power saving mode when no wakelocks are active.  
`stated` won't replace `gnome-settings-daemon`, and it tries not to go in its way.

`stated` is pre-alpha and not ready for primetime. It is not shipped by default, but it lies in a separate feature branch. So, if you know where to look, you can install it rather easily. Otherwise, it's probably better to wait some more weeks ;)

Alongside that, he has been trying to fix/workaround some issues experienced on wake-ups, more details in this 
[pull request](https://github.com/droidian/wlroots/pull/3). And there is more to come!


Middleware updates
------------------------

As usual, Giuseppe diligently updated many middleware packages to keep in sync with our upstreams.


Download now
------------------

All of this (and more!) is now available in the latest release, bullseye/21. Get it from this [link](https://github.com/droidian-images/rootfs-api28gsi-all/releases/tag/droidian%2Fbullseye%2F21) while it’s hot!
Remember that this is **alpha quality software, absolutely not daily driver ready**. If you break your device, you get to keep both pieces!

Be sure to read the [flashing instructions](https://github.com/droidian-images/rootfs-api28gsi-all#installation-instructions).

~ The Droidian Team

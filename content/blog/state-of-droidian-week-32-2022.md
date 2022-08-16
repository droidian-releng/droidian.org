---
title: "State of Droidian - Week 32, 2022"
date: 2022-08-17T00:40:29+02:00
draft: false
featured_image: /img/posts/4/p1.jpg
images:
- /img/posts/4/p1.jpg
---

Long time no see! While we have been silent here, if you kept following the activity in GitHub and Telegram you know we have been hard at work, and we have some great news to share.

<!--more-->

## Summary

* New Debian bookworm-based snapshot
* Official support for F(x)tec Pro1-X and Sony Xperia 5
* New unified image build system
* Support for the creation of flashboot-flashable images
* Opt-in, online full disk encryption
* Android™ App support through WayDroid
* Support for devices shipped with Android 10 and 11
* External monitor support
* Flashlight
* Vibration Motor, notification LED
* Accelerated Flatpak apps
* Performance and stability fixes

## New snapshot

9 months since the last snapshot (snapshot 23, which got released but never announced here!), we are pleased to announce the release of the first bookworm-based snapshot!

Since late last year, nightlies have switched to Debian 12, `bookworm`. This release is just a point-in-time snapshot of a known good state. If you are already running Droidian bookworm there is no need to reflash.

One of the major higlights are GNOME 42, phoc 0.10.0, phosh 0.17.0 and squeekboard 1.16.0.

## New devices

F(x)tec Pro1-X and Sony Xperia 5 join the supported device roster.

## Online full disk encryption, new unified image build system, fastboot-flashable images

Eugenio has been hard at working in implementing Full Disk Encryption.

This work touched many parts of the whole stack - and one of the results is that the image build system has been refactored and allows the building of device specific, fastboot-flashable images!

Currently the following devices offer said images, and support Full Disk Encryption as well:

* F(x)tec Pro1 (qx1000)
* F(x)tec Pro1-X (qx1050)
* Sony Xperia 5 (bahamut)

Encryption in Droidian uses the usual dm-crypt/LUKS, but with some twists. Most notably, encryption happens online via the `reencrypt` LUKS2 feature. We recommend reading the whole Twitter thread for some insights:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Over the past weeks, I&#39;ve been working in adding Full Disk Encryption in <a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a>. It uses dm-crypt/LUKS, but with a twist:<br><br>(thread) <a href="https://t.co/PY8T1o72ri">pic.twitter.com/PY8T1o72ri</a></p>&mdash; Eugenio Paolantonio (@eugenio_g7) <a href="https://twitter.com/eugenio_g7/status/1543746872342466560?ref_src=twsrc%5Etfw">July 4, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


## Android™ App support

Our very own Erfan's side project, [WayDroid](https://waydro.id) has been making waves in the last months. Of course, it's available and ready to install in Droidian. By shipping WayDroid with Droidian, we hope to help bridge the gap with other mobile Operating Systems.

Provided your device is supported, you can install it using the following command on api28 ("Halium 9") images:

    sudo apt install waydroid waydroid-system-29 waydroid-vendor-28


...and on api29 ("Halium 10") images:

    sudo apt install waydroid waydroid-system-29 waydroid-vendor-29

Work is ongoing to support Halium 11 devices as well.

## Support for devices shipped with Android 10 and 11

You heard that right! Starting from snapshot 23, Droidian supports devices shipped with Android 10. Eugenio added support for Halium 10 and, while at it, refactored a bit the start-up flow shortening the average boot time.

<blockquote class="twitter-tweet"><p lang="in" dir="ltr"><a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a> x Halium 10 🎉🎉 <a href="https://t.co/keymHYhDe9">pic.twitter.com/keymHYhDe9</a></p>&mdash; Eugenio Paolantonio (@eugenio_g7) <a href="https://twitter.com/eugenio_g7/status/1419381058722729991?ref_src=twsrc%5Etfw">July 25, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

Snapshot 24 adds experimental support for Halium 11 as well:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Have been quiet lately but kept working on <a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a>! Beyond moving to bookworm, Halium 11 devices are now experimentally supported. Have fun: <a href="https://t.co/6pm3uQyxUb">https://t.co/6pm3uQyxUb</a> <a href="https://t.co/Pk7JBUyNaI">pic.twitter.com/Pk7JBUyNaI</a></p>&mdash; Eugenio Paolantonio (@eugenio_g7) <a href="https://twitter.com/eugenio_g7/status/1500822359577608195?ref_src=twsrc%5Etfw">March 7, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

Huge thanks goes to all the Halium developers and contributors!

## External monitor support

Eugenio began refactoring the wlroots hwcomposer backend. One of the side effects of this work (after fixing a couple of bugs down the stack) is that external monitors are now supported!

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">No better time than a week off work to refactor the wlroots hwcomposer backend used in <a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a> - adding external output support in the process!<a href="https://twitter.com/thefxtec?ref_src=twsrc%5Etfw">@thefxtec</a> Pro1 becomes a nice little laptop, powered by Debian 🚀 <a href="https://t.co/yjEGTDu6Nx">pic.twitter.com/yjEGTDu6Nx</a></p>&mdash; Eugenio Paolantonio (@eugenio_g7) <a href="https://twitter.com/eugenio_g7/status/1436765957939212288?ref_src=twsrc%5Etfw">September 11, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

This is an experimental feature and currently enabled only on the F(x)tec Pro1 and Sony Xperia 5 ports, where it has been tested extensively.

## Flashlight

Giuseppe implemented flashlightd, a dbus service handling camera flashlight via gstreamer and some small adaptation works on phosh. Currently only for Halium 9 devices.

## Vibration Motor, notification LED

Haptic feedback and notification LEDs support has finally been rewritten, and landed our production repositories.
Thanks to Erfan and Eugenio these features no longer depends on libhardware APIs and work directly via binder (both via HIDL and AIDL).

## Accelerated Flatpak apps

Eugenio has fixed GPU acceleration for Flatpak applications. Most GTK4 and Qt/KDE flatpaks should now go through libhybris:

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Accelerated flatpaks coming 🔜 to <a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a> ! 🚀 <a href="https://t.co/y5TI0RqLQS">pic.twitter.com/y5TI0RqLQS</a></p>&mdash; Eugenio Paolantonio (@eugenio_g7) <a href="https://twitter.com/eugenio_g7/status/1431581365712166914?ref_src=twsrc%5Etfw">August 28, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

## Download, and release notes:

You can find the release notes for snapshot 24 [here](https://github.com/droidian-images/droidian/releases/tag/droidian%2Fbookworm%2F24).

Please read the release notes carefully.

*Remember that this is alpha quality software, absolutely not daily driver ready. If you break your device, you get to keep both pieces!*

As always, the default PIN is **1234**.

You can use the following links to download this new snapshot:

* Rootfs (arm64, Halium 9): https://images.droidian.org/droidian/droidian-bookworm-24/arm64/generic/rootfs-api28.zip
* Rootfs (arm64, Halium 10): https://images.droidian.org/droidian/droidian-bookworm-24/arm64/generic/rootfs-api29.zip
* Rootfs (arm64, Halium 11): https://images.droidian.org/droidian/droidian-bookworm-24/arm64/generic/rootfs-api30.zip

### F(x)tec Pro1

* Fastboot-flashable image: https://images.droidian.org/droidian/droidian-bookworm-24/arm64/fxtec/image-fastboot-pro1.zip

Ensure the latest Android stock firmware is installed before flashing.

### F(x)tec Pro1-X

* Fastboot-flashable image: https://images.droidian.org/droidian/droidian-bookworm-24/arm64/fxtec/image-fastboot-pro1x.zip

Ensure the latest Android stock firmware is installed before flashing.

### Sony Xperia 5

* Fastboot-flashable image: https://images.droidian.org/droidian/droidian-bookworm-24/arm64/sony/image-fastboot-bahamut.zip

Ensure the latest Android stock firmware is installed before flashing.
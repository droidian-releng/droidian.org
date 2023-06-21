---
title: "State of Droidian - Week 25, 2023"
date: 2023-06-21T18:40:29+03:00
draft: false
featured_image: /img/posts/5/p1.jpg
images:
- /img/posts/5/p1.jpg
---

Hello there!

Already waiting eagerly for Droidian 13 `trixie`? We have some good news for you!

We are now releasing the final snapshot based on `bookworm` which means development will soon be moved to Debian 13 `trixie`.

Read on to see what progress has happened since the last blog post.

<!--more-->

## Summary

* [**Barry (aka FakeShell)**](https://github.com/FakeShell) has been added to the Droidian core team.
* Based on Debian 12 `bookworm`
  * GNOME 43 (except some non-essential packages)
  * phoc 0.28.0
  * phosh 0.28.0
  * squeekboard 1.22.0
* **Google Pixel 3a** and **Volla Phone** return to the official builds roster
* **Volla Phone 22** is added to the official builds roster as a new device
* A bunch of previously community supported devices were added to the official builds roster with most features now working: 
  * Oneplus 3/3T (oneplus3/oneplus3t)
  * Xiaomi Redmi 7 (onclite)
  * Xiaomi Redmi Note 7 (lavender)
  * Xiaomi Redmi 9C/9C NFC (angelica/angelican)
  * Poco M2 Pro / Xiaomi Redmi Note 9 Pro / Pro Max / 9S (miatoll)
  * Samsung Galaxy S9 (Qualcomm) (starqlte)
* A new battery management solution **batman** was included in all devices together with its GUI. It will possibly prolong the battery life by even two or three times in daily use.
* Halium 11: Enabled camera stack
* Much more stable camera stack has been worked on and added to Droidian devices that did not support camera.
* New sysfs fallback in flashlightd code. This should ensure the flashlight works on most devices out of the box.
* Image has been cleaned off from all mobile unfriendly apps.
* Fixed HW acceleration in WebKitGtk+ apps
* Fixed Flutter apps
* Fixed keyring unlock at login
* Multiple display support is now available for everyone, provided the device itself supports it
* Numerous bug fixes, improvements and cleanups through the whole stack.

## New snapshot

3 months since the last snapshot (snapshot 25, which got released but never announced here!), we are pleased to announce the release of the last bookworm-based snapshot!

This release is just a point-in-time snapshot of a known good state. If you are already running Droidian bookworm there is no need to reflash as per usual.

One of the major higlights are GNOME 43, phoc 0.28.0, phosh 0.28.0 and squeekboard 1.22.0.

## New devices

**Google Pixel 3a** and **Volla Phone** return to the official builds roster. 

Erik has also ported **Volla Phone 22** which is now in the official builds roster. Additionally, a bunch of previously community supported devices were added to the official builds roster by Barry:
* Oneplus 3/3T (oneplus3/oneplus3t)
* Xiaomi Redmi 7 (onclite)
* Xiaomi Redmi Note 7 (lavender)
* Xiaomi Redmi 9C/9C NFC (angelica/angelican)
* Poco M2 Pro / Xiaomi Redmi Note 9 Pro / Pro Max / 9S (miatoll)
* Samsung Galaxy S9 (Qualcomm) (starqlte)

## Battery-life

Barry implemented a new battery management solution called "batman". It conservers power by controlling power modes on different pieces of hardware like the CPU and even shutting down CPU cores. It won't slow you down though as it monitors if the screen is on. Batman GUI, a graphical configuration tool for batman, is also shipped with the new images.

## Camera

For devices not supporting gst-droid camera, Erik introduced a QtMultimedia plugin based on qtubuntu-camera from Ubuntu Touch. On these devices, a different camera application, droidian-camera, is included.

## Flashlight

For devices not supporting gst-droid camera and its torch functionality, Barry added support for using sysfs nodes as fallback in flashlighd.

## External monitor support

Support for external monitor has been added during snapshot 25 and it was later illustrated on Fxtec and Samsung devices. Any device with display out should be able to output to an external display on Droidian.

Currently these devices include: F(x)tec Pro1, Sony Xperia 5 and Samsung Galaxy S9. To achieve this, an HDMI to USB C adapter such as the one provided by pine64 can be used.

## Download, and release notes:

You can find the release notes and downloads for snapshot 26 [here](https://github.com/droidian-images/droidian/releases/tag/droidian%2Fbookworm%2F26).

Please read the release notes carefully.

As always, the default PIN is **1234**.

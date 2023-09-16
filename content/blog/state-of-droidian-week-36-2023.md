---
title: "State of Droidian Week 36 2023"
date: 2023-09-16T00:16:41-04:00
draft: false
featured_image: /img/posts/6/p1.jpg
images:
- /img/posts/6/p1.jpg
---

Hello Everyone!

We're thrilled to unveil our latest snapshot, proudly standing on the foundation of trixie.

Dive right in to see how we've evolved since our previous update.

<!--more-->

## Summary

* Based on Debian 13 Trixie
* GNOME 44 (except some non-essential packages)
  * phoc 0.29.0
  * phosh 0.31.0
  * squeekboard 1.22.0
* Volla Phone 22 has been temporarily removed from the builds
* The camera stack has been updated with support for smooth video recording, multi camera support, zoom, flashlight and a completely redesigned user interface.
* Support for fingerprint has been added for all devices.
* Support for automatic notch and cutout detection has been added for all devices.
* Support for NFC has been added for all devices that support NFC.
* Support for MTP has been added for all devices.
* Waydroid, NFC, MTP, fingerprint and encryption settings have all been integrated into the settings app
* Preliminary support has been added for Halium 12 (halium images, libhybris, A12 compiler, etc)
* Hardware video playback is now in working.
* Numerous bug fixes, improvements and cleanups through the whole stack.

## New snapshot

Three months post our last snapshot, we are unveiling the trixie-based release.

This isn't merely an incremental update, but a comprehensive upgrade.

One of the major higlights are GNOME 44, phoc 0.29.0, phosh 0.31.0 and squeekboard 1.22.0.

## Device changes

Volla Phone 22 has been temporarily removed from the builds

## Fingerprint

Barry implemented support for fingerprint and full integration in settings.

Current fingerprint implementation runs a daemon which can communicate with Android's biometric hal.

A client was also developed to ease the process of enrollment, finger verification and communication with logind and Phosh.

A PAM module was also developed to make integrating programs with the fingerprint sensor easier.

Fingerprint support is now available on all official devices.

## Camera

Barry added the support for pinhole (gst-droid) for all devices. Alongside this advancement, pinhole was further developed to provide a much smoother viewfinder.

Barry also further developed the newly added camera stack with support for video recording, flash, focus and devices with a multi camera setup.

The user interface was also completely redesigned UI thanks to the community member `arpio23`.

At the moment, some devices default to the newly developed stack known as `droidian-camera`, and some still use the old stack using pinhole.

## NFC

Barry added NFC support which is now included and will be available out of the box for all the devices with an NFC chip.

Support for enabling/disabling and testing NFC was also added to settings.

## MTP

Barry added support for MTP and integration in settings for switching between states, RNDIS/MTP/None to provide a smooth experience.

Live switching between states is possible with the help of a small daemon called mtp-configfs which will read the configuration modified by the settings app.

## Waydroid

Barry added a settings panel for Waydroid, this panel includes all the options required for a fast and smooth experience with Waydroid.

This panel includes support for options such as installing Waydroid, starting and stopping Waydroid, installing, removing, and launching apps, wiping Waydroid's userdata, getting info such as Waydroid's IP, vendor type and OS version as well as enabling direct access to hardware such as GPS and NFC.

## Cutout and notches

Phosh initially introduced manual tweaks for notches and cutouts. Barry's subsequent feature facilitates automatic detection by leveraging specific device data from the vendor image.

Information about device specific dimensions is read from vendor overlay also known as RRO then a file gets built including the information calculated in a way to be served to Phosh.

This feature works automatically without any user interaction.

## Halium 12

Eugenio added the required toolchain for Android 12-12.1 devices. This should let users build kernels for newer devices released with Android 12.

Later, Barry added halium images for Halium 12 into the repos.

## Hardware video playback

Erik identified and rectified an issue hindering video playback in select apps.

Tools like celluloid and clapper now use hardware video playback.

## Encryption settings

Eugenio has integrated encryption settings within the main settings app, refining the overall user interface.

## Download, and release notes:

You can find the release notes and downloads for snapshot 27 [here](https://github.com/droidian-images/droidian/releases/tag/droidian%2Ftrixie%2F27).

Please read the release notes carefully.

As always, the default PIN is **1234**.

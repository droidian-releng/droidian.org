---
title: "State of Droidian Week 16 2021"
date: 2021-04-20T10:00:51+02:00
draft: false
featured_image: /img/posts/1/p1.png
images:
- /img/posts/1/p1.png
---

Hello folks!

This post is meant to give a summary of what happened around Droidian in the recent past. We're going to post similar updates every two weeks, so mark your calendars!

<!--more-->

Summary
------------

* Erik Inkinen joined the team: Welcome!
* SMSes can now be received and sent
* Performance and battery life improvements 
* Various middleware & shell updates
* Sensors should now mostly work out-of-the-box
* Two new ports!
* All of this is available in the latest release: keep reading ;)


SMSes and modem configuration
----------------------------------------

<blockquote class="twitter-tweet" data-theme="dark"><p lang="en" dir="ltr">I received SMS from the Finnish postal office using <a href="https://twitter.com/Puri_sm?ref_src=twsrc%5Etfw">@Puri_sm</a> Chats and oFono2MM daemon on <a href="https://twitter.com/droidianlinux?ref_src=twsrc%5Etfw">@droidianlinux</a> . So, receiving SMS works now with oFono2MM. 🎉 Cc <a href="https://twitter.com/eugenio_g7?ref_src=twsrc%5Etfw">@eugenio_g7</a> <a href="https://twitter.com/r3vnn?ref_src=twsrc%5Etfw">@r3vnn</a> <a href="https://twitter.com/Khode_Erfan?ref_src=twsrc%5Etfw">@Khode_Erfan</a> <a href="https://t.co/BdXyNEdIJF">pic.twitter.com/BdXyNEdIJF</a></p>&mdash; Erik Inkinen (@erikinkinen) <a href="https://twitter.com/erikinkinen/status/1379087460295192580?ref_src=twsrc%5Etfw">April 5, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

New team entry Erik started working on a ModemManager drop-in replacement that uses oFono as its backend. It is called oFono2MM and it is our current solution to make non-ofono aware applications work. Moreover, this means that SMSes can now be sent and received, but currently it is not possible to check if sending SMS failed as status reporting in oFono2MM has not been implemented yet. 

Also, the modem can be mostly configured via the Settings application. We're now working to enable configuration of mobile data and fix a few bugs related to PIN-locked SIM cards. Currently, Chats does not always detect the SIM card getting unlocked and the modem getting online.


Performance and battery life improvements on the compositor side
---------------------------------------------------------------------------------

Eugenio's improvements to the wlroots hwcomposer backend finally landed in the production repositories!

Previously known with the *g7-experiments* moniker, these changes improve the vsync syncronization and try to avoid emitting more frame events than needed. Plus, damage tracking for GPUs supporting the `EGL_KHR_partial_update` extension (i.e. the vast majority of Android devices ;) ) has been implemented, in a slightly hacky way to avoid too invasive changes.

This allows us to achieve vsync-syncronized 60fps with at least half of the frame events as before, so both the eyes and the CPU are happy!

For the technicalities you can check out [these](https://github.com/droidian/wlroots/pull/1) [two](https://github.com/droidian/wlroots/pull/2) pull requests.

If you're curious how Droidian works with these changes, you can check out this video (phone is F(x)tec Pro¹). Keep in mind that there is no hardware acceleration involved here - GTK3 is only software accelerated. Still, it seems to work very well, and is definitely an improvement.

<blockquote class="twitter-tweet" data-theme="dark"><p lang="und" dir="ltr">👀 <a href="https://t.co/859SdKg2S4">pic.twitter.com/859SdKg2S4</a></p>&mdash; Eugenio Paolantonio (@eugenio_g7) <a href="https://twitter.com/eugenio_g7/status/1366860787629834242?ref_src=twsrc%5Etfw">March 2, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


Various middleware & shell updates
-------------------------------------------

Giuseppe upgraded a sizable amount of middleware packages to catch up with our various upstreams. In addition, he imported gnome-clocks directly from the PureOS tree - this means that alarms now work!

phosh and phoc have been updated to their latest releases (0.10.1 and 0.7.0 respectively). If you haven't kept up with the latest developments, these releases bring a bunch of stability improvements, while also introducing some new features: OSD, long swipes, (both landed in 0.9.0), shutdown/reboot dialogs and auto rotation.


Sensors
----------

The sensor stack has been improved as well and our sensors daemon (`hadess-sensorfw-proxy`) created by Erfan, is now enabled at startup as an `iio-sensor-proxy` replacement.

This, thanks to the new phosh version, finally allows us to auto-rotate the screen!


Two New Ports!
------------------

Last but not least we are pleased to welcome two new officially ported devices to our list: the Volla Phone (yggdrasil), and Google Pixel 3a (sargo), both ported by Erik!

These devices join the F(x)tec Pro¹, and the adaptation bundle for these devices can be downloaded directly from the release download page.


Download now
------------------

All of this is now available in the latest release, bullseye/20. Get it from this [link](https://github.com/droidian-images/rootfs-api28gsi-all/releases/tag/droidian%2Fbullseye%2F20) while it's hot!

Remember that this is **alpha quality software, absolutely not daily driver ready**. If you break your device, you get to keep both pieces!


![MEME](/img/posts/1/meme.jpg)

*(courtesy of @cyjan)*

Be sure to read the [flashing instructions](https://github.com/droidian-images/rootfs-api28gsi-all#installation-instructions).

Wrapping up
---------------

We're humbled and proud to see this much of interest around Droidian. See you in two weeks!

~ The Droidian Team




---
title: "State of Droidian Week 22 2021"
date: 2021-06-01T10:00:29+02:00
draft: false
featured_image: /img/posts/3/p1.png
images:
- /img/posts/3/p1.png
---

Hey!

Missing news about Droidian development? Here's what happened under the hood during the past weeks ;) 
<!--more-->


Summary
------------

* Power management stuff: part 2
* Orientation sensor on hadess-sensorfw-proxy
* phosh and phoc upgrades!
* Volla community days 2021
* Release 22, keep reading ;)


Power management stuff: part 2
---------------------------------------

Eugenio continued his work on [`stated`](https://github.com/droidian/stated). Although there is nothing really exciting to share, there have been some improvements on wakelocks handling and now `stated` can detect "sleep/resume loops" and damper them by better spacing out the next sleep cycles.

In Droidian, this means that, with opportunistic sleep enabled, the system is much more stable in some edge cases (like having an active SSH connection to the device with screen off). Previously, continuous wake-ups caused instability on the compositor side (mostly due to the expensiveness of taking/releasing input devices). Now that sleep/resume loops are detected and dampened, wake-ups from sleep mostly behave as expected.

He also fixed some other stuff throughout the stack. With the latest upgrades, the display should not wake-up anymore without user input.

Please note that the `stated` stuff is still pre-alpha, and is not included in the downladable images. It resiedes in a separate feature branch.


Orientation sensor on hadess-sensorfw
-----------------------------------------------

Erfan's [hadess-sensorfw-proxy patch](https://github.com/droidian/hadess-sensorfw-proxy/pull/3) improving orientation sensor handling has been finally merged into the production repositories. This should now fix dynamic orientation on devices with reversed display panel, highlighted on [Issue #2](https://github.com/droidian/hadess-sensorfw-proxy/issues/2) and also reported by several community members.


phosh and phoc upgrades
-------------------------------

Both phosh and phoc have been upgraded, to the latest [0.11.0](https://github.com/droidian/phosh/releases/tag/droidian%2Fbullseye%2F0.11.0-1droidian0) release and the latest [git snapshot](https://github.com/droidian/phoc/releases/tag/droidian%2Fbullseye%2F0.7.0%2Bgit20210411-1droidian0) respectively.

Most notable improviements since what was available in Droidian before is the ability to take screenshots (you should install `gnome-screenshot` first), and quick settings for the Modem/WLAN/Bluetooth switches in the top menu.


Volla Comunity Days 2021
-------------------------------
Hope you didn't miss Erik's presentation about Droidian at Volla Community Days 2021! If so, don't worry you can still find it below ;)

<iframe width="560" height="315" src="https://www.youtube.com/embed/qLaX4DcBHZA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


Download now
------------------
As always all of this is now available in the latest release, **bullseye/22**. Get it from **[this link](https://github.com/droidian-images/rootfs-api28gsi-all/releases/tag/droidian%2Fbullseye%2F22)** while it’s hot! 

*Remember that this is alpha quality software, absolutely not daily driver ready. If you break your device, you get to keep both pieces!*

~ The Droidian Team




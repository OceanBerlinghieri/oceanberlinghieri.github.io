---
layout: post
permalink: /blog/:categories/:title
title: An Intel AX200 in low power mode took 2 hours of my life
cover: /assets/images/posts/an-intel-ax-in-low-power-mode-took-2-hours-of-my-life.png
excerpt: AX200 enters in low power mode after suspend and does not return.
date: 2026-05-24T16:16:30.466Z
categories: linux
tags:
  - omarchy
  - arch
  - linux
  - wifi
  - intel
---
This is a simple story — no technical knowledge required, just proofreading. The thing is, I spent two years on Windows due to easier gaming setup. Why did I return to Linux? Didn't need gaming setup anymore and, in one word, desperation. Two-minute boot times, unnecessary Microsoft apps, updates that feel like downgrades — I'd had enough (again). It may not be the best substitute for its default app installation, but I decided to install Omarchy.

Everything was great — quick, keyboard-driven, built with developers in mind. I decided to suspend my PC since I'd be back in a few hours. Next day, WiFi was gone, and the research began.

First thing was basic: `ip link` — my WiFi card was nowhere to be found, only the RJ45 input was recognized. Was my device even recognized in the first place? Yes — `lspci` returned `Network controller: Intel Corporation Wi-Fi 6 AX200`, so it had to be a firmware problem. Needed to confirm, and confirmed it: error -110, firmware was not loading correctly.

``` shell
> sudo dmesg | grep -i "iwl".
	probe with driver iwlwifi failed with error -110
```

Could it be a Linux regression that broke the firmware? Checked by installing other kernels — no solution. Could it be fixed through a BIOS option to disable low power mode, as suggested in some AX200 threads? No such option on my laptop's BIOS. Could it be possible to do the same from the Linux bootloader instead? Didn't work either.

Finally, I just restored the system from a previous snapshot and — boom! Problem solved. All it was: an AX200 stuck in a low power state that, somehow, a snapshot rollback managed to fix. Obviously I don't want this happening again, so I added these configs for `iwl` and system boot:
- `pcie_aspm=off` → disables aggressive PCIe sleep states (common AX200 breakage source)
- `power_save=0` → stops WiFi from entering low-power mode
- `d0i3_disable=1` → prevents deep device sleep (very important for resume bugs)
- `uapsd_disable=1` → avoids power-save QoS issues

Anyways, I am not suspending my laptop anymore.

Some references:

[Reddit post] (https://www.reddit.com/r/openSUSE/comments/thrptr/issues_with_intel_ax200_after_suspend/)

[Arch linux forum](https://bbs.archlinux.org/viewtopic.php?id=261205)

[Github bazzite issue](https://github.com/ublue-os/bazzite/issues/4178)
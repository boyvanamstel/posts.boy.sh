---
layout: post
title: "Fix Windows 10 2004 update Blue Screen on Corsair ONE"
date: 2020-06-10
tags: [windows]
description: "Update Corsair Link to resolve the blue screen you get while updating."
apps: [pipvid]
---

TL;DR: Install [the latest version of Corsair Link](CORSAIR LINK 4.4.4.9 for CORSAIR ONE (2017/2018)) to fix the issue.

Microsoft recently released the 2004 version update for Windows 10. It includes a bunch of cool new features, like [WSL 2](https://docs.microsoft.com/en-us/windows/wsl/compare-versions) which integrates Linux even better into the Windows operating system.

I immediately jumped at the opportunity to install the update when it presented itself, only to be disappointed during the installation. It repeatedly failed with a BSOD mentioning `cpuz141_x64.sys` caused a `PAGE_FAULT_IN_NONPAGED_AREA`.

At first I was confused, because I wasn't aware a CPU-Z driver was installed at all. After some digging I discovered it's used by the [Corsair Link](https://www.corsair.com/eu/en/corsairlink) utility installed on all 2017/2018 [Corsair ONE](https://www.corsair.com/eu/en/Categories/Products/Systems/CORSAIR-ONE/CORSAIR-ONE-GAMING-PC/p/CS-9020003-EU) models.

Corsair Link is mandatory as it's solely responsible for updating the fan speeds while the system is in use.  Without it the computer will overheat. A terrible depedency I wasn't fully aware of when I bought the machine.

![A picture of the Corsair ONE with its components visible](/assets/blog/blog_CORSAIR-ONE-ELITE-PRO-PLUS-Content-3.jpg)

It's pretty though and fast.

The in-app update mechanism for Corsair Link promised me I was running the latest version. That was concerning. It suggested I might not be able to install the 2004 update at all. Luckily I came across this topic on the Corsair forum: [CORSAIR LINK 4.4.4.9 for CORSAIR ONE (2017/2018)](https://forum.corsair.com/v3/showthread.php?t=175259). Posted in 2018 it provides a download link to an updated version of Corsair Link. Why this version isn't available through the in-app updater is unknown to me.

After installing the newer version, Windows continued the OS update without a hitch. 🥳

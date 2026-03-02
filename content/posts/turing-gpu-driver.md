---
date: '2025-07-04T00:00:00Z'
draft: false
layout: 'post'
title: Power Management and driver issues for mobile Turing GPUs on Linux
---

## Description

Power management is broken (simply not implemented by Nvidia) on mobile Turing-based GPUs in both the nvidia proprietary drivers and nvidia-open drivers.
Battery life is better with Noveau + NVK + GSP karg. Performance is better with nvidia-open, but then battery life is terrible because the GPU never goes into a power down / sleep state.

You can use this command to monitor the current power state of the GPU: 
`watch --interval 0.1 cat /sys/bus/pci/devices/0000:00:01.0/power_state`

## Switching Drivers
This setup is specific to [secureblue](https://secureblue.dev), which I use. The kernel arguments and drivers used will apply to other systems, but are not as easy to switch between. Refer to secureblue documentation for the list of Nvidia kargs.

### Nvidia-open to Noveau + NVK + GSP karg 
1. `ujust remove-kargs-nvidia` (do not reboot afterwards)
2. `rpm-ostree kargs --append=nouveau.config=NvGspRm=1` (do not reboot afterwards)
3. Rebase to `main` image

### The prior setup back to nvidia-open
1. `rpm-ostree kargs --delete=nouveau.config=NvGspRm=1` (do not reboot afterwards)
2. `ujust set-kargs-nvidia` (do not reboot afterwards)
3. Rebase to `nvidia-open` image

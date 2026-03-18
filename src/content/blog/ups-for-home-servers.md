---
title: "UPS for Home Servers"
date: 2023-08-22
categories: ["Self-Hosting"]
description: "Why you should get a UPS for your home server — learned the hard way"
---

A power outage taught me an important lesson about home server management.

## What Happened

I was running a home server for various self-hosted services when an unexpected power outage hit. When the power came back, the server wouldn't boot properly. The abrupt shutdown had corrupted both **GRUB** (the bootloader) and **fstab** (the filesystem table).

This meant:

- The bootloader couldn't find the operating system
- Even after fixing GRUB, the filesystem mounts were broken
- I had to manually repair the configurations from a live USB

It took hours of troubleshooting to get everything back up and running. Some services needed their configurations restored from backups.

## The Lesson

After that experience, the lesson was clear: **get a UPS (Uninterruptible Power Supply)** for any home server setup. A UPS provides:

- **Battery backup** during power outages, giving your server time to shut down gracefully
- **Power conditioning** to protect against voltage spikes and surges
- **Peace of mind** knowing your data and configurations are safe from sudden power loss

If you're running any kind of home server — whether it's for media, development, or self-hosted services — a UPS is not optional. It's essential infrastructure. Don't learn this lesson the hard way like I did.

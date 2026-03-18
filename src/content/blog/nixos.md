---
title: "NixOS"
date: 2023-08-20
categories: ["Operating Systems"]
description: "Exploring NixOS and its declarative approach to system configuration"
---

NixOS is a Linux distribution built on top of the Nix package manager. What makes it unique is its **declarative approach** to system configuration — your entire system is defined in a single configuration file.

## Declarative Configuration

Instead of imperatively installing packages and tweaking config files scattered across the filesystem, NixOS lets you describe your desired system state in `configuration.nix`. The system then builds itself to match that description.

```nix
{ config, pkgs, ... }:

{
  # System packages
  environment.systemPackages = with pkgs; [
    vim
    git
    firefox
    htop
  ];

  # Enable SSH
  services.openssh.enable = true;

  # Firewall
  networking.firewall.allowedTCPPorts = [ 22 80 443 ];

  # User account
  users.users.abdulrahman = {
    isNormalUser = true;
    extraGroups = [ "wheel" "docker" ];
  };
}
```

## Atomic Upgrades and Rollbacks

Every time you rebuild your system with `nixos-rebuild switch`, NixOS creates a new **generation**. If something breaks, you can roll back to any previous generation — even from the boot menu. This makes system updates virtually risk-free.

## Generations

Generations are snapshots of your system configuration. You can list them, switch between them, and delete old ones. This is incredibly powerful for experimentation — try something out, and if it doesn't work, just roll back.

## Nix Flakes

Flakes are an experimental feature that brings reproducibility and composability to Nix. They allow you to:

- Lock dependencies to specific versions
- Share and reuse configurations easily
- Create reproducible development environments

Flakes are still evolving, but they represent the future direction of the Nix ecosystem.

## Why NixOS?

For someone interested in self-hosting and home labs, NixOS is a game-changer. Being able to version-control your entire system configuration, reproduce it on any machine, and roll back if something goes wrong is incredibly valuable. It has a steep learning curve, but the payoff is worth it.

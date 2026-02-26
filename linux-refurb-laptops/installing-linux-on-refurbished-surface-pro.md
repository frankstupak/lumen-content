---
title: "Installing Linux on a Refurbished Surface Pro: Complete 2025 Guide"
keyword: "linux on surface pro"
niche: "linux-refurb-laptops"
date: "2026-02-26"
status: published
model: "seeded"
---

# Installing Linux on a Refurbished Surface Pro: Complete 2025 Guide

Buying a refurbished Surface Pro and running Linux on it is one of the best deals in portable computing. Microsoft's premium hardware — PixelSense display, fanless design, excellent build quality — at liquidation prices, running a free OS. Here's how to do it right.

## Why Linux on a Refurbished Surface Pro?

The economics are compelling. A Surface Pro 5 with 8GB RAM and 256GB SSD costs $150-250 on eBay. Put Pop!_OS or NixOS on it, and you have a machine that handles development, writing, and light server workloads with no licensing costs and excellent battery optimization.

The linux-surface project has made Surface hardware support genuinely good:
- Touchscreen: works (iptsd daemon)
- Type Cover keyboard: works
- WiFi: works (Surface Pro 4+)
- Battery management: works with surface kernel
- Pen input: works
- Cameras: partially supported

## Which Surface Pro Models Work Best with Linux?

| Model | Linux Support | Value Score | Recommendation |
|-------|--------------|-------------|----------------|
| Surface Pro 4 (2015) | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | Best value buy |
| Surface Pro 5 (2017) | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | Great mid-range |
| Surface Pro 6 (2018) | ⭐⭐⭐⭐ | ⭐⭐⭐ | Good, pricier |
| Surface Pro 7 (2019) | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | Best performance |
| Surface Pro 7+ (2021) | ⭐⭐⭐⭐⭐ | ⭐⭐ | Premium option |

For a pure Linux daily driver, the Surface Pro 4 or 5 with an i5/8GB is the sweet spot.

## Step 1: Get the Hardware

**Budget build ($100-150):**
Surface Pro 4, Core i5, 8GB RAM, 128GB SSD

**[Check current Surface Pro 4 prices on eBay →](https://www.ebay.com/sch/i.html?_nkw=surface+pro+4+i5+8gb)**

**Mid-range ($180-250):**
Surface Pro 5, Core i5, 8GB RAM, 256GB SSD

**[Browse Surface Pro 5 listings →](https://www.ebay.com/sch/i.html?_nkw=surface+pro+5+i5+8gb)**

## Step 2: Choose Your Linux Distribution

### Pop!_OS (Recommended for Beginners)
System76's distro has the best out-of-box hardware compatibility. NVIDIA support is built in, and the COSMIC desktop is excellent on high-DPI displays. Install the linux-surface kernel via their repo after installation.

**[Download Pop!_OS →](https://pop.system76.com/)**

### Ubuntu 22.04 LTS
The most documented option. Massive community support. Add the linux-surface PPA after installation.

### NixOS (Advanced)
Declarative configuration makes Surface setup reproducible. The nixos-hardware repository includes a dedicated Surface Pro module:

```nix
imports = [
  inputs.nixos-hardware.nixosModules.microsoft-surface-pro-intel
];
hardware.microsoft-surface.kernelVersion = "stable";
```

**[Download NixOS →](https://nixos.org/download)**

## Step 3: Install the linux-surface Kernel

This step is critical for touchscreen, Type Cover, and battery management.

### On Ubuntu/Pop!_OS:
```bash
# Add signing key
wget -qO - https://raw.githubusercontent.com/linux-surface/linux-surface/master/pkg/keys/surface.asc \
  | gpg --dearmor | sudo dd of=/etc/apt/trusted.gpg.d/linux-surface.gpg

# Add repository
echo "deb [arch=amd64] https://pkg.surfacelinux.com/debian release main" \
  | sudo tee /etc/apt/sources.list.d/linux-surface.list

sudo apt update
sudo apt install linux-image-surface linux-headers-surface iptsd libwacom-surface
sudo systemctl enable iptsd
sudo update-grub
```

Reboot into the linux-surface kernel. Touch and Type Cover should work immediately.

## Step 4: Display Scaling

The Surface's high-DPI display needs scaling configured:

```bash
# GNOME
gsettings set org.gnome.desktop.interface scaling-factor 2
gsettings set org.gnome.desktop.interface text-scaling-factor 1.0

# i3/sway - add to config
output eDP-1 scale 2
```

## Step 5: Power Optimization

Surface Pro hardware benefits heavily from power tuning:

```bash
sudo apt install powertop tlp
sudo powertop --auto-tune
sudo systemctl enable tlp
```

For the Surface Pro 7/7+ with the performance dock, configure TDP unlocking via the intel-rapl interface for maximum performance.

[RELATED: Unlocking Surface Pro 7+ TDP for Maximum Performance on Linux]

## Essential Software for Surface Linux

**iptsd** — Touchscreen daemon, required for touch to work  
**libwacom-surface** — Improves pen pressure sensitivity  
**surface-control** — Battery limit and TDP control (requires linux-surface kernel)

## Common Fixes

### WiFi Not Working After Suspend
```bash
echo "options iwlwifi power_save=0" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

### Screen Too Dim
Brightness controls may need the surface kernel. With the right kernel, `brightnessctl` works natively.

### Type Cover Lag After Boot
The surface_aggregator module sometimes needs a few seconds to initialize. If the cover isn't responding, wait 10 seconds or detach/reattach.

## Accessories for Linux Surface Users

**USB-C hub** — The Surface Pro 4/5 lacks USB-C natively. A USB 3.0 hub expands connectivity.

**[Browse USB hubs compatible with Surface →](https://www.amazon.com/s?k=usb+hub+surface+pro)**

**Surface Dock** — The 1661 dock adds Ethernet, 4x USB 3.0, and 2x MiniDP for $30-50.

**[Find Surface Docks on eBay →](https://www.ebay.com/sch/i.html?_nkw=surface+dock+1661)**

## Final Thoughts

A refurbished Surface Pro running Linux is a genuinely excellent machine for developers, students, and anyone who wants premium build quality without the Microsoft tax. The linux-surface kernel makes hardware support solid, and the touch/pen experience is a bonus most Linux laptops don't offer.

Start with a Surface Pro 4 or 5 to minimize cost and risk, add the linux-surface kernel, and you'll have a machine that'll serve you well for years.

**[Shop refurbished Surface Pro laptops on eBay →](https://www.ebay.com/sch/i.html?_nkw=surface+pro+refurbished+linux)**

---
*This guide may contain affiliate links. We earn a small commission on qualifying purchases.*

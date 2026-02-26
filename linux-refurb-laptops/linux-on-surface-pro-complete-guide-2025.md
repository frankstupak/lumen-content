---
title: "Linux on Surface Pro: The Complete Setup Guide (2025)"
slug: linux-on-surface-pro-complete-guide-2025
date: 2025-02-26
status: draft
niche: linux-refurb-laptops
keywords: ["linux on surface pro", "nixos surface pro", "popos surface pro", "linux surface pro 4 5 7"]
affiliate_opportunities: ["Amazon - Surface hardware", "iFixit toolkit", "Anker USB-C hubs"]
---

# Linux on Surface Pro: The Complete Setup Guide (2025)

Running Linux on a Surface Pro used to require fighting the hardware at every step. In 2025, it's genuinely excellent — better in many ways than Windows on the same device. This guide covers everything: which models work best, how to install, what still doesn't work, and whether it's worth doing.

---

## Why Linux on Surface Pro Makes Sense in 2025

Three things converged to make this a serious option:

**1. The linux-surface project matured.** The [linux-surface kernel](https://github.com/linux-surface/linux-surface) now provides working drivers for touch (iptsd), Type Cover, WiFi (Marvell/Killer), Surface Pen, battery/charging, and the Surface Aggregator Module that controls fans and power states. What required hours of patching in 2019 is now a single kernel install.

**2. Microsoft dropped Windows 11 support for 7th Gen and older.** Surface Pro 4, 5, and 6 are officially unsupported for Windows 11 updates. Linux gives these machines a supported, secure OS indefinitely.

**3. Refurbished Surface hardware is cheap.** An SP5 i5/8GB running NixOS is a $250 machine that performs like a $600 laptop for Linux workloads. The value proposition is real.

---

## Which Surface Pro Models Work Best on Linux

### Surface Pro 7 (2019) — Best Linux Experience
The SP7 is the current sweet spot. Full USB-C support, 10th Gen Intel (good driver support), and the linux-surface kernel handles everything. If you're buying specifically for Linux and can spend $350–$450, the SP7 is the one.

### Surface Pro 5 (2017) — Best Value
The SP5 has excellent linux-surface support. Touch, Type Cover, WiFi, pen — all work. The i5-7300U handles real workloads well. At $220–$320 for a refurbished unit, this is the best dollar-per-performance Linux Surface.

### Surface Pro 4 (2015) — Works, With Caveats
SP4 has good linux-surface support but the thermal issues (see our [SP4 buyers guide](/surface-pro-refurb/surface-pro-4-refurbished-buyers-guide-2025/)) make performance inconsistent without proper thermal repaste. A reseated SP4 on Linux runs very well. An untreated one throttles.

### Surface Pro 6 (2018) — Avoid for Linux
The SP6 has quirks with the Type Cover on some kernel versions and offers no advantage over the SP5 at typically higher prices. The linux-surface team prioritizes SP5 and SP7.

---

## Choosing Your Linux Distribution

### NixOS (Advanced, Best Long-Term)
NixOS is the most powerful option for Surface hardware. The nixos-hardware repository includes a dedicated Surface module that configures the linux-surface kernel, iptsd, and power management automatically. Declarative configuration means your entire system setup is reproducible and version-controlled.

```nix
# In your flake.nix inputs:
nixos-hardware.url = "github:NixOS/nixos-hardware/master";

# In your configuration:
imports = [ 
  nixos-hardware.nixosModules.microsoft-surface-pro-intel
];
hardware.microsoft-surface.kernelVersion = "stable";
```

NixOS gives you atomic updates (roll back if something breaks), the best power management of any distro on Surface hardware, and a system you can reproduce exactly on any machine.

**Best for:** Developers, sysadmins, anyone comfortable with config files.

### Pop!_OS (Easiest, Best for Beginners)
Pop!_OS from System76 has the best out-of-box hardware support of any Ubuntu-based distro. The linux-surface kernel installs via their official package repository in minutes.

```bash
# Add linux-surface repo
wget -qO - https://raw.githubusercontent.com/linux-surface/linux-surface/master/pkg/keys/surface.asc \
  | sudo gpg --dearmor | sudo dd of=/etc/apt/trusted.gpg.d/linux-surface.gpg
echo "deb [arch=amd64] https://pkg.linux-surface.io/packages/ noble main" \
  | sudo tee /etc/apt/sources.list.d/linux-surface.list

# Install
sudo apt update && sudo apt install linux-image-surface linux-headers-surface iptsd
```

Pop!_OS also includes System76's excellent power management tools which work well on Surface hardware for battery optimization.

**Best for:** Anyone switching from Windows who wants things to just work.

### Ubuntu 24.04 LTS
If you're already comfortable with Ubuntu, 24.04 LTS + linux-surface kernel is a solid choice. The same repository commands above work identically. Ubuntu's LTS support through 2029 means you're covered.

---

## Installation: Step by Step

### Prerequisites
- USB drive (8GB+)
- Your chosen distro ISO
- Backup of anything on the Surface (installation wipes the drive)

### UEFI Setup
Before booting from USB, you need to disable Secure Boot:

1. Hold Volume Up while pressing Power to enter UEFI
2. Navigate to Security → Secure Boot → Disabled
3. Save and exit

Surface UEFI is locked down but Secure Boot can always be toggled here.

### Boot from USB
1. Hold Volume Down while pressing Power
2. Select your USB drive from the boot menu

Installation from here is standard for your chosen distro. For NixOS, follow the [NixOS installation manual](https://nixos.org/manual/nixos/stable/) — the only Surface-specific step is adding the nixos-hardware module after installation.

### Post-Install: linux-surface Kernel

**For Ubuntu/Pop!_OS:** Run the repo commands above, then `sudo update-grub && sudo reboot`. After reboot, `uname -r` should show `surface` in the kernel version string.

**For NixOS:** Add the nixos-hardware module to your configuration, run `sudo nixos-rebuild switch`, and the correct kernel installs automatically.

### iptsd: Touch Configuration

iptsd is the touchscreen daemon that makes Surface touch work properly on Linux. It handles palm rejection, stylus input, and multi-touch gestures.

On NixOS: `services.iptsd.enable = true;` — done.
On Ubuntu/Pop!_OS: It installs with the linux-surface packages and starts automatically.

If touch is jittery or palm rejection is poor, iptsd has a configuration file at `/etc/iptsd.conf` where you can tune sensitivity.

---

## What Works, What Doesn't

### Works Perfectly
- WiFi (Marvell 88W8897 on SP4/5, Killer 1535 on SP7)
- Bluetooth
- Type Cover keyboard and trackpad (including gestures)
- USB-A port
- Mini DisplayPort (SP4/5) / USB-C display output (SP7)
- Surface Pen pressure sensitivity
- Front and rear cameras (via libcamera on recent kernels)
- Battery status, charging
- Suspend/resume (mostly — see below)

### Works With Configuration
- **HiDPI scaling:** Set your compositor scaling to 200% for the 2736x1824 display. GNOME and KDE handle this well. Some older GTK apps need `GDK_SCALE=2`.
- **Screen rotation:** Works via `xrandr --output eDP-1 --rotate left` or your compositor's display settings.
- **Power management:** Install `auto-cpufreq` or use the NixOS power options for best battery life.

### Partially Working
- **Suspend/resume:** Usually works but occasionally wakes up with a black screen requiring a keyboard shortcut to restore display. A known issue with i915 drivers and Surface firmware.
- **Thunderbolt 3 (SP7 i7):** External displays work. Hot-plug is unreliable. For permanent desk setups, fine.

### Doesn't Work
- **LTE modem (SP5 LTE model):** The LTE modem in the 1807 model has no Linux driver. WiFi still works normally.
- **Windows Hello facial recognition:** Requires the IR camera driver which isn't in linux-surface yet.
- **Surface Dial:** No Linux support.

---

## Performance Reality Check

On an SP5 i5-7300U running NixOS:

| Task | Performance |
|------|-------------|
| Boot to desktop | 8–10 seconds |
| Browser (10 tabs) | Smooth, ~2GB RAM |
| VS Code with project | Smooth, no lag |
| Compile medium project | Fine, CPU stays under 80°C |
| 4K YouTube (hardware decode) | Smooth via VA-API |
| Video editing (Kdenlive, 1080p) | Workable but not fast |

The SP5 on Linux outperforms the SP5 on Windows for development workloads, primarily because there's no background telemetry, no Defender scanning, and no forced update activity stealing CPU/disk during work.

---

## Battery Life Tips

The Surface Pro's battery is one area where Linux needs tuning to match Windows:

**Install auto-cpufreq:**
```bash
# Snap install (Ubuntu/Pop!_OS)
sudo snap install auto-cpufreq
sudo auto-cpufreq --install
```

**Disable bluetooth when not in use:** `sudo rfkill block bluetooth`

**Use powertop to identify wakeup sources:** `sudo powertop` shows which processes and devices are preventing deep C-states.

With proper tuning, SP5 i5 gets 5–7 hours of mixed use. Without tuning, expect 3–4.

---

## Is It Worth It?

If you're buying a refurbished Surface Pro specifically to run Linux, yes — without reservation. You get genuinely premium hardware (PixelSense display, excellent keyboard, compact form factor) running a fully supported modern OS, for $200–$350.

If you're already using a Surface Pro on Windows and considering switching, it depends on what you need Windows for. If the answer is "Office, browser, and maybe some coding," Linux handles all of that and does it faster on the same hardware.

The Surface Pro is one of the best Linux laptops you can buy for under $400. That's not a caveat — it's the actual situation in 2025.

---

*See also: [Refurbished Surface Pro 5: The 2025 Buyers Guide →](/surface-pro-refurb/surface-pro-5-refurbished-guide-2025/)*

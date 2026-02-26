---
title: "Surface Pro 5 (2017) Refurbished in 2025: The Honest Review"
slug: surface-pro-5-refurbished-guide-2025
date: 2025-02-26
status: draft
niche: surface-pro-refurb
keywords: ["refurbished surface pro 5", "surface pro 2017 review", "surface pro 1796 specs", "surface pro 5 vs 4"]
affiliate_opportunities: ["Amazon Renewed", "iFixit", "eBay Partner Network"]
---

# Surface Pro 5 (2017) Refurbished in 2025: The Honest Review

The Surface Pro 5 — officially called just "Surface Pro" by Microsoft, model 1796 — was released in 2017 and is still one of the most sought-after refurbished devices on the market in 2025. It fixed most of the Surface Pro 4's worst problems, added LTE options, and introduced a fanless design on the m3 and i5 models that actually works.

But it's not perfect. Here's the real picture from someone who handles these at scale.

---

## SP5 vs SP4: What Actually Changed

The Surface Pro 5 wasn't a revolutionary upgrade from the 4, but the improvements it made were in exactly the right places.

**Better thermal management:** Microsoft redesigned the thermal system. The i5-7300U model is semi-fanless — it runs passively most of the time and only spins the fan under heavy sustained load. The m3-7Y30 is completely fanless. Both run significantly cooler than the SP4's i5-6300U under identical workloads.

**USB-C / Thunderbolt 3 (i7 only):** The i7-7660U model added a full Thunderbolt 3 port. This is a big deal — it enables 4K external displays, 40Gbps storage, and future-proof connectivity the SP4 never had.

**Better display:** The SP5 bumped to a 12.3-inch PixelSense display at 2736x1824 (267 PPI), slightly improved from the SP4's already excellent screen. Outdoor visibility is better.

**LTE option:** Some SP5 configurations shipped with an LTE modem (model 1807). These are rare on the used market but genuinely useful — a built-in SIM beats carrying a hotspot.

**What didn't change:** Same Surface Connect charging port (your SP4 charger works). Same Type Cover connector (SP4 keyboards work on SP5). Same single USB-A port situation.

---

## Specs Guide: What to Buy in 2025

### Tier 1: Best Value
**i5-7300U / 8GB / 256GB — $220–$320 refurbished**

This is the one to buy. The i5-7300U is fast enough for everything short of video editing, 8GB is workable for modern workflows, and the semi-fanless design means it stays quiet. The thermal issues that plagued the SP4 are largely absent here — we've tested dozens of these and rarely see the throttling problems that were endemic on SP4 i5 units.

### Tier 2: Power User
**i7-7660U / 16GB / 512GB — $300–$450 refurbished**

The Thunderbolt 3 port alone justifies the premium if you use external displays or fast storage. The i7-7660U has Intel Iris Plus 640 graphics (vs 620 on i5) which makes a meaningful difference for light creative work. Battery life takes a hit compared to i5 — expect 3–5 hours vs 5–7.

### Tier 3: Budget
**m3-7Y30 / 4GB / 128GB — $120–$180 refurbished**

The m3 runs completely silent and cool forever. It's genuinely pleasant hardware. But 4GB of RAM in 2025 is a hard limit. If you only need a browser, light Office work, and email — it's fine. For anything else, skip it.

---

## The Remaining Issues (Be Honest About These)

### Battery Degradation

SP5 units are 7–8 years old. Even with careful use, most batteries have degraded to 60–80% of original capacity. Original capacity was ~45Wh, so a unit at 70% health gives you about 31Wh effective — which means 4–5 hours of real use instead of the claimed 13.5 hours.

**What to ask:** Request the battery health percentage. On Windows, `powercfg /batteryreport` gives the full picture. On Linux, `upower -i /org/freedesktop/UPower/devices/battery_BAT0` shows current vs original capacity. Below 70% health, factor in a $50–$80 battery replacement.

### Windows 11 Support Ends in October 2025

Microsoft officially ended Windows 11 support for 7th Gen Intel processors. This matters if you're running Windows — after October 2025, you won't receive security updates through normal channels.

**The fix:** Linux. The SP5 runs Linux excellently. Pop!_OS, Ubuntu, and NixOS with the linux-surface kernel give you full driver support and a machine that will receive security updates indefinitely. This is actually one of the strongest arguments for buying a refurbished SP5 right now — you get premium hardware for $250 that runs a modern, fully-supported OS.

Alternatively, Windows 10 remains supported until October 2025, and there are unofficial upgrade paths to Windows 11 for unsupported hardware if you need Windows specifically.

### Type Cover Wear

Many used Type Covers show fabric wear on the palm rest and key legends fading. This is cosmetic but annoying. If the listing doesn't include a Type Cover, budget $30–$60 for a used one. SP4, SP5, SP6, and SP7 covers all share the same connector — buy whichever is cheapest.

---

## SP5 on Linux: Better Than SP4

The SP5's improved thermal management makes it a better Linux machine than the SP4. Under NixOS with the linux-surface kernel:

- **No throttling** under sustained workloads on i5 models
- **Full touch support** via iptsd (the linux-surface touch daemon)
- **Type Cover trackpad** works perfectly including gestures
- **WiFi** (Marvell 88W8897) works out of the box with linux-surface kernel
- **Pen pressure** works in Krita, Xournal++

The i7 Thunderbolt 3 port has partial Linux support — external displays work, but Thunderbolt hot-plug can be unreliable depending on the dock. For permanent desk setups it's fine.

---

## Where to Find Them

**eBay** has the best selection. Search "Surface Pro 1796" (the model number is more precise than "Surface Pro 5" since Microsoft dropped the number). Filter by "sold" listings first to understand actual market prices before buying.

**Amazon Renewed** has fewer options but better buyer protection. The 90-day Renewed Guarantee is useful for a device this age.

**Corporate liquidation lots** are the hidden gem. Companies replacing their fleet sell SP5 units in batches — often untested, often dusty, but usually with very low battery cycles since enterprise devices get plugged in constantly. If you're comfortable with the risk, watching eBay for "surface pro lot" or "surface pro 1796 lot" can get you units at $80–$120 each.

---

## The Upgrade Decision: SP4 vs SP5 vs SP7

If you're deciding between models, here's the honest answer:

**Buy SP4 if:** Budget is tight (under $200) and you're willing to verify thermals and accept the Windows 11 support situation. Running Linux eliminates most concerns.

**Buy SP5 if:** You want the best balance of value, reliability, and longevity. The thermal improvements are real. $250–$320 for a properly refurbished i5/8GB SP5 is the best value in the Surface lineup right now.

**Buy SP7 if:** You need USB-C natively (built in, not via adapter), want 10th Gen Intel performance, and can stretch to $350–$500. The SP7 has a fundamentally better architecture.

**Skip SP6:** The SP6 (2018) used the same 8th Gen Intel platform as the SP5 but without USB-C. It's harder to find, similarly priced to SP7, and offers no meaningful advantage over SP5 for most users.

---

## Final Recommendation

The refurbished Surface Pro 5 is the best value in the Surface lineup for 2025. It fixes the SP4's worst problems, is cheap enough to justify as a secondary or experimental machine, and runs modern Linux beautifully. For developers, students, or anyone who needs a portable productivity machine without paying new prices, the i5/8GB SP5 at $250–$320 from a seller who's done their homework is a genuinely excellent purchase.

Just check the battery, verify the thermals, and seriously consider running Linux.

---

*Related: [Should You Install Linux on a Refurbished Surface Pro? Complete Guide →](/linux-refurb-laptops/linux-on-surface-pro-complete-guide/)*

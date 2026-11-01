<div align="center">

# ComparIoT V3

<img src="hardware/images/board.webp" alt="Compatriot badge, top view" width="460">

**The Compatriot hardware security badge** — pre-built firmware, full hardware
reference, and player guides for every challenge.

[![Firmware](https://img.shields.io/badge/firmware-ESP32--C6-00897B)](firmware)
[![Challenges](https://img.shields.io/badge/challenges-17-success)](challenges)
[![Points](https://img.shields.io/badge/points-2775-success)](challenges)
[![Target](https://img.shields.io/badge/target-STM32F103C8-blue)](hardware)
[![Guides](https://img.shields.io/badge/full%20guides-Wired%20Village-orange)](https://gautham-sai05.github.io/wired_village/)

</div>

---

No firmware source here, just what you need to flash a badge, know what's on it,
and solve the challenges. Full write-ups, connection diagrams, and a browsable
site live at **[Wired Village](https://gautham-sai05.github.io/wired_village/)**.

## Contents

- [What's in this repo](#whats-in-this-repo)
- [Quick start](#quick-start)
- [The badge](#the-badge)
- [Categories](#categories)
- [Repository structure](#repository-structure)
- [Links](#links)

## What's in this repo

| Folder | Contents |
|--------|----------|
| [`firmware/`](firmware) | Pre-built binaries + a one-command flash script |
| [`hardware/`](hardware) | Board photos, full schematic, 3D render, BOM, pin maps |
| [`challenges/`](challenges) | Player guides for all 17 challenges (Automotive / Embedded / Wireless) |

## Quick start

1. **Flash the badge**
   ```bash
   cd firmware
   ./flash.sh /dev/ttyACM0
   ```
2. **Connect a serial terminal** at **115200 8N1** to see the badge's own console.
3. **Open [`challenges/`](challenges)** and start solving. The badge screen itself
   also shows each challenge's objective and wiring.

## The badge

| | |
|---|---|
| **MCU** | ESP32-C6-WROOM-1 (RISC-V), 4 MB flash |
| **Secondary target** | STM32F103C8T6, SWD-debuggable over header H3 |
| **Network** | W5500 Ethernet module, speaks `cannelloni` (CAN-over-UDP) for Automotive; onboard BLE + WiFi for Wireless |
| **Display** | 320×240 LCD, 5-button navigation |
| **Challenges** | 3 categories, 17 challenges, 2775 total points |

See [`hardware/README.md`](hardware/README.md) for the full pin map, schematics, 3D
render and bill of materials.

## Categories

| Category | Challenges | Points | Guide |
|----------|:---:|:---:|-------|
| 🚗 Automotive — CAN bus + UDS over Ethernet | 5 | 1150 | [`challenges/automotive.md`](challenges/automotive.md) |
| 🔌 Embedded — hardware peripherals | 7 | 825 | [`challenges/embedded.md`](challenges/embedded.md) |
| 📡 Wireless — BLE / WiFi | 5 | 800 | [`challenges/wireless.md`](challenges/wireless.md) |

## Repository structure

```
ComparIoT_V3/
├── firmware/              pre-built binaries, ready to flash
│   ├── compatriot_merged.bin
│   ├── flash.sh
│   └── README.md
├── hardware/               board reference
│   ├── images/             board photo, header/ethernet close-ups, 3D render
│   ├── schematics/          full schematic PDF + annotated crops
│   ├── bom.csv              full bill of materials
│   └── README.md
└── challenges/              player guides, one file per category
    ├── automotive.md
    ├── embedded.md
    ├── wireless.md
    └── README.md
```

## Links

- 🌐 **Full guides & connection diagrams:** [gautham-sai05.github.io/wired_village](https://gautham-sai05.github.io/wired_village/)
- 🛰️ **Sysrupt (the companion OT/ICS range):** linked from the same site
- 🏷️ **team bi0s** — Wired Village

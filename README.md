<div align="center">

# ComparIoT V3

<img src="hardware/images/board.webp" alt="Compatriot badge, top view" width="460">

**The Compatriot hardware security badge.** Pre-built firmware, full hardware
reference, and player guides for every challenge.

[![Firmware](https://img.shields.io/badge/firmware-ESP32--C6-00897B)](firmware)
[![Challenges](https://img.shields.io/badge/challenges-17-success)](challenges)
[![Points](https://img.shields.io/badge/points-2775-success)](challenges)
[![Target](https://img.shields.io/badge/target-STM32F103C8-blue)](hardware)
[![Guides](https://img.shields.io/badge/full%20guides-Wired%20Village-orange)](https://gautham-sai05.github.io/wired_village/)

</div>

---

## What is Compatriot?

Compatriot is a self-contained, offline hardware security training badge built by
team bi0s for Wired Village. It's a physical, hands-on counterpart to the usual
software-only CTF. Every challenge runs on real silicon, on a real bus, not a
simulation: you sniff an actual SPI/I2C/UART line with a logic analyzer, dump an
actual external flash or EEPROM chip with a CH341A programmer, reverse-engineer a
real encrypted binary over SWD on a second microcontroller, and inject real CAN
frames onto a real automotive bus. Nothing about the attack surface is faked for the
exercise. The skills transfer directly to real embedded devices and vehicles.

The board carries two independent microcontrollers on purpose. An **ESP32-C6**
(RISC-V) runs the badge's own UI, challenge logic, BLE/WiFi stack, and the
CAN-over-Ethernet bridge. A separate **STM32F103C8T6** target chip has only one job:
be a genuine reverse-engineering target. Attendees connect their own debug probe to
it over SWD and extract a flag from its firmware the same way they would on any
unknown embedded device in the field. A W5500 Ethernet module exposes a real CAN bus
(bridged over `cannelloni`) for the automotive challenges, so the UDS diagnostic and
ISO-TP tooling used here is identical to what's used against a real vehicle's OBD
port.

The badge is deliberately self-contained: no backend server, no internet dependency,
no shared infrastructure that can fall over under load. Progress is scored and
persisted on the badge itself (NVS, survives a reboot), so it scales to as many
attendees and as many badges as you can physically hand out. The included
[`setup.sh`](https://github.com/gautham-sai05/wired_village) and
[`firmware/flash.sh`](firmware/flash.sh) scripts are built around exactly that:
provisioning many attendee laptops and many badges, unattended, for a live event.

**17 challenges across 3 categories** (Automotive, Embedded, Wireless), each with a
guided hint and a full walkthrough, so the badge works equally well as a timed CTF
station and as a self-paced teaching tool. Full write-ups, wiring diagrams, and tool
setup instructions are published at
[gautham-sai05.github.io/wired_village](https://gautham-sai05.github.io/wired_village/).
This repository is the portable reference, firmware, hardware, and guides, needed to
actually build, flash, and run the badge.

## Contents

- [What is Compatriot?](#what-is-compatriot)
- [What's in this repo](#whats-in-this-repo)
- [Quick start](#quick-start)
- [The badge](#the-badge)
- [Categories](#categories)
- [Repository structure](#repository-structure)
- [Links](#links)

## What's in this repo

| Folder | Contents |
|--------|----------|
| [`firmware/`](firmware) | Pre-built binaries and a one-command flash script |
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
| **Network** | W5500 Ethernet module, speaks `cannelloni` (CAN-over-UDP) for Automotive. Onboard BLE and WiFi for Wireless. |
| **Display** | 320×240 LCD, 5-button navigation |
| **Challenges** | 3 categories, 17 challenges, 2775 total points |

See [`hardware/README.md`](hardware/README.md) for the full pin map, schematics, 3D
render and bill of materials.

## Categories

| Category | Challenges | Points | Guide |
|----------|:---:|:---:|-------|
| Automotive (CAN bus and UDS over Ethernet) | 5 | 1150 | [`challenges/automotive.md`](challenges/automotive.md) |
| Embedded (hardware peripherals) | 7 | 825 | [`challenges/embedded.md`](challenges/embedded.md) |
| Wireless (BLE / WiFi) | 5 | 800 | [`challenges/wireless.md`](challenges/wireless.md) |

## Repository structure

```
ComparIoT_V3/
├── firmware/              pre-built binaries, ready to flash
│   ├── compatriot_merged.bin
│   ├── flash.sh
│   └── README.md
├── hardware/              board reference
│   ├── images/            board photo, header/ethernet close-ups, 3D render
│   ├── schematics/        full schematic PDF + annotated crops
│   ├── bom.csv            full bill of materials
│   └── README.md
└── challenges/            player guides, one file per category
    ├── automotive.md
    ├── embedded.md
    ├── wireless.md
    └── README.md
```

## Links

- Full guides and connection diagrams: [gautham-sai05.github.io/wired_village](https://gautham-sai05.github.io/wired_village/)
- Sysrupt, the companion OT/ICS range, is linked from the same site
- Built by team bi0s for Wired Village

## Acknowledgements

Compatriot's dual-microcontroller approach (an ESP32 for the badge platform paired
with a separate STM32 as a real reverse-engineering target) follows the same idea as
[Traboda's CompatrIoT](https://github.com/traboda/CompatrIoT), an open-source
hardware security training platform built around the same concept. This build is
team bi0s's own implementation for Wired Village: its own PCB, firmware, challenges,
and flags.

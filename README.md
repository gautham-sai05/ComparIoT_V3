# ComparIoT V3

The Compatriot hardware badge — pre-built firmware, hardware reference, and player
guides. No firmware source here, just what you need to flash a badge, know what's
on it, and solve the challenges.

Full write-ups and a browsable site also live at
[Wired Village](https://gautham-sai05.github.io/wired_village/).

## What's in this repo

| Folder | Contents |
|--------|----------|
| [`firmware/`](firmware) | Pre-built binaries + a one-command flash script |
| [`hardware/`](hardware) | Board photos, schematic crops, pin maps |
| [`challenges/`](challenges) | Player guides for all 17 challenges (Automotive / Embedded / Wireless) |

## Quick start

1. Flash the badge:
   ```bash
   cd firmware
   ./flash.sh /dev/ttyACM0
   ```
2. Connect a serial terminal at **115200 8N1** to see the badge's own console.
3. Open [`challenges/`](challenges) and start solving. The badge screen itself also
   shows each challenge's objective and wiring.

## The badge

- **MCU:** ESP32-C6-WROOM-1 (RISC-V), 4 MB flash
- **Secondary target:** STM32F103C8T6, SWD-debuggable over header H3
- **Network:** W5500 Ethernet module, speaks `cannelloni` (CAN-over-UDP) for the
  Automotive challenges; onboard BLE + WiFi for the Wireless challenges
- **Display:** 320&times;240 LCD, 5-button navigation
- 3 categories, 17 challenges, 2775 total points

See [`hardware/README.md`](hardware/README.md) for the full pin map and part list.

## Categories

| Category | Challenges | Points |
|----------|-----------|--------|
| Automotive | 5 | 1150 |
| Embedded | 7 | 825 |
| Wireless | 5 | 800 |

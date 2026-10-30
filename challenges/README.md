# Challenges

Player-facing guides for all 17 Compatriot challenges, grouped by category. Each
guide explains the tool, how to wire up to the badge, a hint, and a full step-by-step
walkthrough — none of them print the flag itself, you still have to find it.

| File | Category | Count | Points |
|------|----------|-------|--------|
| [automotive.md](automotive.md) | Automotive — CAN bus + UDS over Ethernet | 5 | 1150 |
| [embedded.md](embedded.md) | Embedded — hardware peripherals | 7 | 825 |
| [wireless.md](wireless.md) | Wireless — BLE / WiFi | 5 | 800 |
| | **Total** | **17** | **2775** |

## How to score

Connect a serial terminal at **115200 8N1** (`screen /dev/ttyACM0 115200` or
`minicom -D /dev/ttyACM0 -b 115200`), open **Submit Flag** on the badge's home
carousel, pick the challenge with Up/Down + Enter, and type the flag. Progress is
saved on the badge (NVS) and survives a reboot.

See the [hardware](../hardware) folder for header/pin references used throughout
these guides, and [firmware](../firmware) to flash the badge.

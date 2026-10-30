# Hardware

The Compatriot badge is an ESP32-C6-WROOM-1 (RISC-V) board with a secondary
STM32F103C8T6 target chip, a W5500 Ethernet module for CAN-over-Ethernet, and a set
of breakout headers for the hardware challenges.

## Images

| File | What it shows |
|------|----------------|
| `images/board.webp` | Full board, top view |
| `images/headers.jpg` | Close-up of the H1/H2/H3 and U10/U11/U13/U14 breakout headers |
| `images/ethernet.jpg` | The RJ45 (W5500) Ethernet jack used for the CAN bridge |
| `schematics/headers.jpg` | Schematic crop of the breakout headers (pin numbers/net names) |
| `schematics/eeprom_flash.jpg` | Schematic crop of the external I2C EEPROM (U2) and SPI flash (U5) |
| `schematics/io.jpg` | Schematic crop of the free/expansion GPIOs used by the sniffing challenges |

## Core peripherals

| Part | Function |
|------|----------|
| ESP32-C6-WROOM-1 | Main MCU — badge UI, challenge logic, BLE/WiFi, CAN bridge |
| STM32F103C8T6 (U7) | Secondary SWD-debuggable target chip (Target Acquired challenge) |
| W5500 (RJ1) | Ethernet-to-SPI bridge, speaks `cannelloni` (CAN-over-UDP) |
| M24256E (U2) | External I2C EEPROM, 32 KB, addr `0x50` |
| W25Q64 (U5) | External SPI NOR flash |
| AW9523 | I2C GPIO/button expander, addr `0x58` |

## Key pin map

| Signal | GPIO | Header / location |
|--------|------|--------------------|
| I2C_SDA / I2C_SCL | IO21 / IO22 | U14 pins 5 / 6 |
| UART0 TX (leak) | IO16 | U13 pin 4 (net `TX_ESP32`) |
| SPI sniff SCK / MOSI / CS | IO2 / IO3 / IO15 | U13 pins 6 / 5 / 2 |
| SPI flash (W25Q64) SCK/MOSI/MISO/CS | IO20 / IO18 / IO19 / IO0 | shared display bus |
| STM32 SWD (onboard DAP) | SWDIO=IO4, SWCLK=IO6 | shared with JTAG header |
| STM32 target SWD (H3) | SWDIO=PA13, SWCLK=PA14, NRST, GND | H3 |
| NeoPixel | IO10 | — |
| Buzzer | IO11 | — |

GPIO4/5/6/7 on the ESP32 are wired to the onboard SWD/JTAG debug link to the STM32
target — don't reuse them for anything else, they'll fight the debug interface.

No raw KiCad source is published here. These images are exports from the board's own
design files, cropped and color-corrected for readability.

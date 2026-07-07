# STM32 CC1101 USB Dongle

Custom USB dongle featuring **STM32F030F4P6** + **CC1101** RF transceiver + **CH340N** USB-UART bridge. A full hardware project built from scratch — schematic and PCB design in Altium Designer, firmware, and hands-on debugging.

| Front | Back |
|---|---|
| ![Board front](docs/front.png) | ![Board back](docs/back.png) |

---

## Overview

This project is a compact USB dongle for interfacing with sub-GHz RF devices via the CC1101 transceiver. The STM32F030F4P6 handles SPI communication with the CC1101 and exposes data to a host PC through a CH340N USB-to-UART bridge.

**Core components:**
| Component | Role |
|---|---|
| STM32F030F4P6 | Main MCU (Cortex-M0), handles SPI ↔ CC1101 and UART ↔ CH340N |
| CC1101 | Sub-GHz RF transceiver (315/433/868/915 MHz) |
| CH340N | USB-to-UART bridge for host communication |

---

## Schematic & PCB Design (Altium Designer)

All schematic and PCB design was done in **Altium Designer**.

- **Custom schematic symbol for CC1101** — no ready-made symbol was available in the standard libraries, so the component symbol and footprint were built and verified from the datasheet pinout.
- **Series resistors on SPI and UART lines** — added to dampen reflections and reduce EMI on high-speed digital lines between the MCU, CC1101, and CH340N.
- **USB protection** — a polyfuse (overcurrent protection) combined with a TVS diode (ESD/transient protection) on the USB data and power lines.
- **SWD header** — dedicated programming/debug interface for flashing and debugging via ST-Link.
- **PCB stack-up considerations** — evaluated Core vs. Prepreg material choices and controlled impedance requirements for the RF-adjacent traces near the CC1101.

<!-- TODO: додай docs/schematic.png (експорт схеми з Altium) і розкоментуй рядок нижче -->
<!-- ![Schematic](docs/schematic.png) -->

<!-- TODO: додай docs/pcb-layout.png (вигляд трасування плати) і розкоментуй рядок нижче -->
<!-- ![PCB layout](docs/pcb-layout.png) -->

---

## Firmware

- Developed in **STM32CubeIDE** (STM32F0 HAL/LL)
- Handles:
  - SPI initialization and register configuration of the CC1101
  - RF packet transmission/reception
  - UART bridging of data to/from the host PC via CH340N
- Programmed and debugged via **SWD (ST-Link)**

```
firmware/        - STM32CubeIDE project
docs/            - schematics, PCB exports, photos
```

<!-- TODO: додай короткий приклад коду ініціалізації CC1101, якщо хочеш показати стиль коду -->

---

## Design Challenges & Solutions

Some of the practical issues encountered during development:

- **Signal integrity on SPI/UART lines** — added series termination resistors after observing reflections/noise on high-speed digital signals between MCU and peripherals.
- **USB robustness** — designed protection circuitry (polyfuse + TVS) to guard against overcurrent and ESD events on the USB port.
- **PCB material selection** — weighed Core vs. Prepreg options for the stack-up, considering controlled impedance requirements for RF-sensitive routing near the CC1101.
- **SWD programming setup** — verified correct wiring and pin mapping for reliable flashing/debugging through ST-Link.

<!-- TODO: тут головне — додай конкретний кейс. Наприклад: "Спочатку прошивка не флешилась через ST-Link — виявилось, що... Вирішив, що..." Це найважливіша секція для рекрутера. -->

---

## What I'd Improve Next

<!-- TODO: 2-3 реальні пункти, що зробив би інакше в наступній ревізії -->
-
-

---

## Skills Demonstrated

- Schematic capture & PCB design in Altium Designer (including custom library parts)
- Signal integrity considerations for high-speed digital and RF-adjacent traces
- USB interface protection design (ESD/overcurrent)
- Embedded firmware development on STM32 (SPI, UART)
- Hardware debugging via SWD/ST-Link

---

## Author

**Levik** — Telecommunications & Radio Engineering student, Lviv Polytechnic National University
[GitHub](https://github.com/levyyk) · [Portfolio](https://levyyk.github.io/portfolio/)

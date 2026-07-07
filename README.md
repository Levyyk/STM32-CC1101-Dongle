# STM32 CC1101 USB Dongle

Custom USB dongle design featuring **STM32F030F4P6** + **CC1101** RF transceiver + **CH340N** USB-UART bridge.
A complete schematic and PCB design project built in Altium Designer — from component selection to a production-ready layout.

> **Note:** This is a design-stage project — the board has not been manufactured/assembled. The repository showcases the schematic and PCB design process rather than a physical build or firmware implementation.

| Front (3D) | Back (3D) |
|---|---|
| ![Board front](docs/front.png) | ![Board back](docs/back.png) |

---

## Overview

This project is a compact USB dongle designed for interfacing with sub-GHz RF devices via the CC1101 transceiver. The STM32F030F4P6 is intended to handle SPI communication with the CC1101 and expose data to a host PC through a CH340N USB-to-UART bridge.

**Core components:**
| Component | Role |
|---|---|
| STM32F030F4P6 | Main MCU (Cortex-M0), SPI ↔ CC1101 and UART ↔ CH340N |
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

**Schematic (PDF):**
[📄 docs/schematic.pdf](docs/schematic.pdf)

**PCB layers:**
| Top layer | Bottom layer |
|---|---|
| ![Top layer](docs/pcb-layout-top.png) | ![Bottom layer](docs/pcb-layout-bottom.png) |

**Board dimensions:**
![Board size](docs/size.png)

---

## Programming

The board is designed to be flashed and debugged via **SWD** using an **ST-LINK/V2** programmer.

🔗 [ST-LINK/V2 — official product page (STMicroelectronics)](https://www.st.com/en/development-tools/st-link-v2.html)

---

## Design Challenges & Solutions

Some of the practical considerations addressed during the design process:

- **Signal integrity on SPI/UART lines** — added series termination resistors to dampen reflections/noise on high-speed digital lines between MCU and peripherals.
- **USB robustness** — designed protection circuitry (polyfuse + TVS) to guard against overcurrent and ESD events on the USB port.
- **PCB material selection** — weighed Core vs. Prepreg options for the stack-up, considering controlled impedance requirements for RF-sensitive routing near the CC1101.
- **SWD programming header** — verified correct wiring and pin mapping for reliable flashing/debugging through ST-Link.

<!-- TODO: якщо хочеш, додай сюди 1-2 конкретні деталі "чому саме такий номінал резистора" чи "чому саме такий стек шарів обрав" — це найцінніше для рекрутера -->

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
- PCB stack-up and material selection for controlled impedance
- SWD debug interface design

---

## Author

**Levik** — Telecommunications & Radio Engineering student, Lviv Polytechnic National University
[GitHub](https://github.com/levyyk) · [Portfolio](https://levyyk.github.io/portfolio/)

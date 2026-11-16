# Null Modem IXT

[![OSHWA Certified ES000060](https://img.shields.io/badge/OSHWA%20UID-ES000060-008080?style=flat-square)](https://certification.oshwa.org/es000060.html)
[![Hardware License: CERN-OHL-S v2](https://img.shields.io/badge/Hardware%20License-CERN--OHL--S--v2-blue?style=flat-square)](https://ohwr.org/cern_ohl_s_v2.txt)
[![Documentation License: CC BY-SA 4.0](https://img.shields.io/badge/Docs%20License-CC%20BY--SA%204.0-lightgrey?style=flat-square)](https://creativecommons.org/licenses/by-sa/4.0/)

Passive open-source hardware board (v1.0) for RS-232 serial communication switching and signal monitoring, developed for the Telematics Laboratories at UPC (Campus Nord). It implements a 6-position DIP switch for Null Modem cross-over connections and provides two 12-pin female headers (6 duplicated signal lines per side) plus a PCB GND test point for oscilloscope probing and custom jumper patching.

## Hardware Overview

| Front View | Back View | Lab Test Setup |
| :---: | :---: | :---: |
| ![Null Modem IXT Front](img/Null_Modem_IXT_Front.png) | ![Null Modem IXT Back](img/Null_Modem_IXT_Back.png) | ![Null Modem IXT Test](img/Null_Modem_IXT_Test.png) |

---

## Switch Configuration & Pinout

### DIP Switch Cross-Over Matrix (`SW2`)
Each switch in the 6-position DIP (`SW2`) bridges a crossed Null Modem line between `J1` and `J2`. Pins 1 (`DCD`) and 6 (`DSR`) are tied together on each DB9 connector, pin 5 (`GND`) is permanently shared with the PCB GND test point (`J7`), and pin 9 (`RI`) is unconnected (`NC`).

| Switch | `J1` Side (Left) | `J2` Side (Right) | Null Modem Function |
| :---: | :--- | :--- | :--- |
| **SW1** | Pins 1 & 6 (`DCD` + `DSR`) | Pin 4 (`DTR`) | Handshake cross-over (`DTR` $\rightarrow$ `DSR`/`DCD`) |
| **SW2** | Pin 2 (`RXD`) | Pin 3 (`TXD`) | Data line cross-over (`J2 TXD` $\rightarrow$ `J1 RXD`) |
| **SW3** | Pin 3 (`TXD`) | Pin 2 (`RXD`) | Data line cross-over (`J1 TXD` $\rightarrow$ `J2 RXD`) |
| **SW4** | Pin 4 (`DTR`) | Pins 1 & 6 (`DCD` + `DSR`) | Handshake cross-over (`DTR` $\rightarrow$ `DSR`/`DCD`) |
| **SW5** | Pin 7 (`RTS`) | Pin 8 (`CTS`) | Flow control cross-over (`J1 RTS` $\rightarrow$ `J2 CTS`) |
| **SW6** | Pin 8 (`CTS`) | Pin 7 (`RTS`) | Flow control cross-over (`J2 RTS` $\rightarrow$ `J1 CTS`) |

### Operating Modes
- **Full Null Modem (Hardware Handshake):** Set `SW1`–`SW6` to **`ON`**.
- **3-Wire Null Modem (No Handshake):** Set `SW2` and `SW3` to **`ON`**; set `SW1`, `SW4`, `SW5`, and `SW6` to **`OFF`**.
- **Straight-Through / Custom Patching:** Set `SW1`–`SW6` to **`OFF`** to isolate the internal cross-overs, then link the desired signals between the `J1` and `J2` side headers using 2.54 mm jumper wires.

### Side Test Headers (12-Pin Female)
Each 12-pin side header consists of two duplicated 6-pin groups (`J3`/`J4` on the `J1` side, and `J5`/`J6` on the `J2` side), allowing simultaneous jumper patching and oscilloscope signal probing:

| Header Pins | `J1` Side (`J3` & `J4`) | `J2` Side (`J5` & `J6`) |
| :---: | :--- | :--- |
| **1** (Pins 1 & 7) | `J1` Pins 1 & 6 (`DCD` + `DSR`) | `J2` Pin 4 (`DTR`) |
| **2** (Pins 2 & 8) | `J1` Pin 2 (`RXD`) | `J2` Pin 3 (`TXD`) |
| **3** (Pins 3 & 9) | `J1` Pin 3 (`TXD`) | `J2` Pin 2 (`RXD`) |
| **4** (Pins 4 & 10) | `J1` Pin 4 (`DTR`) | `J2` Pins 1 & 6 (`DCD` + `DSR`) |
| **5** (Pins 5 & 11) | `J1` Pin 7 (`RTS`) | `J2` Pin 8 (`CTS`) |
| **6** (Pins 6 & 12) | `J1` Pin 8 (`CTS`) | `J2` Pin 7 (`RTS`) |

---

## Technical Specifications
- **Hardware Version**: 1.0
- **PCB Dimensions**: 70.01 mm × 51.96 mm
- **Design Software**: KiCad 9.0.3
- **Layer Count**: 2-layer THT (Top Copper / Bottom Copper)
- **Serial Connectors**: 2× DB9 Female Right-Angle (90°) THT with UNC 4-40 jack screws
- **DIP Switch**: Omron A6T Series (or equivalent), 6-position slide switch ($\ge 1,000$ operations min.)
- **Probing & Ground**:
  - 2× 12-pin female headers (2.54 mm pitch), one on each side, for jumper wire patching and oscilloscope probes
  - 1× PCB GND test point (`J7`) for oscilloscope ground alligator clip

---

## Repository Structure
```text
Null_Modem_IXT/
├── LICENSE_HARDWARE            # CERN-OHL-S-v2 License
├── LICENSE_DOCUMENTATION       # CC-BY-SA 4.0 License
├── README.md                   # Project documentation
├── img/                        # Project photos & test setups
│   ├── Null_Modem_IXT_Front.png
│   ├── Null_Modem_IXT_Back.png
│   └── Null_Modem_IXT_Test.png
├── hardware/                   # KiCad source design files
│   ├── Null_Modem_IXT.kicad_pro
│   ├── Null_Modem_IXT.kicad_sch
│   ├── Null_Modem_IXT.kicad_pcb
│   └── Null_Modem_IXT.kicad_dru
├── production/                 # Manufacturing deliverables
│   ├── gerbers/                # Gerber RS-274X files
│   │   ├── Null_Modem_IXT-F_Cu.gbr
│   │   ├── Null_Modem_IXT-B_Cu.gbr
│   │   ├── Null_Modem_IXT-F_Mask.gbr
│   │   ├── Null_Modem_IXT-B_Mask.gbr
│   │   ├── Null_Modem_IXT-F_Silkscreen.gbr
│   │   ├── Null_Modem_IXT-Edge_Cuts.gbr
│   │   └── Null_Modem_IXT.drl
│   ├── Null_Modem_IXT_BOM.csv
│   └── Null_Modem_IXT_Schematic.pdf
```

---

## Bill of Materials (BOM)
| Reference | Qty | Value / Component | Package / Footprint | Description / Part Number |
| :--- | :--- | :--- | :--- | :--- |
| J1, J2 | 2 | DB9 Female 90° | DB9_Female_RightAngle_THT | RS-232 Female Connector, 90° PCB Mount |
| SW2 | 1 | Omron A6T DIP Switch | DIP-12 Slide Switch | 6-Position DIP Switch ($\ge 1,000$ cycles) |
| J3–J4, J5–J6 | 2 | Female Pin Header 12x1 | PinHeader_1x12_P2.54mm_Vertical | Duplicated 6-signal monitoring & patching headers |
| J7 | 1 | PCB GND Test Point | TestPoint_Loop_THT | Ground test point for oscilloscope alligator clip |

---

## Certification & Licensing

This project is certified by the **Open Source Hardware Association (OSHWA)** under the [OSHWA Open Source Hardware Definition](https://www.oshwa.org/definition/).

**[Official OSHWA Certification Record — UID: ES000060](https://certification.oshwa.org/es000060.html)**

- **OSHWA UID**: [`ES000060`](https://certification.oshwa.org/es000060.html)
- **Certification Date**: October 03, 2026
- **Hardware Version**: 1.0
- **Creator**: Jordi Lino — Telematics Laboratories Manager, Campus Nord, Universitat Politècnica de Catalunya (UPC), Spain
- **Project Type**: Education (`NULLMODEM`, `TELEMATICS`)

### Licenses
- **Hardware Design** (Schematics, PCB layout, Gerbers): [CERN-OHL-S-v2](https://ohwr.org/cern_ohl_s_v2.txt)
- **Documentation & Media**: [CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)

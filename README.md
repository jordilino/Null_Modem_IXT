# Null Modem IXT

`Null_Modem_IXT` is an open-source hardware board designed for RS-232 serial communication switching and signal monitoring. It allows users to toggle between a direct pass-through connection and a Null Modem cross-over configuration using a high-durability DIP switch, featuring dedicated test points for oscilloscope grounding and lab instrumentation.

This project is certified (pending submission) as Open Source Hardware under the OSHWA definition.

---

## Technical Specifications
* **PCB Dimensions**: 70.01 mm × 51.96 mm
* **Design Software**: KiCad 9.0.3
* **Layer Count**: 2-layer THT design (Top Copper / Bottom Copper)
* **Primary Connectors**: 2× DB9 Female Right-Angle (90°) THT connectors with UNC 4-40 jack screws
* **DIP Switch**: Omron A6T Series (or equivalent) rated for $\ge 1,000$ operations min.
* **Ground Reference**: 
  * 1×4 mm Banana Socket / Test Point for lab power supply or chassis ground

---

## Repository Structure
```text
Null_Modem_IXT/
├── LICENSE_HARDWARE            # CERN-OHL-S-v2 License
├── LICENSE_DOCUMENTATION       # CC-BY-SA 4.0 License
├── README.md                   # Main English documentation
├── README_CA.md                # Catalan documentation
├── hardware/                  # KiCad source design files
│   ├── Null_Modem_IXT.kicad_pro
│   ├── Null_Modem_IXT.kicad_sch
│   ├── Null_Modem_IXT.kicad_pcb
│   └── Null_Modem_IXT.kicad_dru
├── production/                # Manufacturing deliverables
│   ├── gerbers/               # Gerber RS-274X files
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
| InterruptorAtoB1 | 1 | Omron A6T DIP Switch | DIP-12 Slide Switch | 12-Position DIP Switch ($\ge 1,000$ cycles) |
| PINFEMELLA(a)1, PINFEMELLA(b)1 | 2 | Female Pin Header 12x1 | PinHeader_1x12_P2.54mm_Vertical | Breakout / Break-in test headers |
| GND(banana)1 | 1 | 4mm Banana Socket | Socket_Banana_4mm_THT | Lab Ground Binding Post |
| GND_Turret | 1 | Mechanical Turret Terminal | Terminal_Turret_THT | Oscilloscope Ground Probe Attachment Post |

---

## Open Source Hardware Compliance & Licensing

This project fully complies with the [OSHWA Open Source Hardware Definition](https://www.oshwa.org/definition/).

### License Terms
* **Hardware Design** (Schematics, PCB layout, Gerbers): Licensed under the **CERN Open Hardware Licence Strongly Reciprocal v2** ([CERN-OHL-S-v2](https://ohwr.org/cern_ohl_s_v2.txt)).
* **Documentation & Media**: Licensed under the **Creative Commons Attribution-ShareAlike 4.0 International License** ([CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)).

OSHWA Registration ID: *Pending Submission (ES0000XX)*

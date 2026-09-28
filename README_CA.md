# Null Modem IXT

`Null_Modem_IXT` és un mòdul de maquinari lliure dissenyat per a la commutació i monitorització de senyals en línies de comunicació sèrie RS-232. Permet alternar fàcilment entre una connexió directa pas a pas (*pass-through*) i una configuració creuada *Null Modem* mitjançant un commutador DIP d'alta durabilitat, incorporant punts de presa de massa dedicats per a sondes d'oscil·loscopi i instrumentació de laboratori.

Aquest projecte està dissenyat per complir amb la definició de Maquinari Lliure de l'OSHWA (Open Source Hardware Association).

---

## Especificacions Tècniques
* **Dimensions de la PCB**: 70,01 mm × 51,96 mm[cite: 3]
* **Programari de disseny**: KiCad 9.0.3[cite: 1]
* **Nombre de capes**: Disseny THT de 2 capes (Cobre Superior / Cobre Inferior)[cite: 1, 4]
* **Connectors principals**: 2× DB9 Femella horitzontal a 90° THT amb fressat i rosques UNC 4-40
* **Commutador DIP**: Sèrie Omron A6T (o equivalent) garantit per a $\ge 1.000$ operacions
* **Referència de Massa (GND)**:
  * 1× Terminal tipus torre (*Turret Terminal*) per a la pinça de massa de la sonda d'oscil·loscopi
  * 1× Zòcol per a connector Banana de 4 mm per a font d'alimentació o massa de xassís

---

## Estructura del Repositori

```text
Null_Modem_IXT/
├── LICENSE.txt                # Termes de llicència de hardware i documentació
├── README.md                  # Documentació principal en anglès
├── README_CA.md               # Documentació en català
├── hardware/                  # Fitxers font de disseny KiCad
│   ├── Null_Modem_IXT.kicad_pro
│   ├── Null_Modem_IXT.kicad_sch
│   ├── Null_Modem_IXT.kicad_pcb
│   └── Null_Modem_IXT.kicad_dru
├── production/                # Entregables per a fabricació
│   ├── gerbers/               # Fitxers Gerber RS-274X
│   │   ├── Null_Modem_IXT-F_Cu.gbr
│   │   ├── Null_Modem_IXT-B_Cu.gbr
│   │   ├── Null_Modem_IXT-F_Mask.gbr
│   │   ├── Null_Modem_IXT-B_Mask.gbr
│   │   ├── Null_Modem_IXT-F_Silkscreen.gbr
│   │   ├── Null_Modem_IXT-Edge_Cuts.gbr
│   │   └── Null_Modem_IXT.drl
│   ├── Null_Modem_IXT_BOM.csv
│   └── Null_Modem_IXT_Schematic.pdf
└── docs/                      # Guies de muntatge i verificació
    └── assembly_guide.md
```
---

## Llista de Materials (BOM)
| Referència | Qtt | Valor / Component | Format / Footprint | Descripció / Ref. Fabricant |
| :--- | :--- | :--- | :--- | :--- |
| J1, J2 | 2 | DB9 Femella 90° | DB9_Female_RightAngle_THT | Connector RS-232 Femella, muntatge a 90° |
| InterruptorAtoB1 | 1 | DIP Switch Omron A6T | DIP-12 Slide Switch | Commutador DIP de 12 posicions ($\ge 1.000$ cicles) |
| PINFEMELLA(a)1, PINFEMELLA(b)1 | 2 | Tira de pins hembra 12x1 | PinHeader_1x12_P2.54mm_Vertical | Tira de connectors per a mesura i ponts |
| GND(banana)1 | 1 | Zòcol Banana 4mm | Socket_Banana_4mm_THT | Connector de massa de laboratori |
| GND_Turret | 1 | Terminal Turret | Terminal_Turret_THT | Post de connexió per a sonda d'oscil·loscopi |

---

## Compliment i Llicències OSHWA

Aquest projecte compleix íntegrament amb la definició de [Maquinari Lliure d'OSHWA](https://www.oshwa.org/definition/).

### Termes de Llicència
* **Disseny de Maquinari** (Esquemàtic, PCB layout, Gerbers): Llicenciat sota **CERN Open Hardware Licence Strongly Reciprocal v2** ([CERN-OHL-S-v2](https://ohwr.org/cern_ohl_s_v2.txt)).
* **Documentació i Mitjans**: Llicenciat sota **Creative Commons Reconeixement-CompartirIgual 4.0 Internacional** ([CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)).

Registre OSHWA: *Pendent d'enviament (ES0000XX)*

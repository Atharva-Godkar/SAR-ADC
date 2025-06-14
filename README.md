# SAR ADC
# Design of 8 bit SAR ADC

This project presents the complete design, implementation, and analysis of an 8-bit Successive Approximation Register (SAR) Analog-to-Digital Converter (ADC) using Cadence Virtuoso tool. This ADC works on principle of binary search algorithm. The system is composed of four main building blocks: a Sample and Hold (S/H) circuit, a Comparator, a Successive Approximation Register, and an R-2R ladder-based Digital-to-Analog Converter (DAC). The design methodology adopted for this project emphasizes a bottom-up approach, starting with transistor-level schematic design & going upto functional bock level design. For layout we only performed DRC & LVS. we didnt perfrom post layout simulation, PVT analysis etc

Specifications of ADC -
1.	ADC Type = SAR ADC
2.	Resolution = 8 bits
3.	Sample Hold clock speed = 100 ns (10Mhz)
4.	SAR register clock speed = 11.1111 ns (90MHz)
5.	Conversion time = 8 bits * 11.1111 = 88.8888 ns
6.	Supply voltage = 3.3v
7.	Technology used = 180nm 

## software tools
| Tool        | Description |
| :-----------: | :-----------: |
| ![Cadence-Emblem.png](https://i.postimg.cc/dty4wFXS/Cadence-Emblem.png)| Cadence Design Systems provides a wide range of products and services including digital integrated circuit design, functional verification, custom IC design, PCB layout and design, and system design enablement. |


## block diagram of ADC
![ADC block diagram](https://postimage.me/images/2025/06/13/Screenshot-3862.png)

## OPAMP 
we have designed PMOS differential pair OPAMP. it is a 2 stage OPAMP - 1st stage is differential pair amplifier , 2nd stage is CS smplifier. on LHS we have constant current source. OPAMP is fundamental part of our design cuz we will use this OPAMP to further design other 3 analog blocks - SH, DAC, Comparator. we used root force method to do sizing of MOSFETS. 
## OPAMP - MOSFET sizing

| MOSFET | M2 | M4 M5 | M6 M7 | M9 | M1 | M8 | M3 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| LENGTH | 1u | 1u | 1u | 1u | 1u | 1u | 1u |
| TOTAL WIDTH | 76.39u | 6.65u | 10u | 14.55u | 18.14u | 2.46u | 71.2u |
| WIDTH OF EACH MULTIPLIER | 6.365u | 6.65u | 2u | 2.425u | 6.046u | 2.46u | 5.93u |
| NUMBER OF MULTIPLIER | 12 | 1 | 5 | 6 | 3 | 1 | 12 |

## OPAMP circuit diagram
![OPAMP circuit diagram](https://postimage.me/images/2025/06/13/Screenshot-3865.png)

## OPAMP - inter digitization & segmentation
![inter digitization &amp;amp; segmentation](https://postimage.me/images/2025/06/13/Screenshot-3864.png)

## OPAMP - layout
![OPAMP layout](https://postimage.me/images/2025/06/13/Screenshot-from-2025-04-03-16-19-38.png)


## OPAMP parameters
| parameter | theoretical value | practical value |
| :-----------: | :-----------: | :-----------: |
| suuply voltage | 3.3 v | 3.3 v |
| phase margin | PM > 60 db | 180 - 90 = 86 db |
| power | PD < 2 mW | (50 + 200 + 200)3.3 = 1.485 mW |
| settling time | Ts < 40ns | 56.159 ns |
| gain bandwidth product | NA | 33 MHz |
| open loop gain | NA | 73.8 dB |
| unity gain frequency | NA | 28.99 MHz |
| phase angle | NA | 93.57 degree |
| slew rate | NA | 4.808 KV/us |

## ADC circuit diagram
![ADC circuit diagram](https://postimage.me/images/2025/06/13/Screenshot-3867.png)

## ADC parameters
| Parameters | This Work | Paper [5] | Paper [6] | Paper [7] | Paper [8] | Paper [9] |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Technology Node (nm) | 180 | 180 | 65 | 90 | 40 | 90 |
| Resolution (Bits) | 8 | 8 | 14 | 6 | 10 | 10 |
| Sampling Rate (MS/s) | 10 | 100 | 5000 | 1 | 120 | 1 |
| Supply Voltage (v) | 3.3 | 1.8 | 1 | 1 | 1.2 | 1.2 |
| Power (uW) | 8332 | 129.8 | 70 | 77.26 | 1040 | 11.88 |
| ENOB | 7 | NA | NA | 5.05 | NA | NA | 
| SNR (dB) | 43.76 | NA | NA | 37.34 | NA | NA |
| SFDR (dB) | 50.23 | NA | NA | NA | NA | NA |
| SNDR (dB)	| 41.12	| NA | NA | NA | 46.9 | NA |
| Architecture | SAR R-2R | Binary weighted capacitive | Capacitive | Binary weighted resistor | NA | Capacitive |

## ADC layout 
![ADC layout](https://postimage.me/images/2025/06/13/Screenshot-from-2025-04-17-14-58-43-1.png)

## layout parameters
| parameters | values |
| :-----------: | :-----------: |
| core dimensions | 370 um * 370 um |
| die dimensions | 518 um * 518 um |
| pad dimensions | 74 um * 74 um |
| filler pad | 74 um * 14.8 um |
| total pads | 16 |
| total MOSFET in layout | 1250 |
| total resistors in layout | 20 |
| total capacitors in layout | 21 |

## Team Members
- [@vansh](https://github.com/VanshD40)
- [@ansih](https://github.com/KNIGHTAPG)
- [@anushri]()
- [@godkar](https://github.com/Atharva-Godkar)
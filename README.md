# Two-Stage CMOS Operational Amplifier

## Overview

This project presents the design and simulation of a two-stage CMOS operational amplifier using 1 μm CMOS technology in LTspice.

The amplifier consists of:

- NMOS differential input pair
- PMOS current mirror active load
- Common-source second gain stage
- Miller compensation capacitor
- Self-biased current mirror

The design was developed using analytical transistor sizing equations and refined through LTspice simulations.

---

## Specifications

| Parameter | Value |
|------------|------------|
| Technology | 1 μm CMOS |
| Supply Voltage | 2.5 V |
| Load Capacitor | 10 pF |
| Compensation Capacitor | 2 pF |
| Bias Current | 20 μA |
| DC Gain | 68.5 dB |
| Voltage Gain | 2657 V/V |
| Unity Gain Bandwidth | 4.89 MHz |
| Phase Margin | 73.2° |
| Output Bias Voltage | 1.49 V |

---

## Circuit Architecture

### First Stage
- M1, M2 : Differential Pair
- M3, M4 : PMOS Current Mirror Load
- M5 : Tail Current Source

### Second Stage
- M6 : Common Source Gain Stage
- M7 : Current Source Load

### Bias Circuit
- M8 : Diode Connected NMOS
- R1 : 86 kΩ Bias Resistor

---

## Simulation Results

- All MOSFETs verified in saturation region
- Stable operation with 73° phase margin
- Self-biased current mirror generating approximately 20 μA
- Open-loop gain of approximately 68.5 dB

---

## Tools Used

- LTspice
- Analog CMOS Design
- Small-Signal Analysis
- Frequency Compensation
- Current Mirror Design

# Two-Stage CMOS Operational Amplifier

Design and simulation of a two-stage CMOS operational amplifier in LTspice using 1 μm CMOS technology. The project implements a differential input stage, active current-mirror load, common-source second gain stage, Miller compensation, and a self-biased current mirror to achieve high gain and stable frequency response.

---

## Overview

This project explores the complete design flow of a two-stage CMOS operational amplifier, starting from specification-based transistor sizing and ending with AC performance verification through LTspice simulations.

The amplifier consists of:

* NMOS differential input pair
* PMOS active current mirror load
* Common-source second gain stage
* Miller compensation capacitor
* Self-biased current mirror
* Capacitive load

Unlike many textbook implementations that use ideal current sources, this design employs a practical self-biased current mirror for bias generation.

---

## Design Specifications

| Parameter                   | Value     |
| --------------------------- | --------- |
| Technology                  | 1 μm CMOS |
| Supply Voltage              | 2.5 V     |
| Load Capacitance (CL)       | 10 pF     |
| Compensation Capacitor (Cc) | 2 pF      |
| Target GBW                  | 5 MHz     |
| Target Slew Rate            | 10 V/μs   |
| Bias Current                | 20 μA     |

---

## Circuit Architecture

### First Stage

* **M1, M2** → NMOS differential pair
* **M3, M4** → PMOS active current mirror load
* **M5** → Tail current source

The differential pair converts the input voltage difference into current while the active load performs differential-to-single-ended conversion and provides gain.

### Second Stage

* **M6** → Common-source gain transistor
* **M7** → Current source load

This stage provides additional voltage gain required to achieve the overall amplifier gain.

### Bias Network

* **M8** → Diode-connected reference transistor
* **R1** → Bias resistor

A self-biased current mirror generates the required 20 μA reference current, eliminating the need for an ideal current source.

### Compensation Network

* **C1 (2 pF)** → Miller compensation capacitor
* **C2 (10 pF)** → Load capacitance

The compensation capacitor introduces a dominant pole and improves phase margin for stable operation.

---

## Transistor Sizing Methodology

Initial transistor dimensions were obtained using first-order CMOS design equations.

The design process followed:

1. Selection of compensation capacitor from load capacitance.
2. Calculation of tail current from the slew-rate requirement.
3. Determination of differential pair transconductance from the gain-bandwidth specification.
4. Sizing of the differential pair and active load using MOSFET square-law equations.
5. Design of the self-biased current mirror.
6. Initial sizing of the second gain stage using phase-margin design rules.
7. Iterative optimization in LTspice to account for non-ideal effects such as:

   * Channel-length modulation
   * Finite output resistance
   * Parasitic capacitances
   * Frequency-dependent behavior

---

## Final Transistor Dimensions

| Transistor | Function            | W/L   |
| ---------- | ------------------- | ----- |
| M1         | Differential Pair   | 1.644 |
| M2         | Differential Pair   | 1.644 |
| M3         | Current Mirror Load | 20    |
| M4         | Current Mirror Load | 20    |
| M5         | Tail Current Source | 4.44  |
| M6         | Second Gain Stage   | 234.5 |
| M7         | Current Source Load | 24.8  |
| M8         | Bias Reference      | 4.44  |

---

## Simulation Results

### DC Operating Point

The self-biased current mirror successfully generates approximately 20 μA of reference current while maintaining all transistors in saturation.

### AC Performance

| Parameter            | Achieved Value |
| -------------------- | -------------- |
| DC Gain              | 68.47 dB       |
| Voltage Gain         | ≈ 2650 V/V     |
| Unity Gain Bandwidth | 4.87 MHz       |
| Phase Margin         | 73.24°         |
| Supply Voltage       | 2.5 V          |
| Bias Current         | ≈ 20 μA        |

---

## Key Design Decisions

### Why Miller Compensation?

A Miller compensation capacitor was added between the first-stage output and second-stage output to introduce a dominant pole and improve stability.

### Why Use a Self-Biased Current Mirror?

Using a self-biased current mirror makes the design more realistic and suitable for integrated circuit implementation compared to an ideal current source.

### Why Were M6 and M7 Optimized?

Theoretical sizing equations provide only first-order estimates. The final values of M6 and M7 were obtained through simulation-based optimization to satisfy gain and phase-margin requirements.

---

## Repository Structure

```text
Two-Stage-CMOS-OpAmp/
│
├── LTspice/
│   ├── opamp.asc
│   ├── opamp.raw
│
├── Images/
│   ├── Schematic.png
│   ├── AC_Response.png
│   ├── Operating_Point.png
│
├── Documents/
│   ├── Design_Calculations.pdf
│
└── README.md
```

---

## Tools Used

* LTspice XVII / LTspice 24
* CMOS Square-Law Design Methodology
* Small-Signal Analysis
* Frequency Compensation Techniques

---

## Future Improvements

Possible extensions of this work include:

* Layout design and parasitic extraction
* Slew-rate analysis
* Monte Carlo mismatch analysis
* Power-supply rejection ratio (PSRR) analysis
* Common-mode rejection ratio (CMRR) analysis
* Migration to deep-submicron CMOS technologies

---

## Author

**Lokesh Kumar**
B.Tech Electrical Engineering
Indian Institute of Technology Ropar

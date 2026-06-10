# Design and Analysis of MOS-Only Active Inductor Circuit

## Project Description
This repository contains the design, simulation, and parametric evaluation of a fully integrated, compact, low-power MOS-only active inductor circuit. Conventional on-chip spiral inductors occupy extensive silicon area, exhibit low quality factors ($Q = 3\text{--}10$) due to substrate losses, and lack electronic tunability. 

This project addresses these limitations by leveraging a gyrator-capacitor (gyrator-C) architecture implemented in standard 180 nm CMOS technology. By substituting physical coils with common-gate and common-source transistor configurations, the circuit eliminates external biasing current sources or passive components, making it a true MOS-only implementation optimized for RF integrated circuits (RFICs).

---

## Technical Specifications & Features
* **Technology Node:** TSMC 180 nm CMOS Process (`tsmc018.lib`)
* **Supply Voltage ($V_{DD}$):** 1.8 V (nominal operating conditions)
* **Power Consumption:** Approximately 1.85 mW to 1.9 mW ($I_{total} \approx 1.0\text{ mA}$)
* **Inductive Frequency Range:** Stable operation from 100 kHz up to 2 MHz
* **Self-Resonant Frequency ($f_0$):** Peak resonance in the 300–400 MHz range
* **Peak Impedance:** ~29 $\Omega$ at resonance
* **Quality Factor ($Q$):** Reaches an exceptional linear peak up to ~14,000 due to active negative resistance compensation
* **Negative Resistance Corner:** $-10.58\ \Omega$ extracted from DC Transfer Function analysis

---

## Circuit Topology and Transistor Sizing

The circuit architecture employs four MOS transistors arranged in a cross-coupled feedback loop. PMOS devices act as the primary transconductance and biasing blocks, while NMOS devices complete the gyrator feedback path. The loop translates the internal gate-source capacitance ($C_{gs}$) into an equivalent input inductance:

$$L_{eq} \propto \frac{C_{gs}}{g_{m1} \cdot g_{m2}}$$

The transistors are sized intentionally to guarantee stable feedback loop operation, high transconductance ($g_m$), and optimal saturation conditions:

| Transistor | Width ($W$) | Length ($L$) | Type | Function |
| :--- | :--- | :--- | :--- | :--- |
| **M1** | 20 $\mu$m | 0.36 $\mu$m | PMOS | Gyrator Core / Transconductance Stage |
| **M2** | 20 $\mu$m | 0.36 $\mu$m | PMOS | Gyrator Core / Transconductance Stage |
| **M3** | 10 $\mu$m | 0.36 $\mu$m | NMOS | Feedback / Stability Loop |
| **M4** | 10 $\mu$m | 0.36 $\mu$m | NMOS | Feedback / Stability Loop |

---

## Repository Structure

```text
📦 MOS-Active-Inductor
 ┣ 📂 schematics
 ┃ ┣ 📜 active_inductor_core.asc  # LTspice schematic design file
 ┃ ┗ 📜 tsmc018.lib               # TSMC 180nm transistor SPICE model library
 ┣ 📂 plots
 ┃ ┣ 📜 dc_analysis.png           # Saturation region check vs Input Voltage
 ┃ ┣ 📜 transient_power.png       # Steady-state power simulation curve
 ┃ ┣ 📜 ac_input_impedance.png    # Impedance magnitude and phase sweeps
 ┃ ┣ 📜 equivalent_inductance.png # U-shaped stable inductance band graph
 ┃ ┣ 📜 quality_factor_linear.png # Linear scale curve illustrating peak Q
 ┃ ┗ 📜 noise_spectral_density.png# Flicker and thermal noise spectral plots
 ┗ 📜 README.md                   # Project documentation and analysis
---

## Contributors
* [Shashikant](https://github.com/Shashi-kalal)
* [Tejaswini K N](https://github.com/tejaswini1009)


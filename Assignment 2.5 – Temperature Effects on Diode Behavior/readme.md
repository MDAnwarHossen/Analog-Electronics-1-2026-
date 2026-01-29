# Temperature Effects on a Silicon Diode (1N4148) – LTspice Analysis

## Overview
This simulation investigates how temperature affects the electrical behavior of a real silicon diode (1N4148). Using LTspice, a DC sweep was performed at two different temperatures (25 °C and 75 °C) to observe changes in forward voltage and reverse current. The goal is to demonstrate why temperature must be considered when analyzing and designing real electronic circuits.

---

## Circuit and Simulation Setup
The circuit consists of a DC voltage source, a 1N4148 diode, and a 1 kΩ series resistor. A DC sweep is applied from −2 V to +2 V. The same circuit is simulated at two temperatures using a temperature step command:
.step temp list 25 75

The diode current `I(D1)` is plotted to compare behavior at both temperatures.

---

## Observations

### Forward Voltage
The simulation shows that at **75 °C**, the diode conducts the same current at a **lower forward voltage** than at **25 °C**. The forward I–V curve shifts left as temperature increases. For silicon diodes, the forward voltage decreases by approximately **2 mV/°C**. Over a 50 °C increase, this results in about a **0.1 V reduction**, which matches the simulation.

### Reverse Current
In the reverse-bias region, the diode shows **higher leakage current at 75 °C** compared to 25 °C. Although small in magnitude, this leakage current increases rapidly with temperature due to thermally generated carriers in the PN junction.

---

## Why Temperature Affects Diode Behavior
As temperature increases, charge carriers gain thermal energy, making it easier to cross the PN junction. This lowers the forward voltage required for conduction. Higher temperature also increases intrinsic carrier concentration, which raises the reverse saturation current and leakage.

---

## Why This Matters in Real Electronic Systems
Temperature effects can cause increased current draw, higher power dissipation, and potential thermal runaway. Increased reverse leakage can introduce noise, offsets, or logic errors in sensitive circuits. Because of this, ideal diode models are insufficient for real-world design and temperature-aware models must be used.

---

## Conclusion
The LTspice results confirm that increasing temperature reduces forward voltage and increases reverse leakage current in a silicon diode. These effects are critical in practical electronics and must be considered for reliable circuit design.

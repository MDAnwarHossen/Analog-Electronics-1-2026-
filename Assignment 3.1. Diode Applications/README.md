# Diode Physics and Characteristics

## 1. Diode Physics and Characteristics

### a. Thermal voltage calculation
To find the thermal voltage \(V_T\) at \(25^\circ\text{C}\) we use:
\[
V_T = \frac{kT}{q}
\]

- Temperature: \(T = 25^\circ\text{C} + 273 = 298\ \text{K}\)  
- Boltzmann's constant: \(k = 1.38 \times 10^{-23}\ \text{J/K}\)  
- Electron charge: \(q = 1.602 \times 10^{-19}\ \text{C}\)

Substituting:
\[
V_T = \frac{(1.38 \times 10^{-23}\ \text{J/K})(298\ \text{K})}{1.602 \times 10^{-19}\ \text{C}}
\approx \mathbf{25.67\ \text{mV}}
\]

---

### b. Diode current calculation
Using the diode equation:
\[
I_D = I_s\left(e^{\frac{V_D}{nV_T}} - 1\right)
\]

- Saturation current: \(I_s = 40\ \text{nA} = 40 \times 10^{-9}\ \text{A}\)  
- Ideality factor: \(n = 2\)  
- Applied voltage: \(V_D = 0.5\ \text{V}\)  
- Thermal voltage: \(V_T = 0.02567\ \text{V}\) (from part a)

Compute exponent:
\[
\frac{V_D}{nV_T} = \frac{0.5}{2 \cdot 0.02567} \approx 9.739
\]

Then:
\[
I_D = 40\times 10^{-9}\cdot\left(e^{9.739} - 1\right)
\approx 0.679\ \text{mA}
\]

---

## 2. Series Diode Configuration

**Circuit parameters:** \(E = 30\ \text{V}\), \(R = 1.5\ \text{k}\Omega\), silicon (Si) diode.

### a. Approximate model (\(V_D = 0.7\ \text{V}\))
- \(V_D = 0.7\ \text{V}\)  
- \(V_R = E - V_D = 30 - 0.7 = \mathbf{29.3\ \text{V}}\)  
- \(I_D = \dfrac{V_R}{R} = \dfrac{29.3}{1.5\times 10^3} \approx \mathbf{19.53\ \text{mA}}\)

### b. Ideal model (\(V_D = 0\ \text{V}\))
- \(V_D = 0\ \text{V}\)  
- \(V_R = 30 - 0 = \mathbf{30\ \text{V}}\)  
- \(I_D = \dfrac{30}{1.5\times 10^3} = \mathbf{20\ \text{mA}}\)

### c. Conclusion
The ideal model is a good approximation here — the current difference is small (≈ 2.3–2.4%) because the supply (30 V) is large compared to the diode forward drop (0.7 V).

---

## 3. Configuration Analysis (Figure 5)

> Using the approximate silicon diode model \(V_D = 0.7\ \text{V}\).

### (a) Reverse-bias case
- The battery is oriented so the diode anode is at lower potential than the cathode → diode is **OFF**.  
- \(I = 0\ \text{A}\).

### (b) Dual-branch case
- The \(20\ \text{V}\) source makes the shared node \(-20\ \text{V}\) relative to ground. Both diodes are forward biased (anodes at 0 V, cathodes at \(-20\ \text{V}\)).  
- Voltage available across each resistor before the diode drop: \(20\ \text{V}\). With one diode drop \(0.7\ \text{V}\) across each branch:
  - \(I_1\) (10 Ω branch): \(\dfrac{20 - 0.7}{10} = \dfrac{19.3}{10} = 1.93\ \text{A}\)  
  - \(I_2\) (20 Ω branch): \(\dfrac{20 - 0.7}{20} = \dfrac{19.3}{20} = 0.965\ \text{A}\)  
- Total current: \(1.93 + 0.965 = \mathbf{2.895\ \text{A}}\)

### (c) Back-to-back (series-opposed) case
- Two series Si diodes are oppositely oriented in the middle branch → that branch behaves like an open circuit. Current flows only through the 10 Ω branch.  
- Given a 10 V supply for that branch:
  - \(I = \dfrac{10\ \text{V}}{10\ \Omega} = \mathbf{1\ \text{A}}\)

---

## 4. Parallel and Multi-diode Networks

### (a) Si and GaAs in parallel
- Source: \(1\ \text{V}\)  
- Diodes in parallel: Si (\(0.7\ \text{V}\)) and GaAs (\(1.2\ \text{V}\)).  
- The Si diode conducts first and clamps the parallel node to \(0.7\ \text{V}\); GaAs remains off.  
- Output node: \(V_o = 1 - 0.7 = \mathbf{0.3\ \text{V}}\)  
- Current through resistor \(R = 1\ \text{k}\Omega\):
  \[
  I = \frac{0.3}{1\times 10^3} = \mathbf{0.3\ \text{mA}}
  \]

### (b) Multi-stage Si network
- Path: \(+16\ \text{V} \rightarrow\) one Si diode \((0.7\ \text{V})\) \(\rightarrow\) parallel pair of Si diodes (effective drop \(0.7\ \text{V}\)) \(\rightarrow V_o\).  
- Total diode drop: \(0.7 + 0.7 = 1.4\ \text{V}\)  
- \(V_o = 16 - 1.4 = \mathbf{14.6\ \text{V}}\)  
- Resistor connected between \(V_o\) and \(-4\ \text{V}\): voltage across resistor \(= 14.6 - (-4) = 18.6\ \text{V}\).  
- \(I = \dfrac{18.6}{4.7\times 10^3} \approx \mathbf{3.96\ \text{mA}}\)

---

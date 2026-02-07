# Assignment 3 – Diode Applications

---

## Question 1

### 1(a) Thermal Voltage at 25°C

The thermal voltage of a diode is given by:

\[
V_T = \frac{kT}{q}
\]

Where:
- \( k = 1.38 \times 10^{-23}\ \text{J/K} \) (Boltzmann constant)
- \( q = 1.602 \times 10^{-19}\ \text{C} \)
- \( T = 25^\circ C + 273 = 298\ \text{K} \)

Substituting the values:

\[
V_T = \frac{(1.38 \times 10^{-23})(298)}{1.602 \times 10^{-19}}
= 0.0257\ \text{V}
\]

\[
\boxed{V_T \approx 25.7\ \text{mV}}
\]

---

### 1(b) Diode Current Calculation

The diode current equation is:

\[
I_D = I_S \left( e^{\frac{V_D}{nV_T}} - 1 \right)
\]

Given:
- \( I_S = 40\ \text{nA} = 40 \times 10^{-9}\ \text{A} \)
- \( n = 2 \)
- \( V_D = 0.5\ \text{V} \)
- \( V_T = 0.0257\ \text{V} \)

\[
\frac{V_D}{nV_T} = \frac{0.5}{2 \times 0.0257} \approx 9.73
\]

\[
I_D = 40 \times 10^{-9} (e^{9.73} - 1)
\]

\[
I_D \approx 40 \times 10^{-9} \times 16837
\]

\[
\boxed{I_D \approx 0.67\ \text{mA}}
\]

---

## Question 2  
**Boylestad, Chapter 2 – Problem 4**

Given:
- Source voltage \( E = 30\ \text{V} \)
- Resistor \( R = 1.5\ \text{k}\Omega \)
- Silicon diode

---

### 2(a) Approximate Diode Model (\( V_D = 0.7\ \text{V} \))

\[
V_D = 0.7\ \text{V}
\]

\[
V_R = E - V_D = 30 - 0.7 = 29.3\ \text{V}
\]

\[
I_D = \frac{V_R}{R} = \frac{29.3}{1500}
\]

\[
\boxed{I_D \approx 19.53\ \text{mA}}
\]

---

### 2(b) Ideal Diode Model (\( V_D = 0\ \text{V} \))

\[
V_D = 0\ \text{V}
\]

\[
V_R = 30\ \text{V}
\]

\[
I_D = \frac{30}{1500}
\]

\[
\boxed{I_D = 20\ \text{mA}}
\]

---

### 2(c) Model Comparison

Yes, the ideal model provides a good approximation in this case.

The current difference between the two models is small (about 2.4%) because the supply voltage (30 V) is much larger than the diode forward drop (0.7 V).

---

## Question 3  
**Boylestad, Chapter 2 – Problem 5**

Using the approximate silicon diode model (\( V_D = 0.7\ \text{V} \)):

---

### (a) Reverse-Biased Configuration

The diode is reverse biased.

\[
\boxed{I = 0\ \text{A}}
\]

---

### (b) Dual-Branch Configuration

Both diodes are forward biased.

- 10 Ω branch:
\[
I_1 = \frac{20 - 0.7}{10} = 1.93\ \text{A}
\]

- 20 Ω branch:
\[
I_2 = \frac{20 - 0.7}{20} = 0.965\ \text{A}
\]

Total current:
\[
\boxed{I = 2.895\ \text{A}}
\]

---

### (c) Back-to-Back Diode Configuration

The middle branch is open due to opposing diode directions.  
Current flows only through the 10 Ω resistor.

\[
I = \frac{10}{10}
\]

\[
\boxed{I = 1\ \text{A}}
\]

---

## Question 4  
**Boylestad, Chapter 2 – Problem 11**

---

### 4(a) Parallel Si and GaAs Diodes

- Source voltage: 1 V  
- Si diode drop: 0.7 V  
- GaAs diode drop: 1.2 V  

The silicon diode conducts first and clamps the voltage.

\[
V_o = 1 - 0.7 = 0.3\ \text{V}
\]

\[
I = \frac{0.3}{1\ \text{k}\Omega}
\]

\[
\boxed{I = 0.3\ \text{mA}}
\]

---

### 4(b) Multi-Stage Silicon Diode Network

Total diode drop:
\[
0.7 + 0.7 = 1.4\ \text{V}
\]

\[
V_o = 16 - 1.4 = 14.6\ \text{V}
\]

Voltage across resistor:
\[
14.6 - (-4) = 18.6\ \text{V}
\]

\[
I = \frac{18.6}{4.7\ \text{k}\Omega}
\]

\[
\boxed{I \approx 3.96\ \text{mA}}
\]

---

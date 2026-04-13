# BJT Voltage-Divider Bias – DC Analysis

**Tool:** LTspice  
**Goal:** Analyze the DC operating point of a voltage-divider biased NPN BJT using the approximate method, then verify with simulation.

---

## Circuit Parameters

| Component | Value |
|-----------|-------|
| VCC | 18 V |
| R1 (top bias resistor) | 39 kΩ |
| R2 (bottom bias resistor) | 8.2 kΩ |
| RC (collector resistor) | 3.3 kΩ |
| RE (emitter resistor) | 1 kΩ |
| β (hFE) | 120 |
| Transistor | NPN (e.g. 2N2222) |

---

## Approximate Analysis

### Step 1 – Validity Check

The approximate method is valid when:

$$\beta R_E \geq 10 R_2$$

$$120 \times 1\,\text{k}\Omega = 120\,\text{k}\Omega \geq 10 \times 8.2\,\text{k}\Omega = 82\,\text{k}\Omega \quad \checkmark$$

---

### Step 2 – Base Voltage (V_B)

Using the voltage-divider rule:

$$V_B = \frac{R_2 \cdot V_{CC}}{R_1 + R_2} = \frac{8.2\,\text{k} \times 18}{39\,\text{k} + 8.2\,\text{k}} = \mathbf{3.13\,V}$$

---

### Step 3 – Emitter Voltage (V_E)

$$V_E = V_B - V_{BE} = 3.13 - 0.7 = \mathbf{2.43\,V}$$

---

### Step 4 – Emitter Current (I_E)

$$I_E = \frac{V_E}{R_E} = \frac{2.43}{1\,\text{k}\Omega} = \mathbf{2.43\,mA}$$

---

### Step 5 – Collector Current (I_C)

$$I_C \approx I_E = \mathbf{2.43\,mA}$$

---

### Step 6 – Collector-to-Emitter Voltage (V_CE)

$$V_{CE} = V_{CC} - I_C(R_C + R_E) = 18 - 2.43\,\text{m} \times 4.3\,\text{k} = \mathbf{7.55\,V}$$

---

### Step 7 – Base Current (I_B)

$$I_B = \frac{I_C}{\beta} = \frac{2.43\,\text{mA}}{120} = \mathbf{20.25\,\mu A}$$

---

### Step 8 – Collector Voltage (V_C)

$$V_C = V_{CC} - I_C \cdot R_C = 18 - 2.43\,\text{m} \times 3.3\,\text{k} = \mathbf{9.98\,V}$$

---

## Summary of Results

| Parameter | Calculated | LTspice Simulation |
|-----------|-----------|--------------------|
| V_B | 3.13 V | |
| V_E | 2.43 V | |
| V_C | 9.98 V | |
| V_CE | 7.55 V | |
| I_C | 2.43 mA | |
| I_E | 2.43 mA | |
| I_B | 20.25 µA | |

> Fill in the **LTspice Simulation** column after running `.op` analysis.

---

## LTspice Schematic

The `.asc` schematic file is included in this repository.

**To run the simulation:**
1. Open the `.asc` file in LTspice
2. Run a **DC Operating Point** (`.op`) simulation
3. View node voltages and branch currents in the SPICE log (`View → SPICE Error Log`)
4. Compare results with the calculated values above

**Schematic overview:**

```
        +18V
          |
        [R1 = 39kΩ]
          |
VB -------+-------- B
          |         |
        [R2 =      NPN (β=120)
         8.2kΩ]     |
          |         C ---- [RC = 3.3kΩ] ---- +18V
         GND        |
                    E
                    |
                 [RE = 1kΩ]
                    |
                   GND
```

---

## Key Observations

- The **approximate method** is valid because `βRE = 120 kΩ ≥ 10R2 = 82 kΩ`
- The Q-point (`IC`, `VCE`) is **independent of β** in this configuration — a major advantage of voltage-divider biasing
- The transistor is in the **active region** since `VCE = 7.55 V > 0.2 V` and `VBE ≈ 0.7 V`

---

## Files

| File | Description |
|------|-------------|
| `voltage_divider_bias.asc` | LTspice schematic |
| `waveform_op.png` | Screenshot of `.op` simulation results |
| `README.md` | This file |

# EFA8100-3004 – Op-Amp Circuits (LTspice Lab)

**Course:** EFA8100-3004  
**Tool:** LTspice  
**Submission:** LTspice schematic files (`.asc`) + screenshots of waveforms  
**Goal:** Understand op-amp behaviors — open-loop comparator, non-inverting amplifier, inverting amplifier

---

## Table of Contents

- [Task 1 – Open-Loop Op-Amp (Comparator)](#task-1--open-loop-op-amp-comparator)
- [Task 2 – Non-Inverting Amplifier](#task-2--non-inverting-amplifier)
- [Task 3 – Inverting Amplifier](#task-3--inverting-amplifier)
- [Files](#files)

---

## Task 1 – Open-Loop Op-Amp (Comparator)

### Circuit Setup

| Parameter | Value |
|-----------|-------|
| Supply | ±5 V |
| Vin | SINE(0 10m 1k) — 10 mV amplitude, 1 kHz |
| (+) input | Vin |
| (−) input | GND |
| Feedback | None |
| Simulation | `.tran 10ms` |

### Schematic Overview

```
       +5V                    
        |             
       [V1]    Vin ---(+)              Vout
               GND ---(−)   [µA741] ---o
                             |
       −5V                  GND
        |
       [V2]
        |
       GND
```

### Theory

With no feedback, the op-amp applies its full open-loop gain (~200,000 for µA741):

$$V_{out} = A_{OL} \times V_{in} = 200{,}000 \times 10\,\text{mV} = 2000\,\text{V}$$

This far exceeds ±5 V, so the output immediately saturates at the supply rails.

### Observed Behavior

- Input: 10 mV sine wave at 1 kHz
- Output: Square wave switching between **+5 V** and **−5 V**
- The op-amp acts as a **1-bit comparator**: Vout = +Vs when V+ > V−, and −Vs when V+ < V−

### Waveform Screenshot

![Task 1 Waveform](screenshots/task1_comparator.png)

---

## Task 2 – Non-Inverting Amplifier

### Circuit Setup

| Parameter | Value |
|-----------|-------|
| Supply | ±5 V |
| Vin | SINE(0 10m 1k) |
| (+) input | Vin |
| Rg | 10 kΩ — from (−) to GND |
| Rf | 90 kΩ — from Vout to (−) |
| RL | 1 kΩ (load) |
| Op-Amp | LT6016 |
| Simulation | `.tran 10ms` |

### Schematic Overview

```
              Rf = 90k
       +-----/\/\/------+
       |                |
Vin ---(+)            Vout ---[RL 1k]--- GND
       (−)--- [LT6016]
        |
      [Rg = 10k]
        |
       GND
```

### Theory

The closed-loop gain for a non-inverting configuration:

$$A_v = 1 + \frac{R_f}{R_g} = 1 + \frac{90\,\text{k}}{10\,\text{k}} = \mathbf{+10}$$

Expected output amplitude:

$$V_{out} = 10 \times 10\,\text{mV} = \mathbf{100\,mV}$$

### Observed Behavior

- Gain ≈ **+10** (verified from waveform amplitude ratio)
- **No phase inversion** — output is in phase with input
- Output is a clean sine wave (no clipping, within ±5 V rails)

### Waveform Screenshot

![Task 2 Waveform](screenshots/task2_noninverting.png)

---

## Task 3 – Inverting Amplifier

### Circuit Setup

| Parameter | Value |
|-----------|-------|
| Supply | ±5 V |
| Vin | SINE(0 10m 1k) |
| (+) input | GND |
| Rin (R1) | 10 kΩ — from Vin to (−) |
| Rf | 90 kΩ — from Vout to (−) |
| RL | 1 kΩ (load) |
| Op-Amp | LT6016 |
| Simulation | `.tran 10ms` |

### Schematic Overview

```
         Rin = 10k       Rf = 90k
Vin ---[/\/\/]---+---[/\/\/]--- Vout ---[RL 1k]--- GND
                 |
                (−)
                (+) --- GND
               [LT6016]
```

### Theory

The closed-loop gain for an inverting configuration:

$$A_v = -\frac{R_f}{R_{in}} = -\frac{90\,\text{k}}{10\,\text{k}} = \mathbf{-9}$$

Expected output amplitude:

$$V_{out} = -9 \times 10\,\text{mV} = \mathbf{-90\,mV}$$

### Observed Behavior

- Gain ≈ **−9** (verified from waveform amplitude ratio)
- **180° phase inversion** — output is inverted relative to input
- Output is a clean sine wave (no clipping, within ±5 V rails)

### Waveform Screenshot

![Task 3 Waveform](screenshots/task3_inverting.png)

---

## Summary Comparison

| Feature | Task 1: Open-Loop | Task 2: Non-Inverting | Task 3: Inverting |
|---------|-------------------|-----------------------|-------------------|
| Feedback | None | Negative | Negative |
| Gain | ~∞ (saturates) | +10 | −9 |
| Phase shift | 0° (clips to square) | 0° | 180° |
| Output shape | Square wave | Sine wave | Sine wave |
| Use case | Comparator | Signal amplifier | Signal amplifier |

---

## Files

| File | Description |
|------|-------------|
| `task1_comparator.asc` | LTspice schematic – Open-loop comparator |
| `task2_noninverting.asc` | LTspice schematic – Non-inverting amplifier |
| `task3_inverting.asc` | LTspice schematic – Inverting amplifier |
| `screenshots/task1_comparator.png` | Waveform screenshot – Task 1 |
| `screenshots/task2_noninverting.png` | Waveform screenshot – Task 2 |
| `screenshots/task3_inverting.png` | Waveform screenshot – Task 3 |
| `README.md` | This file |

---

## How to Run

1. Open any `.asc` file in **LTspice**
2. Press **Run** (the running man icon) — simulation is pre-configured as `.tran 10ms`
3. Click on the **Vin** and **Vout** wires to plot both waveforms
4. Use **Ctrl+click** on a waveform label to change its color for clarity
5. Take a screenshot and save it to the `screenshots/` folder

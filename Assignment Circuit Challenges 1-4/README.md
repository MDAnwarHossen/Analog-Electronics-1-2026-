# Transistors & Capacitors – DC and AC Applications Lab

**Course:** The Art of Doing: Electronics For Everyone  
**Supply:** 9V Battery (Ansmann Industrial Alkaline)  
**Goal:** Understand transistor switching, biasing, RC filters, and audio amplification using real breadboard circuits

---

## Table of Contents

- [Lab Overview](#lab-overview)
- [Circuit 1 – Basic LED & Resistor](#circuit-1--basic-led--resistor)
- [Circuit 2 – Transistor Switch (Touch Trigger)](#circuit-2--transistor-switch-touch-trigger)
- [Circuit 3 – Transistor Switch with Push Button & Capacitor](#circuit-3--transistor-switch-with-push-button--capacitor)
- [Circuit 4 – Common Emitter Transistor Amplifier](#circuit-4--common-emitter-transistor-amplifier)
- [Key Concepts](#key-concepts)
- [Parts Used](#parts-used)
- [Lab Photos](#lab-photos)

---

## Lab Overview

This lab covers two main areas:

**DC Applications** — Using transistors as switches, controlling LEDs with small base currents, and exploring capacitor timing behavior.

**AC Applications** — Building a common emitter amplifier biased for 9V supply, using coupling and bypass capacitors, and understanding how RC filters shape AC signals.

---

## Circuit 1 – Basic LED & Resistor

### Components
| Component | Value |
|-----------|-------|
| Supply | 9V battery |
| Resistor | ~330 Ω |
| LED | Red (5mm) |
| Capacitor | Small electrolytic (for timing) |

### Circuit Description
A simple series circuit: 9V → resistor → LED → GND. The resistor limits current to a safe level for the LED (~20 mA).

```
+9V --- [R = 330Ω] --- [LED] --- GND
```

### Current Calculation

$$I = \frac{V_{cc} - V_{LED}}{R} = \frac{9 - 2}{330} \approx 21\,\text{mA}$$

### Observed Behavior
- LED glows brightly at safe current level
- Removing or increasing the resistor risks burning out the LED

---

## Circuit 2 – Transistor Switch (Touch Trigger)

### Components
| Component | Value |
|-----------|-------|
| Supply | 9V battery |
| Transistor | PN2222 NPN |
| Collector Resistor | 330 Ω |
| LED | Red (5mm) |
| Base Resistor | 10 kΩ |

### Circuit Description

A transistor wired as a switch. A small current at the base (from touching the wire with a finger) is enough to trigger a large collector current, turning on the LED.

```
+9V --- [RC = 330Ω] --- Collector
                        |
                      [NPN]  <--- Base (finger touch / wire)
                        |
                      Emitter --- GND

LED connected: Collector --> [LED] --> GND
```

### How It Works

The human body acts as a resistor (~1 MΩ), providing a tiny base current (μA range). The transistor amplifies this by β (≈100), producing mA-level collector current — enough to light the LED.

$$I_C = \beta \times I_B \approx 100 \times 10\,\mu A = 1\,\text{mA}$$

### Observed Behavior
- LED is **OFF** with no finger contact
- LED turns **ON** when finger touches the base wire
- Demonstrates transistor as a current-controlled switch

---

## Circuit 3 – Transistor Switch with Push Button & Capacitor

### Components
| Component | Value |
|-----------|-------|
| Supply | 9V battery |
| Transistor | PN2222 NPN |
| Push Button | Tactile switch |
| Capacitor | Electrolytic (timing) |
| Resistors | 10 kΩ base, 330 Ω collector |
| LED | Red |

### Circuit Description

Adding a push button to the base path and a capacitor to observe timing/debounce behavior. When the button is pressed, the capacitor charges through the base resistor and triggers the transistor.

```
+9V --- [R1=10kΩ] ---+--- [Button] --- Base
                     |
                    [C] (charges/discharges)
                     |
                    GND

Collector: +9V --- [RC=330Ω] --- [LED] --- Collector --- Emitter --- GND
```

### Observed Behavior
- LED turns on when button is pressed
- Capacitor introduces a brief delay (RC time constant) in the switch response
- Demonstrates how capacitors can control timing in switching circuits

---

## Circuit 4 – Common Emitter Transistor Amplifier

### Design Parameters

| Parameter | Value |
|-----------|-------|
| VCC | 9 V |
| Target IC | 1 mA |
| β (Beta) | 100 |
| Ve target | ≈ 1/10 × VCC = 1 V |

### Component Values (Calculated)

| Component | Calculated | Used |
|-----------|-----------|------|
| Re (emitter) | 1 kΩ | 1 kΩ (brown, black, black, brown) |
| Rc (collector) | 4.5 kΩ | 2× 2 kΩ in series |
| R2 (bias to GND) | 17 kΩ | 10K + 5.1K + 2K in series |
| R1 (bias from VCC) | 66 kΩ | 47K + 10K + 10K in series |
| C1 (input coupling) | 100 µF | 100 µF electrolytic |
| C2 (output coupling) | 100 µF | 100 µF electrolytic |
| C3 (emitter bypass) | 100 µF | 100 µF electrolytic |

### Design Derivations

**Step 1 — Emitter Resistor (Re):**

$$R_e = \frac{V_e}{I_e} = \frac{1\,V}{1\,\text{mA}} = 1\,\text{k}\Omega$$

**Step 2 — Base Current:**

$$I_b = \frac{I_c}{\beta} = \frac{1\,\text{mA}}{100} = 0.01\,\text{mA}$$

**Step 3 — Bias Voltages:**

$$V_2 = V_e + 0.7\,V = 1 + 0.7 = 1.7\,V$$
$$V_1 = V_{cc} - V_2 = 9 - 1.7 = 7.3\,V$$

**Step 4 — Bias Resistors (stiff divider: I₂ = 10·Ib, I₁ = 11·Ib):**

$$R_2 = \frac{V_2}{I_2} = \frac{1.7\,V}{0.1\,\text{mA}} \approx 17\,\text{k}\Omega$$
$$R_1 = \frac{V_1}{I_1} = \frac{7.3\,V}{0.11\,\text{mA}} \approx 66\,\text{k}\Omega$$

**Step 5 — Collector Resistor (Rc):**

$$V_c = \frac{V_{cc}}{2} = 4.5\,V \quad \Rightarrow \quad R_c = \frac{V_c}{I_c} = \frac{4.5\,V}{1\,\text{mA}} = 4.5\,\text{k}\Omega$$

### AC Gain

Without bypass capacitor:

$$A_v = \frac{R_c}{R_e} = \frac{4000}{1000} = 4\times$$

With bypass capacitor C3 (shorts Re for AC):

$$A_v \approx \frac{R_c}{r_e'} \gg 4\times \quad \text{(much higher gain for AC signals)}$$

### Schematic Overview

```
           R1(66k)   Rc(4.5k)
+9V ---+---[/\/\/]---+---[/\/\/]---+--- +9V
       |             |             |
       |           Base          Collector
       |      C1   |               |   C2
Vin --[||]---+---> NPN          Vout--[||]--> 
             |      |               
           R2(17k)  Emitter       
             |      |   
            GND   [Re=1k] // [C3=100µF]
                    |
                   GND
```

### Observed Behavior

| Stage | DC Voltage | AC Behavior |
|-------|-----------|-------------|
| Base (VB) | ≈ 1.7 V | AC signal from microphone |
| Emitter (VE) | ≈ 1.0 V | Stable DC bias |
| Collector (VC) | ≈ 4.5 V | Amplified inverted AC output |
| Output (Vout) | 0 V DC (blocked) | Amplified audio signal |

- C1 and C2 are **coupling capacitors** — block DC, pass AC
- C3 is a **bypass capacitor** — shorts Re for AC, dramatically increasing gain
- LED connected to second transistor switch stage lights up with sound

---

## Key Concepts

### Transistor Operating Regions

| Region | VBE | Behavior |
|--------|-----|---------|
| Cutoff | < 0.7 V | Transistor OFF, no collector current |
| Active | ≈ 0.7 V | Linear amplification (IC = β × IB) |
| Saturation | >> 0.7 V | Transistor fully ON |

### Capacitor Roles in the Amplifier

| Capacitor | Role | Effect |
|-----------|------|--------|
| C1 (input) | Coupling | Blocks DC bias from signal source |
| C2 (output) | Coupling | Blocks DC collector voltage from load |
| C3 (emitter) | Bypass | Shorts Re for AC → higher gain |

### RC Filter Summary

$$f_{cutoff} = \frac{1}{2\pi RC}$$

| Filter Type | Passes | Blocks |
|-------------|--------|--------|
| Low Pass (R then C to GND) | Low frequencies | High frequencies |
| High Pass (C in series, R to GND) | High frequencies | Low frequencies |

---

## Parts Used

| Component | Value / Part | Qty |
|-----------|-------------|-----|
| NPN Transistor | PN2222 | 2 |
| Resistors | 330Ω, 2kΩ×2, 5.1kΩ, 10kΩ×3, 47kΩ | assorted |
| Capacitors | 100µF electrolytic | 3 |
| Electrolytic Capacitor | 1µF, timing | 1 |
| LED | Red 5mm | 1 |
| Push Button | Tactile | 1 |
| 9V Battery | Ansmann Industrial Alkaline | 1 |
| Breadboard | Standard + large | 1 |
| Jumper Wires | Assorted | many |

---

## Lab Photos

### Circuit 1 – Basic LED & Resistor
![LED Resistor Circuit](photos/circuit1_led_resistor.jpg)

### Circuit 2 – Touch-Triggered Transistor Switch
| State | Photo |
|-------|-------|
| OFF (no touch) | ![Switch OFF](photos/circuit2_touch_off.jpg) |
| ON (finger on base) | ![Switch ON](photos/circuit2_touch_on.jpg) |

### Circuit 3 – Push Button Switch with Capacitor
| Angle 1 | Angle 2 |
|---------|---------|
| ![Button Circuit 1](photos/circuit3_button_a.jpg) | ![Button Circuit 2](photos/circuit3_button_b.jpg) |

### Circuit 4 – Transistor Amplifier
| View | Photo |
|------|-------|
| Full board | ![Amplifier Full](photos/circuit4_amplifier_full.jpg) |
| Detail | ![Amplifier Detail](photos/circuit4_amplifier_detail.jpg) |

> Replace filenames with your actual photo filenames after uploading to GitHub.

---

## How to Recreate

1. Build Circuit 1 first to verify your power supply and LED polarity are correct
2. Add the transistor for Circuit 2 — confirm LED turns on only when base is triggered
3. Add the push button and capacitor for Circuit 3 to observe timing
4. Build Circuit 4 step by step: place transistor → add Re → add R1/R2 bias → add Rc → add coupling capacitors → add bypass capacitor
5. Optionally connect a microphone as the AC input source to test audio amplification

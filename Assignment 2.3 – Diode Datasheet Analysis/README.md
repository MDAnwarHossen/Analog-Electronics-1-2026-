# README.md

## Diode
**1N4148 – Small‑signal fast switching silicon diode**

## Manufacturer
Vishay Semiconductor (also manufactured by Nexperia and others)

## Real application (explained)
The 1N4148 is commonly used in **high‑speed signal switching and protection** circuits. Its internal construction results in low junction capacitance and fast reverse recovery, which allows it to respond quickly to changing voltages without significantly distorting digital or pulse signals. Typical uses include logic‑level signal steering, diode‑OR gates, clamping negative transients on microcontroller inputs, and pulse shaping in timing circuits.

---

## Datasheet link
Manufacturer datasheet (PDF):  
https://www.vishay.com/docs/81857/1n4148.pdf

---

## Technical explanation (no copy‑paste)

### Forward voltage (VF)
The forward voltage is the voltage drop that appears across the diode when current flows through it. For the 1N4148, when a small signal current on the order of **10 mA** flows, the diode drops roughly **0.7–1.0 V**. This drop is important because it determines how much voltage remains for other components (such as series resistors or logic inputs). Designers should always assume the higher end of this range to ensure the circuit still works under worst‑case conditions and elevated temperatures.

### Maximum reverse voltage
The maximum reverse voltage specifies how much voltage the diode can block when it is reverse‑biased. In practice, this tells you whether the diode can safely withstand negative or opposite‑polarity voltages in your circuit. The 1N4148 is suitable for signal‑level voltages and moderate transients, but it is **not** intended for high‑voltage rectification (such as mains power).

### Maximum forward current
This value limits how much current the diode can safely conduct without overheating. The 1N4148 is a **small‑signal** diode, meaning it is designed for brief pulses or relatively low continuous currents. Even if short current spikes are allowed, sustained high current will raise the junction temperature and can permanently damage the diode. When designing, the forward current should be chosen so that power dissipation (current × forward voltage) stays well within safe thermal limits.

### Operating temperature range
The operating and storage temperature range indicates the environmental conditions under which the diode remains reliable. While the 1N4148 can operate across a wide temperature range, higher temperatures increase leakage current and reduce safe current limits. For reliable designs, engineers typically derate the current at higher ambient temperatures to keep the junction temperature safely below its maximum.

---

## Design insight
Choose the 1N4148 when you need **speed and signal integrity**, not power handling. If your priority is lower forward voltage, a Schottky diode may be better. If you need higher current or voltage handling, a power rectifier diode is more appropriate.


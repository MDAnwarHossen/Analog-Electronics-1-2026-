# 12V DC Input Protection Circuit

This project demonstrates a simple **Reverse Polarity Protection** circuit using a **1N5819 Schottky Diode**. The goal is to protect downstream components from damage if the 12V DC power supply is connected with incorrect polarity.

---

## 1. Schematic and Simulation

The circuit consists of:

- A 12V DC source  
- A series-connected **1N5819 diode**  
- A `$1k\Omega$` load resistor  

### Circuit Schematic

*(Insert schematic image here)*

### Operating Point Simulation

*(Insert simulation image or data here)*

---

## 2. Component Justification: 1N5819 Schottky Diode

For a 12V DC application, the **1N5819** was selected over standard silicon diodes (like the 1N4007) for its superior efficiency and safety margins.

### Voltage Rating

- Maximum Repetitive Reverse Voltage (`V_RRM`): **40V**  
- Safety Buffer: Over 3× the operating voltage ensures the diode effectively blocks current without breakdown if the input is reversed.

### Current Rating

- Maximum Average Forward Current (`I_F(AV)`): **1.0A**  
- Simulation Current Draw: **11.79 mA**  
- Headroom: The diode operates at roughly **1.2%** of its capacity, allowing it to handle heavier loads or transient spikes without overheating.

### Efficiency (Forward Voltage Drop)

- Standard silicon diodes drop ~0.7V  
- **1N5819 Forward Voltage Drop**: Only **0.211V**, resulting in an output of **11.789V**  
- Benefit: Maximizes voltage delivery to the load and minimizes power dissipation within the diode.

### Cost & Availability

- The 1N5819 is a **“jellybean” component**:  
  - Widely available  
  - Stocked by all major electronics distributors  
  - Costs only a few cents per unit  
- Economically ideal for mass-produced protection circuits.

---


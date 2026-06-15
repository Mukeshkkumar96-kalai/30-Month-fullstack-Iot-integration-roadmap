# 📘 Day 15 – Week 3 | Series & Parallel Circuits

**Roadmap Phase:** Electronics & Hardware Foundations
**Topic:** Series & Parallel Circuits

---

## 1. 📖 What I Learned Today

- **Series circuits** have one single path for current. All electrons travel through every component in sequence.
- **Parallel circuits** have multiple branches. Each branch gets the full supply voltage independently.
- **Ohm's Law** is the foundation of all circuit calculations: `V = I × R`
- In a series circuit, **voltage splits** across components but **current is the same** everywhere.
- In a parallel circuit, **voltage is the same** across all branches but **current splits** across each branch.
- Total resistance in series: `R_total = R1 + R2 + ... + Rn` (increases)
- Total resistance in parallel: `1/R_total = 1/R1 + 1/R2` (decreases)
- Current in parallel does **not** split equally by default — it splits based on the resistance of each branch (`I = V ÷ R` per branch).
- In a multi-sensor parallel bus, total supply current = sum of all branch currents.

---

## 2. ⚠️ Problems Faced

| # | Problem | Where I Got Stuck |
|---|---------|-------------------|
| 1 | Assumed parallel current splits equally across branches | Did not account for different resistor values per branch |
| 2 | Confused about why resistors are present in the parallel circuit diagram | Thought resistors were always required in every parallel branch |
| 3 | Did not immediately see the LED burn risk in a parallel circuit without per-branch resistors | Needed to connect Ohm's Law to component current ratings |

---

## 3. ✅ Issues Fixed / Concepts Clarified

**Problem 1 — Parallel current split:**
Current does not split equally unless resistances are equal.
Each branch is independent: `I_branch = V_supply ÷ R_branch`

**Problem 2 — Resistors in parallel branches:**
Resistors are only required in a branch if the component cannot limit its own current.
- LED → always needs a series resistor (no internal current limiting)
- DHT22, ESP32 modules → have internal regulation, no external resistor needed
- Raw resistive sensor (soil probes) → needs a series resistor to form a voltage divider

**Problem 3 — LED burn risk:**
An LED has a max current rating (typically 20mA).
Connecting it directly across 5V without a resistor causes it to draw far more than 20mA → immediate burnout.
Fix: calculate and add a series resistor per branch.

---

## 4. 🧮 Calculations

### Series circuit example (9V supply, R1 = R2 = 100Ω)
```
R_total = 100 + 100 = 200Ω
I       = 9V ÷ 200Ω = 0.045A = 45mA  (same throughout)
V_R1    = 45mA × 100Ω = 4.5V
V_R2    = 45mA × 100Ω = 4.5V
Check   : 4.5 + 4.5 = 9V ✓
```

### Parallel circuit example (9V supply, R1 = R2 = 100Ω)
```
R_total      = 1 ÷ (1/100 + 1/100) = 50Ω
I_total      = 9V ÷ 50Ω = 0.09A = 90mA
I_branch1    = 9V ÷ 100Ω = 45mA
I_branch2    = 9V ÷ 100Ω = 45mA
Check        : 45 + 45 = 90mA ✓
```

### Checkpoint problem — multi-sensor parallel bus (5V supply)
```
Sensor 1 = 30mA
Sensor 2 = 45mA
Sensor 3 = 60mA
I_total  = 30 + 45 + 60 = 135mA

Safety margin (×1.25): 135 × 1.25 = 168.75mA → minimum 169mA rated supply
```
---

## 5. 📚 Topic Explanation — Series & Parallel Circuits

### What is a circuit?
A circuit is a closed loop that allows electrons to flow from a power source, through components, and back. Voltage (V) is the pressure driving electrons. Resistance (R) is opposition to flow. Current (I) is the resulting flow rate. All three are related by **Ohm's Law: V = I × R**.

### Series circuit
All components are connected end-to-end in a single loop. There is only one path for current.

Key rules:
- Current is identical at every point in the loop
- Total voltage = sum of voltage drops across each component
- Total resistance increases with each component added
- If one component fails (open circuit), the entire circuit stops

Real-world use: voltage dividers for analog sensors (soil moisture, thermistors).

### Parallel circuit
Components are connected across the same two nodes, giving each its own independent path.

Key rules:
- Voltage is identical across every branch
- Each branch draws current independently based on its own resistance
- Total current = sum of all branch currents
- Total resistance decreases as more branches are added
- If one branch fails, all other branches continue operating

Real-world use: powering multiple sensors and microcontrollers from a single battery bus in a field deployment.

### Why this matters for IoT
In a smart agricultural sensor network:
- **Parallel power distribution** ensures a failed sensor does not take down the whole network
- **Series voltage dividers** are the core mechanism for reading analog resistive sensors on an ESP32 ADC pin
- **Power budget calculations** (total parallel current × safety margin) determine battery and solar panel sizing for off-grid deployments

---

## 🔗 Resources

- [Ohm's Law — All About Circuits](https://www.allaboutcircuits.com/textbook/direct-current/chpt-2/voltage-current-resistance-relate/)
- [Resistor color code calculator](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-resistor-color-code)
- [ESP32 ADC reference](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/peripherals/adc.html)

---

## 📅 Next Session

**Day 16 – Week 3 (Wednesday):** Practice exercises — voltage divider circuits and Ohm's Law problems.
**Pending homework:** Complete agricultural sensor node battery life calculation and get mentor confirmation.

---

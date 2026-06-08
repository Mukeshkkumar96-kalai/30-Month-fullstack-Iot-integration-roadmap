# Day 8 — Week 2: Ohm's Law & Calculations

## What I Learned Today

### 1. Ohm's Law from First Principles

Ohm's Law describes the relationship between three fundamental electrical quantities:

```
V = I × R
I = V / R
R = V / I
```

| Symbol | Quantity | Unit | Analogy |
|--------|----------|------|---------|
| V | Voltage | Volts (V) | Water pressure |
| I | Current | Amperes (A) | Flow rate |
| R | Resistance | Ohms (Ω) | Pipe friction |

**At the electron level:** Voltage is electromotive force that pushes free electrons through a conductor. Current is the rate of electron flow (1A = 6.24 × 10¹⁸ electrons/second). Resistance is opposition from atomic collisions, which generates heat.

### 2. LED Resistor Calculation

An LED has a forward voltage (V_f) that it consumes regardless of supply voltage. A current-limiting resistor absorbs the remainder.

**Formula:**
```
R = (Vcc - V_f) / I_f
```

**Example — Red LED on ESP32 (3.3V system):**
```
R = (3.3 - 2.0) / 0.010
R = 1.3 / 0.010
R = 130 Ω  ← standard E24 value
```

**LED forward voltage reference:**

| Color | V_f (typical) | Max Current | Notes |
|-------|--------------|-------------|-------|
| Red | 1.8 – 2.2 V | 20 mA | Most common |
| Orange / Yellow | 2.0 – 2.2 V | 20 mA | Similar to red |
| Green | 2.0 – 3.5 V | 20 mA | Wide range — check datasheet |
| Blue / White | 3.0 – 3.5 V | 20 mA | ⚠ Critical on 3.3V systems |

**Blue/White LED trap:** V_f is close to or equal to ESP32 GPIO output (3.3V). Solution: drive from 5V pin via transistor, or use a dedicated LED driver IC.

---

## Key Formulas — Quick Reference

```
Ohm's Law:        V = I × R
Current:          I = V / R
Resistance:       R = V / I
Power:            P = V × I = V² / R = I² × R

LED resistor:     R = (Vs − Vf) / If
Voltage divider:  V_out = Vcc × R1 / (R1 + R_soil)
Soil resistance:  R_soil = R1 × (Vcc − V_out) / V_out
```

---

## Common Mistakes to Avoid

| Mistake | Why It Fails | Fix |
|---------|-------------|-----|
| Connecting LED directly to power | Near-zero resistance → current surge → LED burns out | Always use a current-limiting resistor |
| Confusing voltage and current | Voltage is pressure; current is what kills components | Calculate I = V/R and check against datasheet |
| No pull-up/pull-down on GPIO pins | Floating pins pick up noise → false sensor readings | Add 10 kΩ pull-up or pull-down resistor |
| DC current continuously through soil probes | Electrolytic corrosion dissolves probes over weeks | Pulse sensor for 10ms per reading via GPIO control |
| Blue LED on 3.3V with no headroom check | V_f ≈ Vcc → resistor has nothing to drop → LED burns | Drive from 5V or use transistor/LED driver |

---

## Practice Tasks for this week

**Wednesday (Practice):**
- [ ] Wire a 9V battery + 470Ω resistor + LED on breadboard
- [ ] Calculate expected current *before* powering on: `I = (9 - 2.0) / 470 = 14.9 mA`
- [ ] Measure with multimeter. Does it match?

**Thursday (Build):**
- [ ] Wire voltage divider circuit: `3.3V → 10kΩ → ADC pin → soil probe → GND`
- [ ] Read ADC values from dry soil and wet soil
- [ ] Record both values — these become your calibration range
- [ ] Map ADC range to 0–100% moisture percentage in code

---

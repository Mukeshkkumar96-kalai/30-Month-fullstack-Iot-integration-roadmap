# LED Circuit Project

A simple 3-LED series circuit built to practice Ohm's Law and basic breadboard wiring.
This is part of a 730-day learning journey toward IoT and embedded systems.
- Add the photo and overview section

🔗 [View Documentation Website](https://github.com/Mukeshkkumar96-kalai/Fullstack-practice/blob/main/led.html)

---

## Theory

A series circuit has a single current path — current is the same through every component, while voltage divides across each one.
To protect the LEDs from excess current, a resistor is needed. The required resistor value is calculated using Ohm's Law:

## Implementation

| Component   | Value          | Purpose           |
|-------------|----------------|-------------------|
| Resistor    | 470 Ω          | Current limiting  |
| LED x 3     | 2V, 20mA (max) | Visual output     |
| Battery     | 9V DC          | Power supply      |
| Breadboard  | 830 tie-points | Prototyping       |

The 3 LEDs and 1 resistor are connected in series with the 9V battery, forming a single loop on the breadboard.

---

## Measurements

```
R = (Vs - Vf) / If
R = (9 - 2) / 0.015
R = 466.67 Ω

Standard resistor used: 470 Ω
```

Running at 15mA (instead of the 20mA max) was chosen for safety and to extend LED lifespan.

---

## Lessons Learned

1. **Series circuits have a single current path** — one open connection kills all LEDs.
2. **Resistors are never optional** — without one, current can be ~70x the LED's rated maximum, causing instant failure.
3. **Voltage divides in series, current stays constant** — 3 × 2V = 6V across the LEDs, remaining 3V across the resistor.
4. **Always calculate R before connecting power** — `R = (Vs - Vf) / If`

---

## Next Steps

- Use a separate resistor for each LED so one failure doesn't affect the others
- Control LEDs remotely via ESP32 + Arduino C++ (Week 10)
- Build a REST API to control LEDs via Node.js (Week 15)
---

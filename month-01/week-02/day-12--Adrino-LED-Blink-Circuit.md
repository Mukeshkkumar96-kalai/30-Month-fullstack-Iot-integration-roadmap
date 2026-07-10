# Arduino LED Blink Circuit

A simple LED blink circuit built using Arduino Uno and Tinkercad simulator.

---

## Objective

To light up an LED using Arduino Uno by:
- Building the correct circuit with a resistor
- Writing Arduino code to blink the LED every 1 second

---

## Theory

An LED (Light Emitting Diode) needs two things to work safely:

1. **Correct polarity** — Long leg (Anode) connects to positive, Short leg (Cathode) connects to GND
2. **Current limiting resistor** — Without it, too much current flows and the LED burns out

An LED typically uses around **2V** and runs safely at **20mA**. Since Arduino outputs **5V**, a resistor is needed to handle the extra voltage.

**Ohm's Law formula used:**

```
R = V / I
```

---

## Circuit Diagram

```
Arduino Pin 13 → Resistor (180Ω) → LED (Anode) → LED (Cathode) → GND
```

**Components used:**

| Component     | Value       |
|---------------|-------------|
| Arduino Uno   | -           |
| LED           | Red         |
| Resistor      | 180Ω        |

---

## Calculations

Finding the resistor value using Ohm's Law:

```
Supply Voltage     = 5V
LED Forward Voltage = 2V
Voltage across Resistor = 5V - 2V = 3V

Safe LED Current = 20mA = 0.02A

R = V / I
R = 3 / 0.02
R = 150Ω (calculated)
```

**Chosen resistor: 180Ω**
> 180Ω was chosen over 150Ω because higher resistance means lower current, which gives the LED a longer life. The LED is slightly dimmer but much safer.

---

## Implementation

**Arduino Code:**

```cpp
void setup() {
  pinMode(13, OUTPUT);
}

void loop() {
  digitalWrite(13, HIGH);
  delay(1000);
  digitalWrite(13, LOW);
  delay(1000);
}
```

**Code explanation:**

- `pinMode(13, OUTPUT)` — sets pin 13 as output, runs once on startup
- `digitalWrite(13, HIGH)` — turns LED ON (sends 5V to pin 13)
- `delay(1000)` — waits 1 second (1000 milliseconds)
- `digitalWrite(13, LOW)` — turns LED OFF (sends 0V to pin 13)
- The `loop()` function repeats this forever

---

## Measurements

| Parameter         | Expected  | Observed       |
|-------------------|-----------|----------------|
| Supply Voltage    | 5V        | 5V             |
| Resistor Value    | 180Ω      | 180Ω           |
| Blink Interval    | 1 second  | 1 second       |
| LED State         | Blinking  | Blinking ✅    |

---

## Problems Faced

1. **LED not glowing at first** — LED was connected in reverse (Cathode to positive side)
2. **Code not running** — `pinmode` was typed instead of `pinMode` (case sensitive mistake)
3. **Confusing 5V pin with digital pin** — Initially tried to connect LED to 5V pin directly without understanding the difference

---

## Debugging Process

1. **Reversed LED fix** — Swapped the legs so long leg (Anode) goes toward Pin 13
2. **Case sensitivity fix** — Corrected `pinmode` → `pinMode` and `OUTPUT` keyword spelling
3. **Resistor calculation** — Used Ohm's Law to calculate correct resistor value instead of guessing

---

## Lessons Learned

- Always use a resistor with an LED — never connect directly to power
- Arduino is **case sensitive** — `pinMode` and `digitalWrite` must be spelled exactly right
- The resistor can go before or after the LED in a series circuit — current is the same either way
- `void setup()` runs once, `void loop()` runs forever
- Higher resistance = safer LED, lower resistance = brighter but shorter life
- Pin 13 has a built-in LED on the Arduino Uno board — useful for testing

---

## Next Steps

- [ ] Make the LED blink 3 times fast, then pause for 2 seconds
- [ ] Control 2 LEDs on Pin 13 and Pin 12 with different blink speeds
- [ ] Try different resistor values and observe brightness difference
- [ ] Deploy circuit simulation link via Tinkercad share

---

## Tools Used and simulation link

- [Tinkercad](https://www.tinkercad.com/things/2cZS9pZUWi7/editel?returnTo=%2Fdashboard) — Online circuit simulator link
- Arduino Uno (simulated)

---

*Built as part of a 24-month IoT + Full Stack learning roadmap.*

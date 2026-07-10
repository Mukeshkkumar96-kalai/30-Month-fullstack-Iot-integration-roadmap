# Potentiometer-Controlled LED Brightness

## 1. Today's Learning

Built a circuit where turning a potentiometer knob smoothly changes an LED's brightness. This combined two new ideas at once:
- Reading an **analog input** (`analogRead`) from a potentiometer
- Producing an **analog-like output** (`analogWrite` / PWM) to control LED brightness

**Components used:** potentiometer, LED, 220Ω resistor, Arduino Uno.

**Wiring:**
- Potentiometer outer legs → 5V and GND
- Potentiometer middle leg (wiper) → A0
- LED anode → 220Ω resistor → pin 9 (PWM-capable, marked `~`)
- LED cathode → GND

## 2. Explanation

**Hardware view**
The potentiometer is a voltage divider. Turning the knob changes the resistance ratio on either side of the wiper, which changes the voltage at A0 between 0V and 5V. The 220Ω resistor on the LED limits current so it doesn't burn out.

**Signal view**
`analogRead()` is an ADC (analog-to-digital converter) — it samples the wiper's voltage and quantizes it into 1024 discrete levels (10-bit resolution). The Uno has no true DAC, so `analogWrite()` doesn't output a real analog voltage either — it generates PWM: a square wave switching fully on/off at ~490Hz on pin 9. The fraction of time it's on (duty cycle) sets the average voltage the LED experiences, and the LED's response smooths this into perceived brightness.

**Code logic**
```cpp
const int potPin = A0;
const int ledPin = 9;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(potPin);               // 0–1023
  int brightness = map(potValue, 0, 1023, 0, 255);  // rescale to 0–255
  analogWrite(ledPin, brightness);
  Serial.println(brightness);
  delay(10);
}
```
Each loop pass: read the knob position → rescale it to the PWM range → write it out to the LED → print it to Serial Monitor → repeat. This read → process → actuate pattern is the base structure behind most embedded control systems.

**Where this shows up in industry**
- Motor speed control (PWM drives H-bridges in robotics/EVs)
- LED dimming in architectural and automotive lighting
- Power electronics — PWM is core to switch-mode power supplies and motor controllers
- Sensor calibration and range-mapping in industrial control panels and automotive sensors
- This circuit is open-loop; adding feedback turns it into closed-loop PID control

## 3. Problem Faced

The potentiometer's outer legs weren't connected to power at all:
- One outer leg was wired to pin 9 instead of 5V/GND
- The other outer leg fed into the LED's anode wire
- A0 was tapped into that same LED node instead of the potentiometer's wiper leg

Result: the pot wasn't acting as a voltage divider — it sat in series between pin 9 and the LED, and A0 was reading the LED's node instead of the knob position. `analogRead(A0)` didn't reflect the knob at all.

**Root cause:** a potentiometer only works as an analog sensor when both outer legs are anchored to a fixed voltage difference (5V and GND). If an outer leg floats or connects to a digital pin instead, the wiper voltage becomes unpredictable.

## 4. Solution

Rewired to two separate branches sharing only a common ground:

| From | To |
|---|---|
| Potentiometer left leg | 5V |
| Potentiometer right leg | GND |
| Potentiometer middle leg (wiper) | A0 |
| Digital pin 9 | resistor → LED anode |
| LED cathode | GND |

**Verification:** opened Serial Monitor — turning the knob produced a smooth 0→1023 sweep in the printed values, and LED brightness visibly tracked it. Confirms the fix worked.

**Note on reliability:** wire tracing from a photo isn't a substitute for a multimeter check — worth confirming the wiper is genuinely the middle leg against the potentiometer's datasheet, since pin order isn't always symmetric across parts.

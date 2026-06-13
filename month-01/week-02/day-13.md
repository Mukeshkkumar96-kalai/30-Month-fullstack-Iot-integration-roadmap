# Today learning in electronics

- I am finding the error in the yesterday building circuit. The correct way to calculation
  
- 20mA is the absolute maximum, not the operating target. Industry standard is 10–15mA.
This means your chosen resistor logic has a flaw in its foundation, even if 180Ω accidentally produces a safer current:
At 20mA target → calculated 150Ω → chose 180Ω

- Actual current at 180Ω = 3V / 180 = 16.67mA ✓ (acceptable)

## Detail Calculation
```
Supply Voltage        = 5V
LED Forward Voltage   = 2V
Voltage across R      = 5V - 2V = 3V
Target Current        = 15mA = 0.015A  (not 20mA — that is absolute maximum)

R = 3 / 0.015 = 200Ω (calculated)
Chosen: 180Ω

Actual operating current at 180Ω:
I = 3 / 180 = 16.67mA  ✓ (within safe range, below 20mA maximum)
```
## Today learning in HTML and CSS 
- Today i learned the CSS variable in colours it provide code readability and easy to change
- I HTML learned the <nav>, <section> and <time>

## Definations
- nav --> represents a section of navigation links that help users move around a website or application.
- section --> groups related content under a common topic or theme.
- time --> represents a date or time in a machine-readable format while displaying a human-readable value.
```
<time datetime="2026-06-13T20:30:00">
  13 June 2026, 8:30 PM
</time>
```

# Debug Day   (DATE : Day 5, Week 1 — Debug Friday)
- Today i learned some basic with the ai metor. The Bug log file was attached


# CIRCUIT  : 3-LED series, 9V, 1kΩ resistor

## FAULT #1
- Symptom  : All LEDs off
- Cause    : Broken connection at LED leg
- Lesson   : Series circuits have single point of failure
- [image] (https://github.com/Mukeshkkumar96-kalai/Electronic-practices/blob/main/LED%20removed.png)

## FAULT #2
- Symptom  : LED glows dangerously bright
- Cause    : Missing current-limiting resistor
- Lesson   : Always protect LEDs with resistors
- [image] (https://github.com/Mukeshkkumar96-kalai/Electronic-practices/blob/main/Resistor%20removed.png)

## Calculation
- LED forward voltage    : ~2V
- Supply voltage         : 9V
- Excess voltage         : 9 - 2 = 7V across nothing
- Resistor               : 0Ω (removed)

- Current               : 7V ÷ 0Ω = ∞ (theoretically)
- Actual limiting factor : Only the wire resistance ~few ohms
 
- Realistic current      : 7V ÷ ~5Ω = 1.4A
- LED maximum rating     : 0.02A (20mA)

- Overstressed by        : 70× its maximum rating

## FAULT #3
- Symptom  : All LEDs off
- Cause    : Broken wire, open circuit
- Lesson   : No closed loop = no current flow
- [image] (https://github.com/Mukeshkkumar96-kalai/Electronic-practices/blob/main/Wire%20removed.png)

# Week 1 — Day 7 | Review Sunday
**Focus:** Review — Electricity Basics + Internet & How Web Works

---
## Completed webpage
[LED circuit] (https://github.com/Mukeshkkumar96-kalai/Fullstack-practice/tree/main/LED%20circuit%20webpage)

## Day Summary

Review Sunday for Week 1. Completed a 5-question quiz covering
Ohm's Law, series circuits, resistor calculation, internet request
sequence, and IoT system thinking. Identified weak areas, wrote
Week 1 portfolio summary, and completed the future roadmap section
of the LED circuit documentation webpage.

---

## Quiz Results

| # | Topic | Result | Score |
|---|-------|--------|-------|
| Q1 | Ohm's Law — calculate current (5V, 250Ω) | Correct — 0.02A | ✅ |
| Q2 | Series circuit — one LED burns out | Correct — all LEDs off | ✅ |
| Q3 | Resistor calculation (3.3V, 2V Vf, 10mA) | Correct — 130Ω | ✅ |
| Q4 | Internet request sequence — DNS to render | Incomplete — wrong order | ⚠️ |
| Q5 | IoT connection — circuit + webpage | Too vague — needs system thinking | ⚠️ |

**Final Score: 3 / 5**

---

## Areas To Revisit

### Priority 1 — DNS and HTTP Request Lifecycle
Wrong order given in quiz. Correct sequence memorised:

```
1. Type google.com → press Enter
2. Browser checks DNS → translates domain to IP address
3. Browser sends HTTPS request to that IP address
4. Request travels through routers across internet
5. Server receives the request
6. Server processes → sends back HTML, CSS, JS
7. Browser receives the response
8. Browser renders the page
```

> Key lesson: DNS lookup happens FIRST — before any
> request is sent. Browser needs the IP address before
> it can send anything.

### Priority 2 — System Level Thinking
Practice connecting every concept to the full IoT pipeline.
Not just "it helps my goal" but HOW it fits architecturally.

**Strong answer template:**
```
The LED circuit  → physical output layer of IoT node
The HTML page    → presentation layer in the browser
They connect via → microcontroller → backend API → browser
```

## Concepts Consolidated This Week

### Electricity Basics

| Concept | Formula | My Understanding |
|---------|---------|-----------------|
| Ohm's Law | V = IR | Voltage = Current × Resistance |
| Current (I) | I = V/R | Flow of electrons in a circuit |
| Resistance (R) | R = V/I | Opposition to current flow |
| Resistor formula | R = (Vs-Vf)/If | Protects LED from excess current |
| Series circuit | One path | One break = all components off |
| Parallel circuit | Multiple paths | One break = others still work |

### HTML Concepts

| Tag | Purpose | Learned |
|-----|---------|---------|
| `<meta charset>` | Browser character encoding | Day 6 |
| `<meta viewport>` | Mobile responsiveness | Day 6 |
| `<section id="">` | Thematic content with anchor target | Day 6 |
| `<table><tr><th><td>` | Structured data display | Day 6 |
| `<pre>` | Preformatted text — preserves spacing | Day 6 |
| `<a href="#">` | Anchor link — same page navigation | Day 6 |

### CSS Concepts

| Property | Value | Effect |
|----------|-------|--------|
| `display` | `flex` | Places children side by side |
| `flex-direction` | `row / column` | Horizontal or vertical layout |
| `flex` | `1` | Child fills remaining space |
| `margin` | `0 auto` | Centers block element horizontally |
| `border-collapse` | `collapse` | Merges table borders into single line |
| `scroll-behavior` | `smooth` | Smooth scroll on anchor click |
| `border-radius` | `8px / 20px` | Rounded corners |
| `:hover` | — | Styles applied on mouse-over |

### CSS Selector Priority
```
ID  >  Class  >  Element
#id    .class    table

Most specific selector always wins when rules conflict.
```

---

## Bugs Fixed This Week — Full Log

| Day | Bug | Cause | Fix | Lesson |
|-----|-----|-------|-----|--------|
| Day 5 | All LEDs off | LED connection removed | Reconnect LED | Series = single point of failure |
| Day 5 | LED too bright | Resistor removed | Add 470Ω resistor | R = (Vs-Vf)/If always |
| Day 5 | Circuit dead | Wire removed | Reconnect wire | No closed loop = no current |
| Day 6 | CSS not applying | Class name typo | Match names exactly | CSS is case-sensitive |
| Day 6 | Bootstrap broken | CDN not linked | Wrote own CSS | Link libraries before use |
| Day 6 | CSS rule ignored | Missing `}` bracket | Added bracket | One bracket breaks all below |
| Day 6 | Duplicate CSS | style.css linked twice | Removed duplicate | Check head tags carefully |
| Day 6 | pre indented | Leading whitespace | Start at column zero | pre preserves all whitespace |
| Day 6 | Wrong href | Missing `#` symbol | Added `#` | # targets same-page section IDs |

---

## Senior Level Insight This Week

> The resistor is never optional. In production IoT systems —
> smart irrigation controllers, crop monitoring nodes — engineers
> have destroyed entire PCB batches worth thousands of dollars
> by miscalculating resistor values. The formula R = (Vs-Vf)/If
> is not a beginner exercise. It is a production engineering decision.

---

## Week 2 Plan — Starting Tomorrow

| Day | Focus | Topic |
|-----|-------|-------|
| Mon Day 8  | Learn | JavaScript fundamentals + parallel circuits |
| Tue Day 9  | Learn | DOM manipulation + capacitors |
| Wed Day 10 | Practice | JS exercises + circuit practice |
| Thu Day 11 | Build | Interactive LED simulator in JavaScript |
| Fri Day 12 | Debug | JS error debugging |
| Sat Day 13 | Project | Week 2 project build |
| Sun Day 14 | Review | Quiz + Week 2 README summary |

---

## IoT Pipeline — Where I Am Today

```
[ LED Circuit ]  ←── Week 1 complete
      ↓
[ HTML/CSS Page ] ←── Week 1 complete
      ↓
[ JavaScript DOM ]  ←── Week 2 next
      ↓
[ Node.js Backend ]
      ↓
[ MQTT Broker ]
      ↓
[ ESP32 Microcontroller ]
      ↓
[ Physical Sensor / LED ]
      ↓
[ React Dashboard — Live Data ]
      ↓
[ Crop Advisory System — Month 24 ]
```

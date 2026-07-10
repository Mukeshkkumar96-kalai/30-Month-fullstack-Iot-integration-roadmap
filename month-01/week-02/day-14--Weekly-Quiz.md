# 📘 Week 2 — Day 14 | Review Sunday
**Topics:** Ohm's Law & Calculations | HTML Structure & Semantics
**Roadmap Phase:** Foundation — Electronics + Web Fundamentals

---

## 1. 📚 Today's Learning

### Electronics — Ohm's Law & Calculations
- Applied **V = IR** and derived forms: `I = V/R`, `R = V/I`
- Calculated **LED series resistor**: accounted for forward voltage drop before applying Ohm's Law
- Applied **Power Law**: `P = I²R` to find resistance from power and current
- Introduced to **Kirchhoff's Voltage Law (KVL)**: sum of voltage rises and drops in a closed loop = 0
- Understood distinction between **ohmic** (resistors) and **non-ohmic** (LEDs, diodes) components

### HTML — Structure & Semantics
- Differentiated `<div>` (generic layout container) from semantic elements (`<section>`, `<article>`, `<nav>`, `<header>`, `<footer>`, `<main>`)
- Understood **heading hierarchy** as a document outline — levels must not skip or reverse (`h1 → h2 → h3`)
- Learned correct `<script>` placement: bottom of `</body>` or `<head>` with `defer` attribute
- Understood why `defer` is the modern preferred approach: parallel download + deferred execution after DOM is ready

---

## 2. ⚠️ Problems Faced

| # | Problem | Subject |
|---|---------|---------|
| 1 | Answered Q3 (SEO + screen readers) with developer code readability — missed the actual question | HTML |
| 2 | Wrote "below the body" for script placement — invalid HTML location | HTML |
| 3 | Marked Q5 as True — incorrectly applied Ohm's Law to non-ohmic components (LEDs, capacitors) | Electronics |
| 4 | KVL stated as "add all voltages = 0" without sign convention — leads to nonsensical equations | Electronics |
| 5 | Used "forward current" instead of "forward voltage" in Q2 verbal explanation — terminology error | Electronics |

---

## 3. 🔧 Fixed

| # | Fix Applied |
|---|-------------|
| 1 | SEO: semantic tags give crawlers structural signals → affects content ranking. Screen readers: semantic landmarks let visually impaired users navigate by region — not a developer convenience feature |
| 2 | Script belongs just before `</body>`, OR in `<head>` with `defer`. Never after `</body>` — that is malformed HTML |
| 3 | Ohm's Law only applies to **ohmic conductors** where resistance is constant. LEDs are non-ohmic — resistance varies with current and temperature. That's why a series resistor is required |
| 4 | KVL with correct sign convention: `+Vsupply − V1 − V2 = 0`. Supply is a rise (+), components are drops (−). This is what makes KVL a valid diagnostic tool |
| 5 | In Q2: 2.1V is the **forward voltage** (Vf), not forward current. Forward current (If) = 20mA. Terminology must match the quantity |

---

## 4. ✅ Right Answer Explanations

### Electronics

**Q1 — Current through 470Ω resistor at 9V**
```
I = V / R = 9 / 470 = 0.0191 A = 19.1 mA
```
Always express low currents in **mA** with 3 significant figures.

---

**Q2 — LED series resistor (5V supply, Vf = 2.1V, If = 20mA)**
```
Voltage across resistor = Vsupply − Vf = 5 − 2.1 = 3.9V
R = V / I = 3.9 / 0.020 = 195Ω → Standard value: 200Ω
```
The forward voltage drop is subtracted first — Ohm's Law is then applied only to the resistor's share.

---

**Q3 — Resistance from power and current (P = 0.5W, I = 100mA)**
```
P = I²R  →  R = P / I² = 0.5 / (0.1)² = 0.5 / 0.01 = 50Ω
```

---

**Q4 — KVL: Series circuit with 12V and 8V drops**
```
+Vsupply − 12 − 8 = 0
Vsupply = 20V
```
KVL is the first diagnostic tool when debugging series circuits — if measured drops don't sum to the supply voltage, something is wrong.

---

**Q5 — Does Ohm's Law apply to all components?**

**False.** Ohm's Law applies only to **ohmic components** (resistors) where V/I = constant.
- **LEDs** are non-ohmic: resistance changes with current and temperature
- **Capacitors** block DC entirely; in AC they exhibit *impedance*, not resistance
- This is why LEDs always require a current-limiting resistor — they cannot self-regulate

---

### HTML

**Q1 — `<div>` vs `<section>`**
- `<div>` — generic container with no semantic meaning; use for layout and styling purposes only
- `<section>` — thematic grouping with a heading; use when content forms a distinct topic in the document outline

**Q2 — Three semantic HTML5 elements**
- `<nav>` — primary navigation links (not every hyperlink on the page)
- `<main>` — the primary content of the document; only one per page
- `<article>` — self-contained content that makes sense independently (blog post, news item)
- `<header>` / `<footer>` — introductory and closing content respectively

**Q3 — Why semantics matter for SEO and screen readers**
- **SEO:** Search crawlers read semantic tags as structural signals. `<article>` tells Google the content is standalone and indexable. `<div>`-only pages give crawlers no hierarchy to parse.
- **Screen readers:** Assistive technology announces semantic elements as landmarks (`<nav>` = "navigation region"). Without semantics, blind users hear an undifferentiated content wall with no way to jump between sections. This is an **accessibility (a11y)** requirement, not a convenience.

**Q4 — Heading hierarchy error**
```html
<!-- ❌ Wrong -->
<h1>My Portfolio</h1>
<h3>About Me</h3>   <!-- skips h2 -->
<h2>Projects</h2>   <!-- reverses back -->

<!-- ✅ Correct -->
<h1>My Portfolio</h1>
<h2>About Me</h2>
<h2>Projects</h2>

<!-- ✅ it is also Correct -->
<h1>My Portfolio</h1>
<h2>About Me</h2>
<h3>Projects</h3>
```
Headings define the document outline. Skipping levels breaks screen reader navigation and SEO parsing.

**Q5 — Script tag placement**
```html
<!-- ✅ Traditional — safe -->
<body>
  ...
  <script src="app.js"></script>
</body>

<!-- ✅ Modern preferred — parallel download + deferred execution -->
<head>
  <script src="app.js" defer></script>
</head>
```
`defer` downloads the script while HTML parses, then executes only after the DOM is complete.
**Practical impact:** Without this, `document.getElementById('audio-player')` returns `null` — your music player breaks before it starts.

---

## 🔁 Revision Priority for Week 3

| Priority | Topic |
|----------|-------|
| 🔴 High | Ohmic vs non-ohmic components (diodes, thermistors, LEDs) |
| 🔴 High | Kirchhoff's Voltage Law — sign convention + series/parallel application |
| 🟡 Medium | `<article>` vs `<section>` vs `<div>` — three-way distinction |
| 🟡 Medium | HTML accessibility (a11y) — ARIA roles, landmark regions |
| 🟢 Next concept | **Voltage Dividers** (Electronics) + **CSS Box Model** (Frontend) |

---

## 📊 Quiz Scores

| Quiz | Score | Status |
|------|-------|--------|
| Ohm's Law & Calculations | 4 / 5 | ⚠️ Revise KVL + non-ohmic components |
| HTML Structure & Semantics | 1.5 / 5 | ❌ Major revision needed — SEO, a11y, script placement |

## Internship details

- There are two task that is image gallery and music player it is in the final stage, have some changes and i uplaoded soon. 

---

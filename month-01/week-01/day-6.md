# Week 1 — Day 6 | Project Saturday
**Date:** 2026-05-22
**Day:** 6 / 730
**Focus:** HTML & CSS — LED Circuit Documentation Page

---

## What I Built Today

A structured webpage that documents my Week 1 series LED circuit.
Built using pure HTML and CSS — no frameworks, no Bootstrap.
The page includes a sidebar navbar, components table, Ohm's law
calculation block, and lessons learned section.

**Live preview:** Open `led.html` in browser via Live Server (port 5501)

---

## Project Files

| File        | Purpose                          |
|-------------|----------------------------------|
| `led.html`  | Main documentation page          |
| `style.css` | All custom styling               |
| `settings.json` | VS Code Live Server config   |

---

## Circuit Details

| Component   | Value        | Purpose          | Status   |
|-------------|--------------|------------------|----------|
| LED × 3     | 2V Vf, 20mA  | Visual output    | Verified |
| Resistor × 1| 470Ω         | Current limiting | Verified |
| Battery     | 9V DC        | Power supply     | Verified |
| Breadboard  | 830 tie-pts  | Prototyping      | Verified |

### Ohm's Law Calculation
```
Formula  : R = (Vs - Vf) / If
Vs       : 9V   — supply voltage
Vf       : 2V   — LED forward voltage
If       : 0.015A — target current (15mA)
─────────────────────────────────────────
Result   : (9 - 2) / 0.015 = 466.67Ω
Standard : 470Ω ✓
```

---

## HTML Concepts Learned Today

### 1. Essential Head Tags
Every HTML file must have these three — missing them causes
rendering and mobile display problems.
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LED Circuit</title>
```

### 2. Anchor Links with #
The `#` symbol makes a link jump to a section on the same page.
Without `#` the browser tries to open a file with that name.
```html
<!-- correct — jumps to section on same page -->
<a href="#components">Components</a>

<!-- wrong — tries to open a file called calculation -->
<a href="calculation">Calculation</a>
```

### 3. Table Tags
Three tags work together to build a table.
```html
<table>         <!-- the whole table -->
  <tr>          <!-- one row -->
    <th>Header</th>   <!-- header cell — bold -->
    <td>Data</td>     <!-- data cell — normal -->
  </tr>
</table>
```

### 4. Preformatted Text
`<pre>` preserves all spaces and line breaks exactly as typed.
Perfect for calculations and code blocks.
```html
<pre>
Formula : R = (Vs - Vf) / If
Result  : 470Ω
</pre>
```
> ⚠️ Always start content at the left edge inside `<pre>`.
> Leading whitespace is visible in the browser.

### 5. Semantic Tags Used
```html
<nav>     — navigation sidebar
<main>    — primary page content
<section> — thematic content group with id for anchor links
<h1>      — one per page only (main title)
<h2>      — section titles
<h3>      — sub-section titles
```

---

## CSS Concepts Learned Today

### 1. CSS Selectors
```css
/* Class selector — targets class="navbar" */
.navbar { }

/* ID selector — targets id="components" */
#components { }

/* Descendant selector — th inside .component-table */
.component-table th { }

/* Multi selector — same rule for both */
.component-table th,
.component-table td { }

/* Hover pseudo-class — on mouse-over */
.navbar-card a:hover { }
```

**Priority rule:**
```
ID  >  Class  >  Element
#id    .class    table
```

### 2. Flexbox Layout
Makes the navbar and main content sit side by side.
```css
/* parent becomes flex container */
.background {
    display: flex;
    flex-direction: row;   /* side by side */
}

/* child fills remaining space */
.main-content {
    flex: 1;
}

/* navbar links stack vertically */
.navbar-card {
    display: flex;
    flex-direction: column;
}
```

### 3. Centering a Table
```css
.component-table {
    margin: 0 auto;   /* auto on left and right = centered */
}
```

### 4. Clean Table Borders
```css
.component-table {
    border-collapse: collapse;   /* merges double borders into one */
}

.component-table th,
.component-table td {
    border: 1px solid #3f2a24;
    padding: 8px 16px;
}
```

### 5. Smooth Scroll Navigation
```css
html {
    scroll-behavior: smooth;   /* anchor links scroll smoothly */
}
```

### 6. Hover Effect
```css
.navbar-card a {
    background-color: #f5dfc0;   /* normal state */
    color: #3f2a24;
}

.navbar-card a:hover {
    background-color: #3f2a24;   /* mouse-over state */
    color: #e6c5a8;
}
```

### 7. border-radius
```css
.navbar  { border-radius: 20px; }   /* very rounded */
.card    { border-radius: 8px; }    /* slightly rounded */
```

---

## Bugs Fixed Today

| # | Bug | Cause | Fix | Lesson |
|---|-----|-------|-----|--------|
| 1 | CSS not applying | Class name typo — `component-table` vs `components-table` | Matched names exactly | CSS is case-sensitive |
| 2 | Bootstrap not working | CDN not linked in `<head>` | Removed Bootstrap, wrote own CSS | Always link libraries before use |
| 3 | CSS rule broken | Missing closing `}` bracket | Added closing bracket | One missing bracket breaks all rules below |
| 4 | Duplicate CSS link | `style.css` linked twice in `<head>` | Removed duplicate `<link>` tag | Check head tags carefully |
| 5 | `<pre>` content indented | Leading whitespace in HTML source | Moved content to column zero | `<pre>` preserves all whitespace |
| 6 | Wrong href format | `href="calculation"` without `#` | Changed to `href="#calculation"` | `#` targets same-page section IDs |

---

## Page Structure Built

```
led.html
│
├── <head>
│   ├── charset, viewport, title
│   └── link to style.css
│
└── <body class="background">  ← display: flex
    │
    ├── <div class="navbar">   ← fixed 200px width
    │   ├── <h1>LED Circuit</h1>
    │   └── <nav> links → #components, #calculation, #lessons
    │
    └── <main class="main-content">  ← flex: 1
        ├── <section id="components">
        │   └── <table> — 4 components with value and purpose
        │
        ├── <section id="calculation">
        │   └── <pre> — Ohm's law formula and result
        │
        └── <section id="lessons">
            └── 4 lessons with h2 + p pairs
```

---

## What I Will Build Next

- [ ] Add `#future` section — IoT roadmap table
- [ ] Style `<h2>` headings inside sections
- [ ] Add `<footer>` with GitHub link
- [ ] Push final version to GitHub with proper commit message

---

## Connection To IoT Goal

> This webpage is the **documentation layer** of a future IoT pipeline.
> Right now it explains a physical circuit in a browser.
> By Week 15 — a Node.js server will serve this page with **live sensor data**
> from an ESP32 reading soil moisture in a field node.
> The HTML structure built today is the same structure that will display
> real agricultural data later.

---

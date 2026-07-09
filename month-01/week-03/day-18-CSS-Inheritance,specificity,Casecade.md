# CSS: Inheritance, Specificity, Cascade & !important

A study README covering the four concepts that decide "which CSS rule actually wins."

---

## 1. Inheritance

### 📘 Today I Learned
Some CSS properties automatically pass down from a parent element to its children, even if you never wrote a rule for the child. Others don't, unless you force them to.

### 💡 Explanation
- **Inherited by default**: mostly text-related properties — `color`, `font-family`, `font-size`, `line-height`, `visibility`, `letter-spacing`.
- **Not inherited by default**: mostly box/layout properties — `margin`, `padding`, `border`, `width`, `height`, `background`, `display`.
- You can override natural behavior with keywords:
  - `inherit` → force a property to take the parent's value.
  - `initial` → reset to the property's default value.
  - `unset` → acts like `inherit` if the property is naturally inherited, otherwise like `initial`.
  - `revert` → resets to the browser's (or user's) default stylesheet value.

```css
p {
  color: inherit;      /* take color from parent, even if p isn't inherited by default in this context */
  border: unset;       /* border isn't inherited by default, so this behaves like initial */
}
```

### ⚠️ Common Misconception
"CSS inherits everything from the parent automatically." — False. Only specific text/typography-related properties inherit by default. Layout and box-model properties do not, which is why a `<div>` doesn't get its parent's `border` or `padding` for free.

### 🔧 How to Fix / Best Practice
- Don't assume — check MDN's "Inherited" field on a property page before relying on it.
- Use `inherit` explicitly when you want consistent typography across nested components (e.g., buttons/inputs not inheriting `font-family` by default — a classic gotcha).
- Use CSS custom properties (`--variables`) for values you want to cascade down predictably; custom properties **do** inherit by default.

---

## 2. The Cascade

### 📘 Today I Learned
The "cascade" is the algorithm the browser uses to resolve conflicts when multiple CSS rules target the same element and property. It's not just "last rule wins" — that's only the final tiebreaker.

### 💡 Explanation
The cascade resolves conflicts in this order (highest priority first):

1. **Origin & Importance** (in order of priority):
   1. User-agent (browser default) styles
   2. User styles
   3. Author styles (your CSS)
   4. Author `!important`
   5. User `!important`
   6. User-agent `!important`
2. **Specificity** — more specific selectors win (see section 3).
3. **Source order** — if origin and specificity are equal, the rule that appears **last** in the stylesheet (or later `<link>`/`<style>`) wins.

There's also **layers** (`@layer`) in modern CSS, which let you group styles and control cascade priority between groups explicitly, before specificity is even considered.

### ⚠️ Common Misconception
"CSS just applies whichever rule comes last in the file." — Only true when specificity is tied. A highly specific selector written earlier in the file will still beat a low-specificity selector written later.

### 🔧 How to Fix / Best Practice
- Think of the cascade as a **series of tiebreakers**, not one rule: Origin/Importance → Specificity → Source order.
- Use `@layer` in larger projects to explicitly control priority between resets, base styles, components, and utilities — instead of fighting specificity wars.
- Keep stylesheet order intentional: resets → base → layout → components → utilities/overrides.

---

## 3. Specificity

### 📘 Today I Learned
Specificity is a "score" the browser calculates per selector to decide which rule wins when there's a conflict — and it's calculated by *counting selector types*, not by which selector "looks" more complicated.

### 💡 Explanation
Specificity is often represented as a 4-part value: **(inline, IDs, classes/attributes/pseudo-classes, elements/pseudo-elements)**.

| Selector type | Example | Weight |
|---|---|---|
| Inline style | `style="color:red"` | more compare to ID |
| ID | `#header` | more compare to Class |
| Class / attribute | `.btn`, `[type="text"]`, `:hover` | more compare to type |
| Type or tag  /  | `<h1>,<p>` | Less |


### ⚠️ Common Misconception
"Three classes = more specificity than one ID, because 3 > 1." — Wrong. Specificity isn't added into a single sum; it's compared column by column, and a single ID always outranks any number of classes.

### 🔧 How to Fix / Best Practice
- Avoid IDs for styling — reserve them for JS hooks/anchors. Style with classes so specificity stays flat and predictable.
- Avoid deeply nested selectors (`div#nav ul li a`) — they're fragile and hard to override later.
- Use `:where()` when writing reusable/utility styles you want to remain easily overridable.
- If you're fighting specificity constantly, it's usually a sign to flatten your selectors, not to add more nesting.

---

## 4. !important

### 📘 Today I Learned
`!important` doesn't just "boost priority a little" — it overrides normal specificity and source-order rules almost entirely, which is exactly why it's dangerous to overuse.

### 💡 Explanation
```css
.text {
  color: blue !important;
}
```
- A declaration marked `!important` wins over **any** non-important declaration for that property on that element, regardless of specificity or source order.
- If two `!important` declarations conflict, the cascade falls back to **specificity**, then **source order**, among the `!important` rules themselves.
- `!important` in a **user stylesheet** (e.g., browser accessibility settings) beats `!important` in an **author stylesheet** (your CSS) — this is intentional, so users can enforce accessibility preferences (like larger fonts) over a site's own styles.

### ⚠️ Common Misconception
"Adding `!important` guarantees my style wins, forever." — Not quite. It only wins over other *non-important* rules. Another `!important` rule with higher specificity (or later source order, if specificity ties) can still beat it — leading to "`!important` wars" where developers keep escalating.

### 🔧 How to Fix / Best Practice
- Treat `!important` as a last resort, not a first tool — it breaks the normal cascade and makes future overrides painful.
- Common legitimate uses: utility classes meant to always win (e.g., `.hidden { display: none !important; }`), or overriding inline styles/third-party CSS you can't edit directly.
- If you find yourself using `!important` to fight your own CSS, the real fix is almost always to **lower specificity elsewhere** (fewer IDs, flatter selectors, better source order) rather than escalating.
- Use `@layer` and `:where()` as modern alternatives to reduce the *need* for `!important` in the first place.

---

## Quick Reference: Resolution Order

When two rules target the same element/property, the browser checks, in order:

1. **Importance** — `!important` beats normal rules
2. **Origin** — user-agent → user → author (with `!important` origins flipped in priority)
3. **Layers** (`@layer`) — if used, layer order matters before specificity
4. **Specificity** — inline > ID > class/attribute/pseudo-class > element
5. **Source order** — last declared rule wins, if everything above is tied

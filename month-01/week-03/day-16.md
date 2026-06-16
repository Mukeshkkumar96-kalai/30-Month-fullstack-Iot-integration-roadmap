# 📘 Today's Learning: HTML Forms & Tables

## 1) Today Learning

- HTML Forms (`<form>`, `<input>`, `<label>`, `<select>`, `<textarea>`, `<button>`, `<fieldset>`)
- Form attributes (`name`, `required`, `pattern`, `min`/`max`, `maxlength`)
- HTML Tables (`<table>`, `<tr>`, `<td>`, `<th>`)
- Table structure tags (`<thead>`, `<tbody>`, `<tfoot>`, `<caption>`)
- Merging cells using `colspan` and `rowspan`
- Why accessibility (labels, `scope`) matters in both

---

## 2) Explanation in Simple Terms (One by One)

### 🔹 `<form>`
The container that wraps all input fields. It defines **where** (`action`) and **how** (`method`: GET or POST) the data goes when submitted.

### 🔹 `<input>`
The most common way to take user input. The `type` attribute decides what kind of input it is — text, email, password, checkbox, radio, file, etc.

### 🔹 `<label>`
Describes what an input field is for. Connected to an input using `for`/`id`, or by wrapping the input inside it. Important for accessibility (screen readers).

### 🔹 `<select>` and `<option>`
Creates a dropdown list. Each `<option>` is one choice inside the dropdown.

### 🔹 `<textarea>`
A box for entering multiple lines of text (like a comment box).

### 🔹 `<button>`
Used to submit the form or trigger other actions.

### 🔹 `name` attribute
Very important — without it, the input's value won't be sent when the form is submitted. It acts as the "key" for that value.

### 🔹 Validation attributes
`required`, `pattern`, `min`, `max`, `maxlength` — these let the browser check input automatically before submitting, without needing JavaScript.

### 🔹 `<fieldset>` and `<legend>`
Used to group related fields together (e.g., "Personal Info" section) with a title, both visually and for accessibility.

---

### 🔹 `<table>`
The main container for tabular (row-and-column) data.

### 🔹 `<tr>`
Stands for **table row** — defines one row.

### 🔹 `<td>`
Stands for **table data** — a single normal cell inside a row.

### 🔹 `<th>`
Stands for **table header** — a header cell, shown bold and centered by default. Should use `scope="col"` or `scope="row"` so screen readers know which header belongs to which data.

### 🔹 `<thead>`, `<tbody>`, `<tfoot>`
Group the header, body, and footer rows separately. Helps with styling and makes headers repeat when printing long tables.

### 🔹 `<caption>`
Adds a title/description for the whole table.

### 🔹 `colspan` and `rowspan`
Used to merge cells — `colspan` merges across columns, `rowspan` merges across rows.

---

## 📚 MDN Reference Links
- Forms: https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms
- Tables: https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Structuring_content/HTML_table_basics

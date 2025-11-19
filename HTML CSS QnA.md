

## 1. Write semantic HTML structure for a simple webpage.
### **Code (HTML)**
```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Sample Page</title>
</head>
<body>
  <header><h1>Site Title</h1><nav><!-- links --></nav></header>
  <main>
    <article><h2>Article Title</h2><p>Content...</p></article>
    <aside>Related</aside>
  </main>
  <footer>© 2025</footer>
</body>
</html>
````

### **Answer**

* Use semantic tags: `<header>`, `<main>`, `<article>`, `<aside>`, `<footer>`.
* Improves accessibility and SEO.
* Keep headings hierarchical (`h1` → `h2` ...).

---

## 2. Implement a responsive 2-column layout using CSS Grid.

### **Code (HTML + CSS)**

```html
<div class="grid">
  <div class="content">Main</div>
  <div class="sidebar">Sidebar</div>
</div>

<style>
.grid {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 16px;
}
@media (max-width: 700px) {
  .grid { grid-template-columns: 1fr; }
}
</style>
```

### **Answer**

* `display: grid` with `grid-template-columns` for columns.
* Use media queries to stack on small screens.
* Grid offers explicit layout control and gaps.

---

## 3. Center a `<div>` both vertically and horizontally (modern way).

### **Code (HTML + CSS)**

```html
<div class="wrap">
  <div class="box">Centered</div>
</div>

<style>
.wrap { display: flex; height: 200px; align-items: center; justify-content: center; }
.box { padding: 16px; border: 1px solid #ccc; }
</style>
```

### **Answer**

* Use Flexbox: `align-items: center; justify-content: center`.
* Works for variable-size children.
* Alternative: CSS Grid `place-items: center`.

---

## 4. Show CSS box model and how to include padding inside width.

### **Code (CSS)**

```css
.box {
  box-sizing: border-box; /* includes padding & border in width */
  width: 300px;
  padding: 16px;
  border: 2px solid #333;
}
```

### **Answer**

* Default `content-box` → padding added outside width.
* `box-sizing: border-box` recommended for predictable sizing.
* Use globally: `* { box-sizing: border-box; }`.

---

## 5. Create a responsive navigation bar (hamburger on small screens).

### **Code (HTML + CSS)**

```html
<nav class="nav">
  <button class="toggle" aria-expanded="false">☰</button>
  <ul class="menu">
    <li><a href="#">Home</a></li><!-- ... -->
  </ul>
</nav>

<style>
.nav { display:flex; align-items:center; gap:16px; }
.menu { display:flex; list-style:none; gap:12px; margin:0; padding:0; }
.toggle { display:none; }
@media (max-width:700px) {
  .menu { display:none; flex-direction:column; }
  .toggle { display:block; }
  .nav[aria-open="true"] .menu { display:flex; }
}
</style>
```

### **Answer**

* Desktop: horizontal flex menu.
* Mobile: hide menu, show toggle (JS toggles aria / attribute).
* Accessibility: use `aria-expanded` / keyboard focus.

---

## 6. Explain CSS specificity and override order.

### **Code (CSS)**

```css
/* lowest */ element { color: blue; }
/* higher */ .class { color: green; }
/* higher */ #id { color: red; }
/* highest */ inline-style in HTML element style="color: black;"
/* !important overrides normal rules */
```

### **Answer**

* Specificity order: inline > ID > class/attribute/pseudo-class > element/pseudo-element.
* `!important` should be avoided except small utility overrides.
* Use well-structured selectors and avoid over-specificity.

---

## 7. Implement a CSS-only tooltip.

### **Code (HTML + CSS)**

```html
<button class="tt">Hover
  <span class="tip">Tooltip text</span>
</button>

<style>
.tt { position: relative; }
.tip {
  position: absolute; bottom: 120%; left: 50%; transform: translateX(-50%);
  white-space: nowrap; padding:6px; border-radius:4px; visibility:hidden; opacity:0;
  transition: opacity .15s;
}
.tt:hover .tip, .tt:focus-within .tip { visibility: visible; opacity:1; }
</style>
```

### **Answer**

* Use `position: absolute` inside relative parent.
* Control visibility with `:hover` / `:focus-within` for keyboard access.
* Keep tooltips accessible (ARIA if needed).

---

## 8. Create a modal dialog (basic accessible structure).

### **Code (HTML + CSS)**

```html
<div class="modal" role="dialog" aria-modal="true" aria-hidden="false">
  <div class="panel">
    <button class="close">×</button>
    <h2>Title</h2>
    <p>Content...</p>
  </div>
</div>

<style>
.modal { position:fixed; inset:0; display:flex; align-items:center; justify-content:center; background:rgba(0,0,0,0.4); }
.panel { background:#fff; padding:20px; max-width:600px; width:90%; border-radius:6px; }
</style>
```

### **Answer**

* Overlay uses fixed positioning and centered panel.
* Manage focus trap and `aria-hidden` via JS for true accessibility.
* Ensure ESC closes modal and focus returns to trigger.

---

## 9. Make an image responsive and preserve aspect ratio.

### **Code (HTML + CSS)**

```html
<img src="photo.jpg" alt="photo" class="img">

<style>
.img { max-width:100%; height:auto; display:block; object-fit:cover; }
.container { width:300px; height:200px; overflow:hidden; }
.container img { width:100%; height:100%; object-fit:cover; }
</style>
```

### **Answer**

* `max-width:100%; height:auto` makes images scale.
* `object-fit` for cropping inside fixed-size containers.
* Use `srcset` / `picture` for responsive images and performance.

---

## 10. Explain CSS positioning types and stacking context.

### **Code (HTML + CSS)**

```css
.static { position: static; }    /* default */
.relative { position: relative; left: 10px; }
.absolute { position: absolute; top:0; right:0; } /* positioned to nearest positioned ancestor */
.fixed { position: fixed; top:0; } /* viewport */
.sticky { position: sticky; top: 0; } /* sticks within container */
```

### **Answer**

* `static`: normal flow. `relative`: offset without removing from flow.
* `absolute`: removed from flow, positioned against ancestor with position ≠ static.
* `fixed`: viewport-locked; `sticky`: switches between relative and fixed.
* `z-index` and properties like `opacity`, `transform` create stacking contexts.

---

# 🎯 Scenario-Based Questions (Top 3) — with minimal code & answers

---

## S1. Build a responsive card grid that becomes a single column on mobile.

### **Code**

```html
<div class="cards">
  <div class="card">1</div><div class="card">2</div><div class="card">3</div>
</div>

<style>
.cards { display: grid; grid-template-columns: repeat(3,1fr); gap:16px; }
@media (max-width:800px) { .cards { grid-template-columns: repeat(2,1fr); } }
@media (max-width:480px) { .cards { grid-template-columns: 1fr; } }
.card { padding:16px; border:1px solid #ddd; }
</style>
```

### **Answer**

* Use CSS Grid `repeat()` for fluid columns.
* Breakpoints via media queries: desktop → tablet → mobile.
* Keep content flexible and avoid fixed heights.

---

## S2. A form layout should be accessible and work on small screens.

### **Code**

```html
<form>
  <label for="email">Email</label>
  <input id="email" name="email" type="email" required />
  <button type="submit">Send</button>
</form>

<style>
form { display:flex; flex-direction:column; gap:8px; max-width:400px; }
input { padding:8px; font-size:1rem; }
@media(min-width:700px){ form{ flex-direction:row; align-items:flex-end; } }
</style>
```

### **Answer**

* Use `<label for>` and proper input types.
* Use `required`, `aria-*` when needed, and client-side + server-side validation.
* Ensure large touch targets and responsive layout.

---

## S3. Elements overlap on mobile — how to debug & fix?

### **Answer (Steps)**

* Check `viewport` meta and remove fixed widths; use `meta name="viewport" content="width=device-width,initial-scale=1"`.
* Inspect `position` and `z-index` (avoid absolute where unnecessary).
* Ensure `box-sizing: border-box`, use flexible units (`%`, `rem`, `vw`) and media queries to adjust layout.
* Test with devtools device emulation and fix the smallest breakpoint first.

---



### **11. Explain the difference between `display: none` and `visibility: hidden` with an example.**

Both properties hide elements, but they behave differently.

#### **Difference Table**

| Property             | Element Visible? | Space Reserved? |
|----------------------|------------------|------------------|
| `display: none`      | ❌ No            | ❌ No            |
| `visibility: hidden` | ❌ No            | ✅ Yes           |

---

### **Example**

```html
<p class="a">Paragraph A</p>
<p class="b">Paragraph B</p>

<style>
  .a { display: none; }        /* Element removed from layout */
  .b { visibility: hidden; }   /* Invisible but takes space */
</style>

---


---

marp: true

# Use Marp to turn this Markdown into slides

# VS Code: “Marp: Toggle Preview” and “Marp: Export Slide Deck…”

title: Product Documentation (Tech Writer Edition)
author: [22f2000757@ds.study.iitm.ac.in](mailto:22f2000757@ds.study.iitm.ac.in)

# Built‑in theme as base; we’ll add custom CSS below

theme: gaia
paginate: true

# Enable HTML/CSS in Markdown

---

<style>
/* ===== Custom Theme Specification (inline) ===== */
:root {
  --brand-bg: #0b1e33;     /* deep blue */
  --brand-accent: #4cc9f0; /* cyan */
  --brand-text: #e6f1ff;   /* near-white */
  --brand-muted: #a0b3c5;
}
section {
  font-family: ui-sans-serif, system-ui, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji", "Segoe UI Emoji";
  letter-spacing: 0.2px;
}
h1, h2, h3 { font-weight: 800; }
code, pre { border-radius: 8px; padding: .25rem .5rem; }
blockquote { border-left: 6px solid var(--brand-accent); padding-left: .8rem; color: var(--brand-muted); }
/* Lead slide variant */
section.lead h1 { font-size: 2.4em; }
/* Footer pagination style when used with _footer directive */
footer { color: var(--brand-muted); }
</style>

<!-- _class: lead -->

<!-- _header: **Product Docs** -->

<!-- _footer: Page {page} / {total} -->

# Product Documentation

**Tech Writer:** [22f2000757@ds.study.iitm.ac.in](mailto:22f2000757@ds.study.iitm.ac.in)

> Maintainable in Git. Exportable to HTML/PDF/PPTX. Styled with custom CSS and Marp directives.

---

## Agenda

* What & Why (Marp in product documentation)
* Authoring workflow in VS Code
* Theming & directives (this deck)
* Math in docs (algorithmic complexity)
* Exporting & CI
* GitHub raw URL for this deck

---

<!-- Background image demo (place your file at images/bg-hero.jpg) -->

<!-- _header: **Product Docs** -->

<!-- _footer: Page {page} / {total} -->

![bg cover](images/bg-hero.jpg)

# Overview

Marp lets you keep documentation **as Markdown** and publish to **multiple formats** without PowerPoint.

* Version control friendly
* Reviewable via PRs
* Theme with CSS

*(Tip: Add your own image at `images/bg-hero.jpg`.)*

---

<!-- Slide with custom colors via directives -->

<!-- _backgroundColor: #0b1e33 -->

<!-- _color: #e6f1ff -->

<!-- _header: **Theming & Directives** -->

<!-- _footer: Page {page} / {total} -->

# Custom Styling with Directives

Use per‑slide directives for **background**, **text color**, **headers/footers**, and layout classes.

```md
<!-- _backgroundColor: #0b1e33 -->
<!-- _color: #e6f1ff -->
<!-- _header: **Product Docs** -->
<!-- _footer: Page {page} / {total} -->
```

> Combine with the inline CSS (above) for a **lightweight custom theme**.

---

## Code Blocks (Syntax Highlighting)

```python
# src/example.py
from time import perf_counter

def timed(fn, *args, **kwargs):
    t0 = perf_counter()
    out = fn(*args, **kwargs)
    dt = perf_counter() - t0
    return out, dt
```

```javascript
// src/example.js
export const greet = (name) => `Hello, ${name}!`;
```

```css
/* themes/tokens.css */
:root { --accent: #4cc9f0; }
code { outline: 2px dashed var(--accent); }
```

---

## Math & Algorithmic Complexity

Inline math: \$O(n \log n)\$, \$E=mc^2\$.

Block math:

$$
T(n) = \begin{cases}
2\,T(\tfrac{n}{2}) + n, & n>1 \\
\Theta(1), & n=1
\end{cases} = \Theta(n\log n)
$$

> Use KaTeX (built into Marp) for performant math typesetting.

---

## Build & Export

From terminal (requires Marp CLI):

```bash
# HTML (web)
marp slides.md -o dist/slides.html

# PDF (sharing)
marp slides.md --pdf --allow-local-files -o dist/slides.pdf

# PowerPoint
marp slides.md --pptx -o dist/slides.pptx
```

VS Code commands (Command Palette):

* **Marp: Toggle Preview**
* **Marp: Export Slide Deck…**
* **Marp: Start Watch**

---

## Recommended Project Layout

```
presentation/
├─ slides.md
├─ images/
│  └─ bg-hero.jpg
├─ themes/
│  └─ custom.css   # (optional if you prefer external CSS)
└─ package.json
```

**.gitignore**

```
node_modules/
dist/
*.pdf
*.pptx
```

**package.json** (scripts)

```json
{
  "scripts": {
    "start": "marp -s .",
    "build": "marp slides.md -o dist/slides.html",
    "pdf": "marp slides.md --pdf --allow-local-files -o dist/slides.pdf",
    "pptx": "marp slides.md --pptx -o dist/slides.pptx"
  }
}
```

---

## Speaker Notes (optional)

Use HTML comments or `notes:` blocks depending on your workflow. Keep **one concept per slide** and prefer **progressive disclosure** through multiple slides instead of heavy bullet walls.

---

## Publishing & Raw GitHub URL

To reference this Markdown directly from GitHub, use the **raw** URL format:

```
https://raw.githubusercontent.com/<YOUR-GITHUB-USER>/<YOUR-REPO>/main/slides.md
```

**Example placeholder** (replace with your actual values):

```
https://raw.githubusercontent.com/your-username/product-docs/main/slides.md
```

> After pushing `slides.md` to GitHub, open it on GitHub and click **Raw** to verify the URL works.

---

## Wrap‑up

* Email embedded: **[22f2000757@ds.study.iitm.ac.in](mailto:22f2000757@ds.study.iitm.ac.in)**
* Custom theme (inline CSS) + directives
* Page numbers via `paginate: true` (and footer with `{page}/{total}`)
* Background image slide (`images/bg-hero.jpg`)
* Math equations included

**Next**: add product‑specific content, diagrams, and screenshots.

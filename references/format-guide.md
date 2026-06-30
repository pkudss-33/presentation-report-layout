# Presentation Report — Complete Format Parameter Reference

This document is the authoritative specification for the presentation-report
design system. Every CSS variable, layout dimension, typography rule, and
component parameter is documented here. Use this as the reference when
building, customizing, or troubleshooting a presentation report.

---

## 1. CSS Custom Properties (Design Tokens)

### 1.1 Color Palette

#### Text Colors (3-level grayscale)
| Variable | Hex | Usage |
|---|---|---|
| `--ink` | `#141e2e` | Primary text: headings, card titles, key labels |
| `--text` | `#2e3a50` | Body text: paragraphs, table cells, descriptions |
| `--muted` | `#5c6b82` | Secondary text: captions, notes, metadata, `.section-note` |

#### Line & Background Colors
| Variable | Hex | Usage |
|---|---|---|
| `--line` | `#d9e1ed` | Card borders, table borders, section dividers |
| `--line-light` | `#e8edf5` | Inner table cell dividers (lighter than card borders) |
| `--paper` | `#ffffff` | Card and container white backgrounds |
| `--wash` | `#f4f6fa` | Page background, subtle gray wash |

#### Brand Blue
| Variable | Hex | Usage |
|---|---|---|
| `--blue` | `#1e4fd4` | Primary buttons, active tab bg, link hover, accent elements |
| `--blue-dark` | `#1439a3` | Button hover, gradient end for active tabs |

#### Semantic Colors
| Variable | Hex | Semantic Meaning |
|---|---|---|
| `--green` | `#0a6e51` | Positive results, completion, profit, growth |
| `--amber` | `#8e5e00` | Strategy, attention needed, moderate concern |
| `--amber-dark` | `#6b4500` | Darker amber (rarely used directly) |
| `--red` | `#b04444` | Risk, warning, shortfall, negative trend |

#### Soft Background Colors (for `.b-card` variants)
| Variable | Hex | Used by |
|---|---|---|
| `--soft-blue` | `#eaf1fd` | `.b-card.blue` |
| `--soft-green` | `#ebf7f2` | `.b-card.green` |
| `--soft-amber` | `#fef8ed` | `.b-card.amber` |
| `--soft-red` | `#fef2f2` | `.b-card.red` |

### 1.2 Border Radius

| Variable | Value | Applied to |
|---|---|---|
| `--radius-sm` | `6px` | Buttons, `.pill`, `.tagline`, small interactive elements |
| `--radius` | `10px` | `.card`, `.b-card`, `.biz-box`, `table`, `.mission`, `.step`, `.panel`, `.topic-detail`, `.risk-alert` |
| `--radius-lg` | `14px` | `.mission-anchor`, `.nh-cover`, `.chapter-tabs a` |

Hardcoded `border-radius: 999px` is used for fully rounded pill/tag/circle elements:
`.quick-nav a`, `.tagline`, `.pill`, `.value-step small`

### 1.3 Box Shadows (4-level Elevation)

| Variable | Value | Usage |
|---|---|---|
| `--shadow-sm` | `0 2px 8px rgba(20,30,46,.04)` | Default state for all cards, tables, panels |
| `--shadow` | `0 4px 20px rgba(20,30,46,.06), 0 1px 3px rgba(20,30,46,.04)` | Hover state for cards, quick-nav, chapter-tabs |
| `--shadow-lg` | `0 12px 40px rgba(20,30,46,.08), 0 2px 6px rgba(20,30,46,.03)` | `.mission-anchor`, toolbar, active card hover |
| `--shadow-xl` | `0 20px 60px rgba(20,30,46,.1), 0 4px 12px rgba(20,30,46,.04)` | Top-layer floating elements (not heavily used) |

**Rule**: default = `shadow-sm`, hover = upgrade to `shadow-lg` + `translateY(-2px)`.
For cards that should feel heavier, default = `shadow-lg`.

### 1.4 Typography

#### Font Families
| Variable | Stack | Usage |
|---|---|---|
| `--display` | `"PingFang SC", "Microsoft YaHei", "Noto Sans CJK SC", -apple-system, BlinkMacSystemFont, "SF Pro Display", sans-serif` | h1, h2 |
| `--body` | `"PingFang SC", "Microsoft YaHei", "Noto Sans CJK SC", -apple-system, BlinkMacSystemFont, "SF Pro Text", "Helvetica Neue", Arial, sans-serif` | body, p, UI elements |

#### Font Weight Scale (from heaviest to lightest)
```
850 → h1, h2 (headlines)
820 → .nh-cover h4 (special large card titles)
800 → h3, details summary, .kpi-card .value
780 → h4, .chapter-tabs a, .card b, .b-card b, .mission b, th
750 → .eyebrow
720 → .tagline, .kpi-card .label
700 → .quick-nav a, .pill
```

#### Sizing Table

| Element | font-size | line-height | font-weight | letter-spacing |
|---|---|---|---|---|
| h1 | `clamp(38px, 5vw, 66px)` | 1.1 | 850 | 0 (removed) |
| h2 | `clamp(30px, 3.2vw, 44px)` | 1.2 | 850 | 0 (removed) |
| h3 | `23px` | 1.32 | 800 | 0 (removed) |
| h4 | `18.5px` | (inherit) | 780 | 0 (removed) |
| `.lead` | `18.5px` | 1.85 | (inherit) | 0 (removed) |
| body | `16px` | 1.72 | (inherit) | 0 (removed) |
| p | `15.5px` | 1.75 | (inherit) | (inherit) |
| `.section-note` | `16px` | 1.78 | (inherit) | (inherit) |
| `.eyebrow` | `14px` | (inherit) | 750 | `.02em` |
| `.tagline` | `13px` | (inherit) | 720 | `.01em` |
| th | `13.5px` | (inherit) | 780 | `.01em` |
| td | `14px` | 1.65 | (inherit) | (inherit) |
| `.kpi-card .label` | `13px` | (inherit) | 720 | `.02em` |
| `.kpi-card .value` | `32px` | 1.15 | 850 | 0 (removed) |
| `.kpi-card .sub` | `13.5px` | 1.5 | (inherit) | (inherit) |
| `.card span` (description) | `14px` | 1.65 | (inherit) | (inherit) |
| `.biz-title .num` | `14px` | (inherit) | 800 | `.03em` |
| `.risk-alert b` | `14px` | (inherit) | 800 | `.02em` |
| `.pill` | `13px` | (inherit) | 700 | (inherit) |
| `.step small` | `13px` | (inherit) | 800 | `.02em` |

### 1.5 Transitions

| Variable | Value | Usage |
|---|---|---|
| `--transition` | `220ms cubic-bezier(0.25, 0.1, 0.25, 1)` | All hover effects, tab switches, color changes |
| `--transition-slow` | `380ms cubic-bezier(0.25, 0.1, 0.25, 1)` | Reserved for larger motion (rarely used) |

**Rule**: every interactive element must use `transition: all var(--transition)`.
Never use a different easing curve — consistency is the point.

---

## 2. Page Layout Architecture

### 2.1 Overall Structure
```
┌─ .progress (fixed top, 3px, gradient, z-index: 40)
├─ .hero (full-width, white bg, radial gradient overlays)
│  ├─ .hero-inner
│  │  ├─ .eyebrow
│  │  ├─ h1
│  │  ├─ .lead
│  │  ├─ .chapter-tabs (3-4 column grid)
│  │  └─ .quick-nav (flex wrap pills)
├─ main
│  ├─ section[data-view="..."] (vertical padding 56px)
│  │  ├─ h2 + .section-note
│  │  ├─ .kpi-row (5-column metric dashboard)
│  │  ├─ .grid-3 / .grid-2 (card grids)
│  │  ├─ .biz-section (sidebar + content)
│  │  ├─ details.panel (collapsible sections)
│  │  └─ table (data tables)
│  └─ ...
```

### 2.2 Width Constraints

| Zone | Constraint | Notes |
|---|---|---|
| `.hero-inner` | `min(1260px, calc(100% - 42px))` | 21px side padding on small screens |
| `main` | `min(1180px, calc(100% - 42px))` | Slightly narrower than hero |
| `.section-note` | `max-width: 1040px` | Constrained for readability |
| h1 | `max-width: 1120px` | Slightly narrower than hero-inner |

### 2.3 Vertical Spacing

| Element | Value |
|---|---|
| `.hero-inner` padding | `62px 0 42px` |
| `section` padding | `56px 0` |
| `section` divider | `border-bottom: 1px solid var(--line)` |
| `section:last-child` | `border-bottom: 0` |
| h2 margin | `0 0 18px` |
| h3 margin | `32px 0 12px` |
| h4 margin | `24px 0 10px` |
| p margin | `10px 0` |

---

## 3. Grid System

All multi-column layouts use CSS Grid with `minmax(0, 1fr)` to prevent overflow.

### 3.1 Named Grids

| Class | Columns | Gap | Margin-top |
|---|---|---|---|
| `.kpi-row` | `repeat(5, minmax(0, 1fr))` | 14px | 26px |
| `.grid-4` | `repeat(4, minmax(0, 1fr))` | 14px | 22px |
| `.grid-3` | `repeat(3, minmax(0, 1fr))` | 14px | 22px |
| `.grid-2` | `repeat(2, minmax(0, 1fr))` | 14px | 20px |
| `.chapter-tabs` | `repeat(N, minmax(0, 1fr))` | 12px | 30px |
| `.timeline` | `repeat(5, minmax(0, 1fr))` | 10px | 20px |
| `.biz-grid` | `repeat(2, minmax(0, 1fr))` | 14px | (none) |

### 3.2 Asymmetric Grids

| Class | Columns | Gap | Use case |
|---|---|---|---|
| `.biz-section` | `270px minmax(0, 1fr)` | 22px | Sticky sidebar + content |
| `.review-work-item` | `minmax(200px, .44fr) minmax(0, 1.56fr)` | 18px | Left title + right description |

---

## 4. Component Specifications

### 4.1 Card Base

All card-like components share this base:
```css
border: 1px solid var(--line);
border-radius: var(--radius);        /* 10px */
background: var(--paper);
padding: 20px;
box-shadow: var(--shadow-sm);
transition: all var(--transition);
```

Hover (applied to `.card`, `.b-card`, `.biz-box`, `.mission`, `.step`, `.kpi-card`):
```css
transform: translateY(-2px);
box-shadow: var(--shadow-lg);
```

### 4.2 Color Cards (`.b-card`)

```css
.b-card.blue  { background: var(--soft-blue);  border-color: rgba(30,79,212,.1); }
.b-card.green { background: var(--soft-green); border-color: rgba(10,110,81,.1); }
.b-card.amber { background: var(--soft-amber); border-color: rgba(142,94,0,.1); }
.b-card.red   { background: var(--soft-red);   border-color: rgba(176,68,68,.1); }
```

### 4.3 KPI Cards (`.kpi-card`)

```
Structure:
  .kpi-card
    .label     → 13px muted, font-weight 720
    .value     → 32px display font, font-weight 850
    .sub       → 13.5px muted, margin-top 6px
```

Value color variants: `.value.up` (green), `.value.warn` (amber).

### 4.4 Chapter Tabs (`.chapter-tabs`)

```
Default:      #fafbfd bg, 1px var(--line) border, shadow-sm
Hover:        #f4f7fe bg, blue-tinged border, shadow, translateY(-1px)
Active:       linear-gradient(135deg, var(--blue), var(--blue-dark)), white text,
              blue glow shadow (0 8px 24px rgba(30,79,212,.25)), translateY(-2px)
```

Each tab: `min-height: 56px`, `padding: 14px 18px`, `font-size: 15.5px`, `font-weight: 780`.

### 4.5 Quick Nav Pills (`.quick-nav a`)

```
border-radius: 999px
height: 36px
padding: 0 14px
font-size: 13.5px
font-weight: 700
```

Hover: blue text, soft-blue background, translateY(-1px).

### 4.6 Tables

```css
table {
  border-collapse: separate;
  border-spacing: 0;
  border: 1px solid var(--line);
  border-radius: var(--radius);     /* 10px */
  overflow: hidden;
  box-shadow: var(--shadow-sm);
}
th {
  background: #f1f5f9;
  font-weight: 780;
  font-size: 13.5px;
  letter-spacing: .01em;
  padding: 13px 14px;
  border-bottom: 1px solid var(--line-light);
  border-right: 1px solid var(--line-light);
}
td {
  padding: 13px 14px;
  font-size: 14px;
  line-height: 1.65;
  border-bottom: 1px solid var(--line-light);
  border-right: 1px solid var(--line-light);
  vertical-align: top;
}
tr:last-child td { border-bottom: 0; }
th:last-child, td:last-child { border-right: 0; }
tbody tr:hover { background: #fafcfe; }
```

### 4.7 Collapsible Panels (`details.panel`)

```
summary:
  padding: 17px 20px
  font-weight: 800
  font-size: 15.5px
  list-style: none (hide default marker)
  ::after pseudo: "展开 ▼" (blue, 12.5px, font-weight 750)

[open] summary:
  border-bottom: 1px solid var(--line-light)
  background: #fafcfd
  ::after pseudo: "收起 ▲"

.detail-body:
  padding: 20px
  border-top: 1px solid var(--line-light)
```

### 4.8 Quote / Callout Blocks

```css
.quote {
  border-left: 4px solid var(--green);
  background: linear-gradient(90deg, var(--soft-green), rgba(235,247,242,.4));
  border-radius: 0 var(--radius) var(--radius) 0;
  padding: 20px 22px;
  margin: 22px 0;
  font-size: 15.5px;
  line-height: 1.75;
}
.quote.warn  { border-left-color: var(--amber); background: linear-gradient(90deg, var(--soft-amber), rgba(254,248,237,.4)); }
.quote.risk  { border-left-color: var(--red);   background: linear-gradient(90deg, var(--soft-red), rgba(254,242,242,.4)); }
```

### 4.9 Risk Alert Cards (`.risk-alert`)

```css
.risk-alert {
  border: 1px solid rgba(176,68,68,.25);
  border-left: 4px solid var(--red);
  border-radius: var(--radius);
  padding: 18px 20px;
  box-shadow: var(--shadow-sm);
}
.risk-alert b {
  display: block;
  color: var(--red);
  font-size: 14px;
  font-weight: 800;
  margin-bottom: 8px;
  letter-spacing: .02em;
}
.risk-alert span {
  color: var(--text);
  font-size: 14px;
  line-height: 1.7;
}
```

### 4.10 Timeline (`.timeline`)

5-column grid, `gap: 10px`.
Each `.step`: `min-height: 164px`, `padding: 20px`, `border-radius: var(--radius)`.

### 4.11 Biz Sections (`.biz-section`)

```
grid-template-columns: 270px minmax(0, 1fr)
gap: 22px
padding-top: 28px
border-top: 1px solid var(--line)

.biz-title: position: sticky; top: 80px
  .num       → blue, 14px, font-weight 800, letter-spacing .03em
  h3         → margin 6px 0 10px
  p          → muted, 14px, line-height 1.7
```

### 4.12 Tags & Pills

```css
.tagline {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 5px 12px;
  border: 1px solid var(--line);
  border-radius: 999px;
  background: #fff;
  color: var(--muted);
  font-size: 13px;
  font-weight: 720;
  letter-spacing: .01em;
}
.pill {
  display: inline-flex;
  padding: 5px 11px;
  border: 1px solid var(--line);
  border-radius: 999px;
  background: #fff;
  color: var(--muted);
  font-size: 13px;
  font-weight: 700;
}
```

---

## 5. Animations

### 5.1 Section Entry (fadeUpIn)
```css
@keyframes fadeUpIn {
  from { opacity: .85; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
section {
  animation: fadeUpIn .4s cubic-bezier(0.33, 0.1, 0.25, 1) both;
}
section:nth-child(2) { animation-delay: .03s; }
section:nth-child(3) { animation-delay: .06s; }
/* ...staggered 30ms per section... */
```

### 5.2 Card Entry (cardIn)
```css
@keyframes cardIn {
  from { opacity: .8; transform: translateY(6px); }
  to   { opacity: 1; transform: translateY(0); }
}
```
Applied to `.kpi-row .kpi-card`, `.grid-3 .card`, `.grid-3 .b-card`,
`.grid-2 .biz-box`, `.biz-grid .biz-box`.

### 5.3 Progress Bar
```javascript
window.addEventListener('scroll', () => {
  const ratio = scrollTop / (scrollHeight - clientHeight);
  progress.style.width = `${Math.min(1, Math.max(0, ratio)) * 100}%`;
});
```

### 5.4 View Switching
Controlled by `main[data-active-view]` — sections whose `data-view` doesn't
match are `display: none`. Tabs with `data-view-toggle` trigger JS that sets
the attribute and smooth-scrolls to top.

---

## 6. Responsive Breakpoints

### `@media (max-width: 980px)`
- All grid columns → `1fr` (single column)
- `.biz-section` → `1fr` with `position: static` sidebar
- Tables → `display: block; overflow-x: auto`
- `.hero-inner` → `padding-top: 48px`

### `@media (max-width: 640px)`
- `.hero-inner` → `padding: 40px 0 30px`
- h1 → `font-size: 28px`
- `.lead` → `font-size: 15px`
- `section` → `padding: 32px 0`
- `.kpi-card .value` → `font-size: 24px`

### Print (PDF Export)

The print stylesheet is designed to produce a clean, proportionally correct PDF
via browser Print → Save as PDF. Key design decisions:

```css
@media print {
  /* Landscape A4 — gives enough width for the 1180px content */
  @page {
    size: landscape;
    margin: 14mm 12mm 14mm 12mm;
  }

  /* Force color & background rendering (browsers strip them by default) */
  * {
    -webkit-print-color-adjust: exact !important;
    print-color-adjust: exact !important;
  }

  /* Hide interactive-only elements */
  .progress, .chapter-tabs, .quick-nav, .pill-row { display: none; }

  /* Clean white page */
  body { background: #fff; background-image: none; }

  /* Each <section> = one logical page */
  section {
    break-before: page;
    break-inside: avoid;
    padding: 18px 0;
    animation: none;
    border-bottom: 0;
  }
  section:first-of-type { break-before: avoid; }

  /* Headings stick to their content */
  h2, h3, h4 { break-after: avoid; }

  /* Cards, panels, biz-sections — never split */
  .card, .b-card, .biz-box, .kpi-card, .step,
  .risk-alert, details.panel, .biz-section {
    animation: none;
    box-shadow: none;
    break-inside: avoid;
  }

  /* Grid rows stay together */
  .kpi-row, .grid-2, .grid-3, .grid-4, .biz-grid { break-inside: avoid; }

  /* Table: repeat header on each page, don't split rows */
  table tr { break-inside: avoid; }
  table thead { display: table-header-group; }

  /* Force all collapsible panels open */
  details.panel:not([open]) .detail-body { display: block; }
  details.panel summary::after { content: none; }

  /* Hero compact in print */
  .hero { border-bottom: 2px solid var(--line); }
  .hero-inner { padding: 28px 0 24px; }
  .hero::after { background: none; }

  /* Un-stick sidebars */
  .biz-title { position: static; }
}
```

**Page break strategy:**
- `h2` triggers a new page (`break-before: page`) — natural topic boundary
- First `h2` in the document skips the break (follows hero naturally)
- Sections flow naturally — content can span multiple pages within one view
- Individual cards/kpi-cards/panels use `break-inside: avoid` (never torn)
- Large containers (biz-section, grid-3, grid-4) can split across pages
- Only `.kpi-row` stays together (small, 3-5 items) 

**Layout preservation:**
- Landscape orientation preserves the 1180px content width without scaling
- 10-12mm margins keep reasonable whitespace
- `print-color-adjust: exact` preserves the semantic color system
- Grid proportions unchanged — no reflow, no column collapse
- Shadows removed (don't print well), borders remain
- `biz-title` sticky positioning removed for print

---

## 7. CJK Typesetting Rules

- **Thin spaces**: Between CJK characters and digits/Latin letters, use
  `&thinsp;` (U+2009, thin space, ~1/5 em). Never use full-width spaces
  (too wide) and never omit the space entirely (too cramped).
- **No letter-spacing on body**: The `body` element must have
  `letter-spacing: 0`. Letter-spacing on CJK text adds gaps around every
  character including digits, which looks broken.
- **Letter-spacing only on micro-labels**: `.eyebrow`, `.tagline`, `th`,
  `.kpi-card .label`, `.risk-alert b`, `.step small`, `.biz-title .num`
  may use small positive letter-spacing (`.01em`–`.04em`) for uppercase-style
  decorative effect. These elements are short (1–10 characters).

---

## 8. Page Background

```css
body {
  background: var(--wash);
  background-image:
    radial-gradient(ellipse at 20% 10%, rgba(30, 79, 212, .015) 0%, transparent 70%),
    radial-gradient(ellipse at 80% 50%, rgba(10, 110, 81, .01) 0%, transparent 60%);
}
```
Two subtle radial gradients at opposite corners give the page a gentle
atmospheric depth without being distracting. The blue tint is at top-left
and green tint at center-right.

---

## 9. Hero Header Decorative Overlays

```css
.hero::after {
  content: "";
  position: absolute; inset: 0;
  background:
    radial-gradient(circle at 85% 30%, rgba(30, 79, 212, .03) 0%, transparent 55%),
    radial-gradient(circle at 15% 70%, rgba(10, 110, 81, .025) 0%, transparent 45%);
  pointer-events: none;
}
```

---

## 10. JavaScript (Required)

The template requires three JS behaviors:

1. **Progress bar**: scroll listener updating `.progress` width
2. **View switching**: `setActiveView(view)` function that sets
   `main.dataset.activeView` and updates `.active` class on tabs
3. **Hash routing**: on page load, read `window.location.hash` to set
   initial active view

All JS is inline in a single `<script>` block at the end of `<body>`.
No external libraries.

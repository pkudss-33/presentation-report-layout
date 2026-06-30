---
name: presentation-report-layout
description: >-
  A pure visual layout / formatting skill for producing multi-view, card-nested,
  clearly structured presentation reports as single self-contained HTML files.
  This skill ONLY provides the format shell — a tabbed view-switching
  architecture with KPI dashboard cards, color-coded semantic cards
  (blue/green/amber/red), collapsible detail panels, sticky sidebar sections,
  and progressive scroll-reveal animations. It does NOT include any content
  analysis, distillation, or information-processing logic. Use this skill when
  the user needs a polished multi-section presentation format for work summaries,
  月度/季度经营报告, 多事项汇总, 摘要报告, 或汇报材料 — the user provides the
  structured content, and this skill wraps it in the layout.
---

# Presentation Report Layout

A **pure formatting skill** — no content logic, no analysis, no distillation.
This skill provides a proven corporate design system as a single self-contained
HTML template: multi-view tabbed navigation, KPI metric dashboards, color-coded
semantic cards, collapsible detail panels, sticky business-unit sections, and
progressive scroll animations. You bring the structured content; this skill
provides the polished multi-page card-nested layout.

## When this applies

The user already has structured content and needs it formatted into a polished,
multi-section HTML report with tabbed navigation. This is a **layout engine**,
not a thinking engine. Keywords include:

- 工作总结 / 年中总结 / 年终总结
- 月度报告 / 季度报告 / 经营简报
- 多事项汇总 / 摘要报告 / 汇报材料
- "做成那个 HTML 报告的格式"
- "用那个格式展示"
- "套用 presentation report 格式"

The output is a **single self-contained HTML file** with tabbed navigation
between major views, designed for screen reading and executive scanning.
**The user is responsible for providing the content, structured as they want it.**
This skill only formats that content into the layout.

## Design System Overview

The format is based on a refined corporate palette with 5 semantic color layers
and a strict card-based layout system. All parameters are defined as CSS custom
properties in `:root`, making them easy to adapt per brand.

### Color System (5 layers)

| Layer | Variables | Usage |
|---|---|---|
| Ink/Text | `--ink #141e2e`, `--text #2e3a50`, `--muted #5c6b82` | Three-level text grayscale: headings → body → captions |
| Line/BG | `--line #d9e1ed`, `--line-light #e8edf5`, `--paper #fff`, `--wash #f4f6fa` | Card borders, inner dividers, card white, page gray |
| Brand Blue | `--blue #1e4fd4`, `--blue-dark #1439a3` | Primary buttons, active states, link emphasis |
| Semantic | `--green #0a6e51`, `--amber #8e5e00`, `--red #b04444` | Positive/completion, strategy/attention, warning/risk |
| Soft BG | `--soft-blue`, `--soft-green`, `--soft-amber`, `--soft-red` | Pastel card backgrounds (`.b-card.blue` etc.) |

### Radius Hierarchy

```
--radius-sm: 6px     → buttons, pills, small tags
--radius: 10px        → cards, tables, general components
--radius-lg: 14px     → large containers, hero cards
999px                 → fully rounded pills / numbered circles (hardcoded)
```

### Shadow Elevation (4 levels)

```
--shadow-sm  → 0 2px 8px  rgba(20,30,46,.04)      default card
--shadow     → 0 4px 20px rgba(...) + 0 1px 3px    hover card
--shadow-lg  → 0 12px 40px rgba(...) + 0 2px 6px   featured containers
--shadow-xl  → 0 20px 60px rgba(...) + 0 4px 12px  top-layer (toolbars)
```

### Typography

```
--display: "PingFang SC", ... "SF Pro Display"   → h1, h2
--body:    "PingFang SC", ... "SF Pro Text"       → body, UI

Font weight scale: 850(h1/h2) > 820 > 800(h3) > 780(card titles) > 750 > 720 > 700
```

### Transition

Every interactive element uses the same easing:
```css
--transition: 220ms cubic-bezier(0.25, 0.1, 0.25, 1);
```

### Animations

- **Section entry**: `fadeUpIn` — opacity 0.85→1, translateY 12px→0, 400ms, staggered 30ms per section
- **Card entry**: `cardIn` — opacity 0.8→1, translateY 6px→0, 350ms, staggered 80ms per card
- **Progress bar**: Gradient bar at page top, width = scroll ratio
- **View switching**: `data-active-view` attribute controls section visibility + smooth scroll to top

## Component Catalog

Copy `assets/presentation-template.html` to your workspace. Its `<style>` block IS
the design system — keep it intact and fill in content, replacing `[[...]]` placeholders.

| Component | CSS class | Use for |
|---|---|---|
| **Hero header** | `.hero` > `.hero-inner` | Report title + eyebrow label + lead paragraph + chapter tabs |
| **Eyebrow** | `.eyebrow` | Green accent label above h1 with 36px gradient line decoration |
| **Chapter tabs** | `.chapter-tabs` > `a[data-view-toggle]` | Top-level navigation between views (3-5 tabs, grid layout) |
| **Quick nav** | `.quick-nav` > `a` | Pill-shaped secondary navigation within a view (999px radius) |
| **KPI cards** | `.kpi-row` > `.kpi-card` | 5-column metric dashboard: label + large number + sub-note |
| **Card grid (2-col)** | `.grid-2` > `.card` | Side-by-side comparison, two perspectives |
| **Card grid (3-col)** | `.grid-3` > `.card` or `.b-card` | Three pillars, three findings, three options |
| **Card grid (4-col)** | `.grid-4` > `.card` | Four capability pillars, four quadrants |
| **Color cards** | `.b-card.blue` / `.green` / `.amber` / `.red` | Semantic color-coded key points with soft backgrounds |
| **Tagline** | `.tagline` | Small pill label inside cards for categorization (999px radius) |
| **Tables** | `table` | Structured data with rounded corners, header bg #f1f5f9, row hover |
| **Collapsible panels** | `details.panel` > `summary` + `.detail-body` | Expandable sections with "展开 ▼" / "收起 ▲" indicator |
| **Quote / Callout** | `.quote` / `.quote.warn` / `.quote.risk` | Key insight with left 4px accent border (green/amber/red) |
| **Quote block** | `.quote` | A single highlighted insight, green left border, gradient green bg |
| **Risk alerts** | `.risk-alert` | Red-left-border warning cards with bold red title |
| **Timeline** | `.timeline` > `.step` | 5-column phased progression with numbered steps |
| **Biz sections** | `.biz-section` > `.biz-title` + content | 270px sticky sidebar + 1fr content for per-business-unit drill-down |
| **Biz grid** | `.biz-grid` > `.biz-box` | 2-column card grid inside biz sections |
| **Pill row** | `.pill-row` > `.pill` | Horizontal tag cloud of rounded pills |
| **Section note** | `.section-note` | Muted paragraph below h2 explaining section scope (max-width 1040px) |
| **Progress bar** | `.progress` | Fixed gradient reading-progress indicator (3px, top of page) |
| **Metric highlight** | `.metric-highlight` > `.num` + `.unit` | Inline large number + small unit label |

### Layout Widths

| Element | Width constraint |
|---|---|
| `.hero-inner` | `min(1260px, calc(100% - 42px))` |
| `main` | `min(1180px, calc(100% - 42px))` |
| `.section-note` | `max-width: 1040px` |
| `h1` | `max-width: 1120px` |

### Responsive Breakpoints

| Breakpoint | Behavior |
|---|---|
| `≤980px` | All multi-column grids → single column; biz-section sidebar → top; tables → horizontal scroll |
| `≤640px` | Hero padding reduced; h1 drops to 28px; section padding shrinks |

### Print Styles

- Hide progress bar
- White background
- No animations
- Avoid page breaks inside cards

## Workflow

### 1. Read the format guide
Read `references/format-guide.md` for the complete parameter reference. It
documents every CSS variable, grid dimension, spacing value, and typography
rule in detail. Use it as the authoritative spec when customizing or
troubleshooting.

### 2. Map content to components
Take the user's structured content and decide which layout component each piece
fits into. This is a **mapping** step, not an analysis step:
- **Which view** does it belong to? (overview / detail / risk / appendix)
- **Which component** best expresses it? (KPI card / table / color card / panel)
- **What's the semantic color?** (blue = foundation/data, green = positive,
  amber = strategy/attention, red = risk/warning)

### 3. Choose the view structure
Map content to 3–5 top-level views. Default arc:

```
01  集团总览 / 核心摘要    KPI cards + 3-card summary
02  业务详情 / 分项展开    biz-sections with per-unit drill-down
03  风险提示 / 关注事项    risk-alert cards
(opt) 附录 / 数据明细    collapsible panels with tables
```

Use `.chapter-tabs` for the main navigation. Use `.quick-nav` for intra-view
anchors within long sections.

### 4. Build from the template
Copy `assets/presentation-template.html`. The template includes:
- Complete `<style>` block (the full design system)
- Hero header with chapter tabs
- Main content area with `data-active-view` switching
- One example of each major component, commented
- Progress bar and view-switching JavaScript
- Responsive and print media queries

Replace `[[...]]` placeholders. Match content to components per the catalog
above. The `<style>` block should rarely need modification — change `:root`
variables only for brand re-skinning.

### 5. Self-check before delivering
- **Hero clarity**: eyebrow + h1 + lead should tell the reader what this report
  is about in 10 seconds.
- **KPI impact**: the first KPI row should surface the 4–5 numbers that matter
  most. Use `.value.up` (green) for positive, `.value.warn` (amber) for
  concerning.
- **One idea per card**: each `.card` or `.b-card` makes exactly one point.
- **Color discipline**: blue = data/infrastructure, green = positive/achievement,
  amber = strategy/attention, red = risk/warning. Don't mix semantics.
- **Scan test**: a reader should understand the entire report by reading only
  h2s, card h3s, and KPI labels.
- **No external dependencies**: all CSS and JS are inline. The file should
  render correctly when opened directly from disk.
- **Thin spaces**: use `&thinsp;` (U+2009) between CJK characters and
  digits/Latin text — never full-width spaces (too gappy) and never zero space
  (too cramped).
- **Number formatting**: numbers in running text should not have letter-spacing
  applied. The `body` has `letter-spacing: 0`. Only decorative micro-labels
  (`.eyebrow`, `.tagline`, `th`, `.kpi-card .label`) use letter-spacing.

### 6. Deliver
Save as `<name>.html` in the working directory. Open in browser to verify.
On iteration: renumber sections, update KPI values, adjust card colors if
sentiment changes, and always re-verify the scan test.

## Quick Reference: Key Numbers

| Parameter | Value |
|---|---|
| Page max width (hero) | 1260px |
| Page max width (content) | 1180px |
| Side padding | 21px each side |
| Section vertical padding | 56px |
| Card padding | 17–20px |
| Default grid gap | 14px |
| Card border-radius | 10px |
| Table border-radius | 10px |
| Pill border-radius | 999px |
| Hover lift | translateY(-2px) |
| Transition duration | 220ms |
| Body font-size | 16px |
| Body line-height | 1.72 |
| KPI value font-size | 32px |
| h1 font-size | clamp(38px, 5vw, 66px) |
| h2 font-size | clamp(30px, 3.2vw, 44px) |
| Section note max-width | 1040px |

## Files
- `references/format-guide.md` — complete parameter reference. **Read first.**
- `assets/presentation-template.html` — full design system with every component
  as a commented, placeholder-filled example. Copy and fill.

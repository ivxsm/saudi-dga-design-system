# DGA Layout and Spacing System

> Reference: https://design.dga.gov.sa/guidelines/foundations/layout-and-spacing

## Overview

The DGA Layout and Spacing system is built around an **8px base grid** (with **4px micro-increments**) and a **12-column responsive fluid grid**. It enforces consistent spatial rhythm across all Saudi government portals while utilizing CSS Logical Properties (`inline`, `block`) to ensure seamless bidirectional responsiveness (RTL for Arabic and LTR for English).

---

## The 4px / 8px Spacing Scale

Every margin, padding, gap, and dimension in DGA-compliant applications must map to standard spacing tokens. Arbitrary pixel measurements (such as `13px`, `19px`, `27px`) are strictly prohibited.

| Token | Pixels | Rem (base 16) | Typical Application |
|-------|--------|---------------|---------------------|
| `--dga-space-0` | `0px` | `0` | Reset / zero spacing |
| `--dga-space-1` | `4px` | `0.25rem` | Micro-gap, badge padding, checkbox inner padding |
| `--dga-space-2` | `8px` | `0.5rem` | Small icon gap, inline tag spacing, button inner gap |
| `--dga-space-3` | `12px` | `0.75rem` | Compact element padding, input vertical padding |
| `--dga-space-4` | `16px` | `1.0rem` | **Base unit:** Standard card padding, input horizontal padding |
| `--dga-space-5` | `20px` | `1.25rem` | Medium component gaps |
| `--dga-space-6` | `24px` | `1.5rem` | Large card padding, section gap on mobile |
| `--dga-space-8` | `32px` | `2.0rem` | Section spacing, container padding on tablet |
| `--dga-space-10` | `40px` | `2.5rem` | Major module separation |
| `--dga-space-12` | `48px` | `3.0rem` | Page section spacing on desktop |
| `--dga-space-16` | `64px` | `4.0rem` | Large hero banner padding, footer separation |
| `--dga-space-20` | `80px` | `5.0rem` | Major landing page block separation |
| `--dga-space-24` | `96px` | `6.0rem` | Maximum macro whitespace separation |

```css
:root {
  --dga-space-0: 0;
  --dga-space-1: 0.25rem;  /* 4px */
  --dga-space-2: 0.5rem;   /* 8px */
  --dga-space-3: 0.75rem;  /* 12px */
  --dga-space-4: 1rem;     /* 16px */
  --dga-space-5: 1.25rem;  /* 20px */
  --dga-space-6: 1.5rem;   /* 24px */
  --dga-space-8: 2rem;     /* 32px */
  --dga-space-10: 2.5rem;  /* 40px */
  --dga-space-12: 3rem;    /* 48px */
  --dga-space-16: 4rem;    /* 64px */
  --dga-space-20: 5rem;    /* 80px */
  --dga-space-24: 6rem;    /* 96px */
}
```

---

## Responsive Breakpoints

Platforms Code segments viewports into five standard responsive tiers:

| Breakpoint | Token | Viewport Range | Device Class | Container Max-Width | Gutters | Outer Margins | Columns |
|------------|-------|----------------|--------------|---------------------|---------|---------------|---------|
| **Extra Small** | `xs` | `< 576px` | Mobile (portrait) | `100%` | `16px` | `16px` | 4 |
| **Small** | `sm` | `576px – 767px` | Large Mobile / Phablet | `540px` | `16px` | `24px` | 6 |
| **Medium** | `md` | `768px – 991px` | Tablet | `720px` | `24px` | `32px` | 8 |
| **Large** | `lg` | `992px – 1199px` | Small Desktop / Tablet Landscape | `960px` | `24px` | `32px` | 12 |
| **Extra Large** | `xl` | `1200px – 1399px` | Standard Desktop | `1140px` | `32px` | `48px` | 12 |
| **Ultra Large** | `xxl` | `≥ 1400px` | Large Display / Wide Desktop | `1320px` | `32px` | `64px` | 12 |

---

## 12-Column Grid Architecture

The DGA grid architecture utilizes standard fluid columns with adaptive gutters:

```css
.govsa-container {
  width: 100%;
  margin-inline: auto;
  padding-inline: var(--dga-space-4); /* 16px mobile */
}

@media (min-width: 576px) {
  .govsa-container {
    max-width: 540px;
    padding-inline: var(--dga-space-6); /* 24px */
  }
}

@media (min-width: 768px) {
  .govsa-container {
    max-width: 720px;
    padding-inline: var(--dga-space-8); /* 32px */
  }
}

@media (min-width: 992px) {
  .govsa-container {
    max-width: 960px;
  }
}

@media (min-width: 1200px) {
  .govsa-container {
    max-width: 1140px;
    padding-inline: var(--dga-space-12); /* 48px */
  }
}

@media (min-width: 1400px) {
  .govsa-container {
    max-width: 1320px;
    padding-inline: var(--dga-space-16); /* 64px */
  }
}

/* Grid Row & Column Definitions */
.govsa-row {
  display: flex;
  flex-wrap: wrap;
  margin-inline: calc(var(--dga-gutter, 1rem) * -0.5);
}

.govsa-col {
  flex: 1 0 0%;
  padding-inline: calc(var(--dga-gutter, 1rem) * 0.5);
}

/* Column spans (1 through 12) */
.govsa-col-12 { flex: 0 0 100%; max-width: 100%; }
.govsa-col-6  { flex: 0 0 50%; max-width: 50%; }
.govsa-col-4  { flex: 0 0 33.333333%; max-width: 33.333333%; }
.govsa-col-3  { flex: 0 0 25%; max-width: 25%; }

@media (min-width: 992px) {
  .govsa-col-lg-8 { flex: 0 0 66.666667%; max-width: 66.666667%; }
  .govsa-col-lg-4 { flex: 0 0 33.333333%; max-width: 33.333333%; }
}
```

---

## RTL & CSS Logical Properties

Saudi Platforms Code requires that interfaces operate natively in RTL (Arabic) with single-toggle LTR support. **Physical CSS properties (`left`, `right`, `margin-left`, `padding-right`) are forbidden** for spatial layout.

### Mapping Physical to Logical Properties

| Physical (Deprecated) | CSS Logical Equivalent | Behavior in RTL (`dir="rtl"`) | Behavior in LTR (`dir="ltr"`) |
|-----------------------|------------------------|-------------------------------|-------------------------------|
| `margin-left` | `margin-inline-start` | Margins the **right** side | Margins the **left** side |
| `margin-right` | `margin-inline-end` | Margins the **left** side | Margins the **right** side |
| `padding-left` | `padding-inline-start` | Pads the **right** side | Pads the **left** side |
| `padding-right` | `padding-inline-end` | Pads the **left** side | Pads the **right** side |
| `margin-top` | `margin-block-start` | Top margin | Top margin |
| `margin-bottom` | `margin-block-end` | Bottom margin | Bottom margin |
| `left: 0` | `inset-inline-start: 0` | Anchors to right edge | Anchors to left edge |
| `right: 0` | `inset-inline-end: 0` | Anchors to left edge | Anchors to right edge |
| `border-top-left-radius` | `border-start-start-radius` | Top-right corner in RTL | Top-left corner in LTR |

---

## Best Practices & Guidelines

### ✅ DO
* Rely on CSS grid and flexbox with CSS Logical Properties (`gap`, `margin-inline`, `padding-block`).
* Ensure mobile touch targets remain at least `44px × 44px` with appropriate outer spacing.
* Use `--dga-space-4` (`16px`) as your default baseline gap between inline elements.
* Scale section spacing up on desktop (`--dga-space-12` or `48px`) while keeping mobile compact (`--dga-space-6` or `24px`).

### ❌ DON'T
* Don't hardcode fixed widths on content containers (e.g., `width: 800px;`), use `max-width` and fluid percentage widths.
* Don't use `float: left` or `float: right` for positioning.
* Don't hardcode `margin-left` or `margin-right`; use `margin-inline-start` and `margin-inline-end`.


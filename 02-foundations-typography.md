# DGA Typography System

> Reference: https://design.dga.gov.sa/guidelines/foundations/typography

## Overview

The DGA typography framework is engineered for **Arabic-first bilingual harmony** (Arabic and English). It is built to ensure high legibility across all screen sizes, handle Arabic diacritics (*Tashkeel*) gracefully without clipping, and scale proportionally using relative units (`rem`) to adhere strictly to **WCAG 2.2 AA** accessibility standards.

---

## Approved Typefaces

### Primary Font Family (Bilingual)
* **Arabic Family:** `IBM Plex Sans Arabic`
* **English / Latin Family:** `IBM Plex Sans`
* **CSS Fallback Stack:**
```css
font-family: 'IBM Plex Sans Arabic', 'IBM Plex Sans', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
```

### Typeface Rationale
* **Harmonious Metrics:** `IBM Plex Sans Arabic` was selected because its x-height, stroke weight, and baseline metrics align precisely with `IBM Plex Sans` (Latin), eliminating layout jumping or visual inconsistency when switching languages.
* **Calligraphic Nuance & Modern Grotesque:** Balances traditional Naskh calligraphic legibility with geometric clarity for digital screens.
* **Diacritics Support:** Generous internal vertical metrics ensure diacritics (*Harakat / Tashkeel*) do not clip adjacent lines.

---

## Font Weights

To maintain visual clarity, cognitive comfort, and performance, the typography system restricts usage to three core weights:

| Weight Name | Numeric Value | Usage | CSS Variable |
|-------------|---------------|-------|--------------|
| **Regular** | `400` | Paragraphs, long-form content, standard body copy, helper text | `--dga-font-weight-regular` |
| **Medium / SemiBold** | `500` / `600` | Form labels, button text, table headers, emphasized copy, navigation items | `--dga-font-weight-medium` / `--dga-font-weight-semibold` |
| **Bold** | `700` | Headings (H1–H6), display titles, modal headers, major metric numbers | `--dga-font-weight-bold` |

---

## Modular Typography Scale

Calculated based on a default root size of `16px = 1rem`. All sizing must be specified in `rem` units to support browser zoom and accessibility scaling.

| Token | Element / Category | Size (rem) | Equivalent (px) | Line Height | Weight | Letter Spacing |
|-------|--------------------|------------|-----------------|-------------|--------|----------------|
| `--dga-text-display` | Hero Display | `3.00rem` | `48px` | `1.2 (3.6rem / 58px)` | `700` | `0` |
| `--dga-text-h1` | Heading 1 | `2.50rem` | `40px` | `1.25 (3.125rem / 50px)` | `700` | `0` |
| `--dga-text-h2` | Heading 2 | `2.00rem` | `32px` | `1.3 (2.6rem / 42px)` | `700` | `0` |
| `--dga-text-h3` | Heading 3 | `1.50rem` | `24px` | `1.35 (2.025rem / 32px)` | `700` | `0` |
| `--dga-text-h4` | Heading 4 | `1.25rem` | `20px` | `1.4 (1.75rem / 28px)` | `600` / `700` | `0` |
| `--dga-text-h5` | Heading 5 | `1.125rem` | `18px` | `1.45 (1.63rem / 26px)` | `600` | `0` |
| `--dga-text-h6` | Heading 6 | `1.00rem` | `16px` | `1.5 (1.5rem / 24px)` | `600` | `0` |
| `--dga-text-body-lg` | Lead Paragraph / Body Large | `1.125rem` | `18px` | `1.6 (1.8rem / 29px)` | `400` / `500` | `0` |
| `--dga-text-body-md` | Standard Body (Default) | `1.00rem` | `16px` | `1.6 (1.6rem / 26px)` | `400` | `0` |
| `--dga-text-body-sm` | Small Body / Secondary | `0.875rem` | `14px` | `1.5 (1.31rem / 21px)` | `400` / `500` | `0` |
| `--dga-text-caption` | Microcopy / Badge / Metadata | `0.75rem` | `12px` | `1.4 (1.05rem / 17px)` | `400` / `500` | `0` |

---

## Line Height (Leading) Rules for Arabic

> [!IMPORTANT]
> Arabic text requires **larger line heights (1.5 to 1.7)** compared to Latin text (1.3 to 1.5). Arabic ascenders, descenders, and optional vowel markings (*Tashkeel*) extend beyond Latin cap-heights. Setting tight line heights (`line-height: 1.1` or `1.2` on body text) causes severe visual clashing and illegibility.

* **Headings:** `1.2` to `1.35`
* **Body & Paragraphs:** `1.6` (Recommended standard)
* **Form Inputs & Single-line elements:** `1.5` with vertical padding

---

## Letter Spacing (Tracking) Rules

> [!WARNING]
> **Never set positive or negative letter-spacing on Arabic text.** Arabic is a cursive script where letters connect directly. Modifying `letter-spacing` breaks cursive connections (*Kashida/ligatures*) and degrades font rendering.
>
> If applying letter-spacing to English text, ensure it is scoped to `[lang="en"]` or `[dir="ltr"]` only.

```css
/* CORRECT */
:root {
  --dga-letter-spacing-ar: 0;
  --dga-letter-spacing-en: 0.01em;
}

[dir="rtl"] {
  letter-spacing: 0 !important;
}
```

---

## CSS Variables & Utility Classes

```css
:root {
  /* Font Families */
  --dga-font-family-base: 'IBM Plex Sans Arabic', 'IBM Plex Sans', system-ui, sans-serif;
  --dga-font-family-code: 'IBM Plex Mono', monospace;

  /* Font Weights */
  --dga-font-weight-regular: 400;
  --dga-font-weight-medium: 500;
  --dga-font-weight-semibold: 600;
  --dga-font-weight-bold: 700;

  /* Sizes */
  --dga-font-size-display: 3rem;       /* 48px */
  --dga-font-size-h1: 2.5rem;          /* 40px */
  --dga-font-size-h2: 2rem;            /* 32px */
  --dga-font-size-h3: 1.5rem;          /* 24px */
  --dga-font-size-h4: 1.25rem;         /* 20px */
  --dga-font-size-h5: 1.125rem;        /* 18px */
  --dga-font-size-h6: 1rem;            /* 16px */
  --dga-font-size-body-lg: 1.125rem;   /* 18px */
  --dga-font-size-body-md: 1rem;       /* 16px */
  --dga-font-size-body-sm: 0.875rem;   /* 14px */
  --dga-font-size-caption: 0.75rem;    /* 12px */

  /* Line Heights */
  --dga-line-height-tight: 1.25;
  --dga-line-height-normal: 1.5;
  --dga-line-height-loose: 1.6;
}

/* Typography Classes */
.govsa-display {
  font-family: var(--dga-font-family-base);
  font-size: var(--dga-font-size-display);
  font-weight: var(--dga-font-weight-bold);
  line-height: var(--dga-line-height-tight);
  color: var(--dga-text-primary);
}

.govsa-h1 {
  font-size: var(--dga-font-size-h1);
  font-weight: var(--dga-font-weight-bold);
  line-height: var(--dga-line-height-tight);
  color: var(--dga-text-primary);
  margin-block-end: 1rem;
}

.govsa-h2 {
  font-size: var(--dga-font-size-h2);
  font-weight: var(--dga-font-weight-bold);
  line-height: var(--dga-line-height-tight);
  color: var(--dga-text-primary);
  margin-block-end: 0.75rem;
}

.govsa-h3 {
  font-size: var(--dga-font-size-h3);
  font-weight: var(--dga-font-weight-bold);
  line-height: var(--dga-line-height-normal);
  color: var(--dga-text-primary);
  margin-block-end: 0.5rem;
}

.govsa-body {
  font-size: var(--dga-font-size-body-md);
  font-weight: var(--dga-font-weight-regular);
  line-height: var(--dga-line-height-loose);
  color: var(--dga-text-primary);
}

.govsa-body--secondary {
  color: var(--dga-text-secondary);
}

.govsa-caption {
  font-size: var(--dga-font-size-caption);
  font-weight: var(--dga-font-weight-regular);
  line-height: var(--dga-line-height-normal);
  color: var(--dga-text-secondary);
}
```

---

## Best Practices & Guidelines

### ✅ DO
* Use semantic heading tags (`<h1>` to `<h6>`) in hierarchical order without skipping levels.
* Use `rem` for font sizes so users can zoom up to 200% without breaking layouts.
* Keep body text line-height at `1.6` for optimal Arabic reading comfort.
* Use primary text color (`#0D121C`) for body text and headers to maintain AAA contrast.
* Ensure headings have clear margin separation from paragraphs (`margin-block-end`).

### ❌ DON'T
* Don't use font weights lighter than `400` (e.g. `100`, `200`, `300`) as they degrade severely on low-DPI displays.
* Don't justify Arabic text using CSS `text-align: justify;` without Arabic kashida engine support, as it introduces broken gaps.
* Don't hardcode font sizes in `px`.
* Don't apply custom letter-spacing to Arabic text.


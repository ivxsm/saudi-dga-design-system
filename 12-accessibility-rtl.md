# DGA Accessibility & RTL Mandates

> Reference: https://design.dga.gov.sa/guidelines/accessibility

## Overview

Accessibility and Arabic-first Right-to-Left (RTL) localization are legal prerequisites under Saudi digital government standards. All government entities are evaluated against the **Digital Experience Maturity Index** based on strict adherence to **WCAG 2.2 Level AA**.

---

## WCAG 2.2 Level AA Core Requirements

### 1. Color Contrast Ratios
* **Normal Text (< 18px / 14px bold):** Minimum **4.5:1** contrast ratio against its background.
* **Large Text (≥ 18px regular or ≥ 14px bold):** Minimum **3:1** contrast ratio.
* **User Interface Components & Graphical Objects:** Minimum **3:1** against adjacent backgrounds (borders, active states, focus indicators).
* **Color as Sole Identifier:** Never use color alone to convey meaning (e.g., pair error borders with text messages and exclamation icons).

### 2. Focus Indicators & Keyboard Navigation
* Every interactive element must be fully operable using keyboard alone (`Tab`, `Shift+Tab`, `Enter`, `Space`, `Arrow` keys, `Escape`).
* **Visible Focus Indicator:** Must be unmistakably visible with at least a **2px solid outline** and `2px` offset (`outline-offset: 2px`).
* **Logical Tab Sequence:** Tab sequence must strictly follow visual reading order (top-right to bottom-left in Arabic).

```css
/* Standard Compliant Focus Ring */
:focus-visible {
  outline: 2px solid var(--dga-primary);
  outline-offset: 2px;
}
```

### 3. Touch Targets (WCAG 2.5.8)
* All interactive targets (buttons, links, form inputs, checkboxes) must have a minimum target size of **44px × 44px** (or equivalent outer spacing) to accommodate touch input on mobile devices.

### 4. Text Resizing (WCAG 1.4.4)
* Content must scale up to **200%** without loss of content or functionality, and without requiring horizontal scrolling on desktop viewports. All font sizes must use relative units (`rem`).

### 5. Non-Text Content & Screen Readers
* Meaningful images must have descriptive `alt` text in Arabic.
* Decorative images must carry empty `alt=""` or `aria-hidden="true"`.
* Icon-only buttons must supply accessible names via `aria-label`.

---

## RTL (Right-to-Left) Localization Architecture

Saudi Platforms Code operates natively in RTL. Flipping from RTL to LTR must be achieved cleanly by changing the `dir` attribute on the root `<html>` element:

```html
<!-- Arabic Mode (Default) -->
<html lang="ar" dir="rtl">

<!-- English Mode -->
<html lang="en" dir="ltr">
```

### CSS Logical Properties Conversion Table

Always write CSS using logical properties rather than physical sides:

```css
/* ❌ FORBIDDEN (Breaks in bilingual toggles) */
.element {
  margin-left: 16px;
  padding-right: 24px;
  left: 0;
  text-align: right;
  border-left: 2px solid green;
}

/* ✅ MANDATORY DGA STANDARD */
.element {
  margin-inline-start: 16px;
  padding-inline-end: 24px;
  inset-inline-start: 0;
  text-align: start;
  border-inline-start: 2px solid var(--dga-primary);
}
```

---

## Handling Arabic Numerals & Diacritics

### Arabic Numerals
In Saudi digital government platforms, Eastern Arabic numerals (٠, ١, ٢, ٣...) or Western Arabic numerals (0, 1, 2, 3...) should remain consistent across a platform according to entity policy. For form inputs and transaction IDs, standard Western Arabic digits are often preferred for database querying.

### Diacritics (*Tashkeel*)
Arabic diacritics must never be clipped by tight line heights or overflow boundaries:
```css
/* Safeguard against Tashkeel clipping */
.govsa-arabic-text {
  line-height: 1.6;
  padding-block: 2px;
}
```

---

## Assistive Technology Patterns (ARIA)

| Component | Required ARIA Attributes |
|-----------|--------------------------|
| **Modal Dialog** | `role="dialog"`, `aria-modal="true"`, `aria-labelledby="[id]"`, `aria-describedby="[id]"` |
| **Accordion Trigger** | `aria-expanded="true/false"`, `aria-controls="[panel-id]"` |
| **Tabs** | `role="tablist"`, `role="tab"`, `aria-selected="true/false"`, `role="tabpanel"` |
| **Alerts / Live Updates**| `role="alert"` (errors), `role="status"` / `aria-live="polite"` (updates) |
| **Form Error** | `aria-invalid="true"`, `aria-describedby="[error-message-id]"` |
| **Expandable Menu** | `aria-haspopup="true"`, `aria-expanded="true/false"` |


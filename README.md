# Saudi DGA Unified Design System — Platforms Code (كود المنصات)

---

## Overview

A comprehensive, production-grade agent skill set and developer reference implementing the official **Unified Design System of Saudi Arabia (Platforms Code / كود المنصات)** mandated by the **Digital Government Authority (DGA)**.

🔗 **Official Guidelines Source:** [https://design.dga.gov.sa/guidelines](https://design.dga.gov.sa/guidelines)

This repository is engineered to serve two purposes:
1. **AI Agent Skill Set:** Directly ingestible and executable by AI coding assistants (such as Google Antigravity, Claude, Cursor, GitHub Copilot) to generate compliant Saudi government UI components and layouts.
2. **Developer Reference:** Complete technical specification containing design tokens, CSS variables, accessibility criteria, and code snippets across all foundations and components.

---

## Skill Set Structure

The repository is modularized into 13 specialized reference guides alongside the root agent manifest (`SKILL.md`):

| File | Category | Description |
|:---|:---|:---|
| [**`SKILL.md`**](./SKILL.md) | Agent Manifest | Agent Skill metadata, guidelines, and quick reference |
| [**`01-foundations-color.md`**](./01-foundations-color.md) | Foundations | National Green, Desert Gold, Lavender, neutrals, and WCAG contrast tokens |
| [**`02-foundations-typography.md`**](./02-foundations-typography.md) | Foundations | `IBM Plex Sans Arabic`, modular `rem` type scale, and line-height standards |
| [**`03-foundations-layout-spacing.md`**](./03-foundations-layout-spacing.md) | Foundations | 4px/8px mathematical scale, 12-column grid, breakpoints, and CSS logical properties |
| [**`04-foundations-elevation-radius.md`**](./04-foundations-elevation-radius.md) | Foundations | 5 elevation levels, border radii (`none` to `full`), and motion tokens |
| [**`05-components-actions.md`**](./05-components-actions.md) | Components | Buttons (Primary, Secondary, Outline, Ghost, Destructive), sizes, and icon handling |
| [**`06-components-forms.md`**](./06-components-forms.md) | Components | Inputs, textarea, select, checkboxes, radios, switches, file upload, and date picker |
| [**`07-components-navigation.md`**](./07-components-navigation.md) | Components | National header, 4-column footer, breadcrumbs, tabs, and pagination |
| [**`08-components-data-display.md`**](./08-components-data-display.md) | Components | Responsive data tables, service cards, badges, filter chips, and avatars |
| [**`09-components-feedback.md`**](./09-components-feedback.md) | Components | Alerts, toast notifications, accessible modal dialogs, and empty states |
| [**`10-components-layout.md`**](./10-components-layout.md) | Components | Accordions (single/multi-expand) and transactional step wizards |
| [**`11-patterns-templates.md`**](./11-patterns-templates.md) | Patterns | Portal homepage, service detail (66/33), wizard flow, and 404/500 error pages |
| [**`12-accessibility-rtl.md`**](./12-accessibility-rtl.md) | Accessibility | WCAG 2.2 AA mandates, 44px touch targets, 200% zoom, and screen reader ARIA |
| [**`13-developer-guide.md`**](./13-developer-guide.md) | Engineering | CSS tokens sheet, React 19 / Next.js setup, Tailwind config, and audit checklist |

---

## Core Visual Identity & Foundations

### 1. Color System
The palette draws symbolic inspiration from Saudi Arabia's heritage, landscapes, and national identity:
* **Primary Brand (National Green):** `#25935F` (Hover: `#188350`, Active: `#166A45`, Light Background: `#E8F5EE`)
* **Secondary Accent (Desert Gold):** `#F5BD02` (Inspired by the golden dunes of the Kingdom)
* **Secondary Accent (Lavender Purple):** `#80519F` (Inspired by *Al-Khuzamay* spring blossoms)
* **Prestige Dark & Gold (Bisht Cloak):** `#1A1A2E` and `#C9A84C`
* **Primary Text:** `#0D121C` (Achieves AAA 17.4:1 contrast ratio against white)

### 2. Typography
* **Primary Bilingual Typeface:** `IBM Plex Sans Arabic` paired with `IBM Plex Sans` for Latin text.
* **Relative Sizing:** All font sizes use `rem` units (base 16px) to support user-configured browser scaling.
* **Arabic Line Height (Leading):** Preserved at `1.6` for body text to prevent clipping of Arabic diacritics (*Tashkeel*).
* **Letter Spacing:** Zero tracking on Arabic cursive text to avoid disconnecting ligatures.

### 3. Layout & Spacing
* **4px / 8px Scale:** Standard mathematical spacing tokens (`--dga-space-1` [4px] through `--dga-space-24` [96px]).
* **12-Column Responsive Grid:** Fluid columns with responsive gutters scaling across 5 breakpoint tiers (`xs`, `sm`, `md`, `lg`, `xl`, `xxl`).
* **CSS Logical Properties:** Built layout-agnostic using `margin-inline`, `padding-block`, and `inset-inline` to seamlessly mirror between RTL (`dir="rtl"`) and LTR (`dir="ltr"`).

---

## Accessibility & RTL Mandates (WCAG 2.2 AA)

Compliance with national digital standards (including the *Digital Experience Maturity Index*) requires:
* **Strict Contrast Ratios:** Minimum **4.5:1** for regular text (< 18px) and **3:1** for large text and interactive UI borders.
* **Keyboard Navigation:** Unmistakable visible focus rings (`2px solid #25935F` with `2px` offset) and trapped focus inside modal dialogs.
* **Touch Targets:** Minimum physical touch dimension of **44px × 44px** on all mobile interactive elements.
* **Screen Reader Support:** Full ARIA role linkage (`role="dialog"`, `role="tablist"`, `aria-describedby`, `aria-live`).

---

## Installation & Developer Quick Start

### 1. Packages
```bash
# Official core Sass/CSS package
npm install govsa-ds

# React 19 component library & design tokens
npm install @dev-dga/react @dev-dga/css @dev-dga/tokens

# Bootstrap 5 theme wrapper
npm install sdga-ui
```

### 2. CSS Custom Properties
Import the stylesheet or inject tokens at your application's root:
```css
@import '@dev-dga/css';

:root {
  --dga-primary: #25935F;
  --dga-primary-hover: #188350;
  --dga-text-primary: #0D121C;
  --dga-font-family-base: 'IBM Plex Sans Arabic', 'IBM Plex Sans', system-ui, sans-serif;
  --dga-radius-md: 8px;
}
```

### 3. HTML / React Document Setup
Always ensure your document declares RTL direction by default:
```html
<!DOCTYPE html>
<html lang="ar" dir="rtl">
  <head>
    <meta charset="utf-8" />
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@400;500;600;700&display=swap" />
  </head>
  <body>
    <!-- Government Application Content -->
  </body>
</html>
```

---

## AI Agent Integration

This repository conforms to modern agent skill conventions (such as Google Antigravity, Cursor, Claude, and Copilot):

### Antigravity
Place this directory inside your customizations or skills folder:
```text
skills/saudi-dga-design-system/
```
The agent automatically indexes `SKILL.md` and references the individual specification files when creating or reviewing Saudi government platform code.

### Cursor / Claude / Copilot
Reference the skill in your project prompt:
```text
@saudi-dga-design-system Follow Saudi DGA Platforms Code guidelines for all colors, components, and RTL layout rules.
```

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](./LICENSE) file for details.

*Disclaimer: All logos, visual identity marks, and official platform specifications of Platforms Code (كود المنصات) belong to the Digital Government Authority (DGA) of Saudi Arabia.*

---
name: dga-design-system
description: >
  Comprehensive skill for building Saudi Digital Government Authority (DGA) compliant interfaces.
  Implements the official Platforms Code (كود المنصات) design system covering foundations,
  components, patterns, accessibility, and RTL/Arabic-first requirements.
  Reference: https://design.dga.gov.sa/guidelines
---

# DGA Design System — Saudi Platforms Code (كود المنصات)

> The official unified design system mandated by the Saudi Digital Government Authority (DGA) for all government digital platforms, portals, and services.

## Quick Reference

This skill set contains the following comprehensive guides:

| File | Description |
|------|-------------|
| [01-foundations-color.md](./01-foundations-color.md) | Color system, palette, tokens, and accessibility |
| [02-foundations-typography.md](./02-foundations-typography.md) | Typography scale, fonts, and text hierarchy |
| [03-foundations-layout-spacing.md](./03-foundations-layout-spacing.md) | Grid system, breakpoints, spacing scale |
| [04-foundations-elevation-radius.md](./04-foundations-elevation-radius.md) | Shadows, elevation, border radius, motion tokens |
| [05-components-actions.md](./05-components-actions.md) | Buttons, links, and action elements |
| [06-components-forms.md](./06-components-forms.md) | Inputs, selects, checkboxes, radios, switches, file upload, date picker |
| [07-components-navigation.md](./07-components-navigation.md) | Header, footer, breadcrumbs, tabs, pagination, side nav |
| [08-components-data-display.md](./08-components-data-display.md) | Tables, cards, badges, tags, avatars, tooltips, dividers |
| [09-components-feedback.md](./09-components-feedback.md) | Alerts, toasts, modals, progress, spinners, empty states |
| [10-components-layout.md](./10-components-layout.md) | Accordion, stepper, and layout containers |
| [11-patterns-templates.md](./11-patterns-templates.md) | Page templates, common patterns, error pages |
| [12-accessibility-rtl.md](./12-accessibility-rtl.md) | WCAG compliance, RTL/Arabic-first, keyboard nav, screen readers |
| [13-developer-guide.md](./13-developer-guide.md) | CSS architecture, tokens, packages, framework integration |

## Core Principles

1. **Arabic-First & RTL-Native** — All layouts built natively for `dir="rtl"` with seamless LTR toggle
2. **National Identity** — Colors and visual language derived from Saudi heritage (flag green, bisht gold, lavender)
3. **Accessibility (WCAG 2.2 AA)** — Mandatory contrast ratios, keyboard navigation, screen reader support
4. **Mobile-First Responsive** — Fluid layouts adapting from 320px mobile to 1440px+ desktop
5. **Design Token Architecture** — All values defined as CSS custom properties (`--dga-*`) for consistency
6. **BEM CSS Naming** — Components use `.govsa-` prefix with BEM methodology

## Installation

```bash
# Official core package
npm install govsa-ds

# Community React components (65+ components)
npm install @dev-dga/react @dev-dga/css @dev-dga/tokens

# Bootstrap-based theme
npm install sdga-ui
```

## How to Use This Skill

When building a DGA-compliant interface:

1. **Read the relevant foundation files first** (color, typography, layout)
2. **Reference component files** for specific UI elements
3. **Follow accessibility guidelines** from the accessibility file
4. **Use design tokens** — never hardcode colors, spacing, or typography values
5. **Test RTL/LTR** — always verify both Arabic and English layouts
6. **Validate contrast** — ensure WCAG 2.2 AA minimum compliance


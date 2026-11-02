# DGA Elevation, Border Radius & Motion System

> Reference: https://design.dga.gov.sa/guidelines/foundations

## Overview

Depth, shape, and animation in the DGA design system guide the user's attention, communicate interactivity, and separate overlapping spatial planes. All values are governed by strict token definitions to avoid visual clutter and maintain **WCAG 2.2** compliance.

---

## Border Radius Tokens

The DGA border radius scale standardizes rounding across all containers, inputs, cards, and modal components.

| Token | Value | Equivalent | Recommended Component Usage |
|-------|-------|------------|-----------------------------|
| `--dga-radius-none` | `0px` | `0` | Flat edges, full-width banners, tables, dividers |
| `--dga-radius-xs` | `2px` | `0.125rem` | Micro elements, progress bar indicators |
| `--dga-radius-sm` | `4px` | `0.25rem` | Checkboxes, tight badges, tooltips, tags |
| `--dga-radius-md` | `8px` | `0.5rem` | **Standard default:** Buttons, inputs, selects, dropdown menus |
| `--dga-radius-lg` | `12px` | `0.75rem` | Standard cards, alert banners, accordions |
| `--dga-radius-xl` | `16px` | `1.0rem` | Modals, dialog boxes, large containers, drawers |
| `--dga-radius-2xl`| `24px` | `1.5rem` | Promotional cards, featured highlight containers |
| `--dga-radius-full`| `9999px` | Pill / Circle | Circular avatars, pill badges, icon buttons, search pills |

```css
:root {
  --dga-radius-none: 0px;
  --dga-radius-xs: 2px;
  --dga-radius-sm: 4px;
  --dga-radius-md: 8px;
  --dga-radius-lg: 12px;
  --dga-radius-xl: 16px;
  --dga-radius-2xl: 24px;
  --dga-radius-full: 9999px;
}
```

---

## Elevation & Shadow Tokens

Elevation conveys depth and visual priority along the z-axis. DGA specifies 5 core elevation levels:

| Level | Token | Box-Shadow Value | Usage Scenario |
|-------|-------|------------------|----------------|
| **Elevation 0** | `--dga-shadow-none` | `none` | Resting flat elements, border-delimited cards |
| **Elevation 1** | `--dga-shadow-sm` | `0 1px 3px 0 rgba(13, 18, 28, 0.08), 0 1px 2px 0 rgba(13, 18, 28, 0.04)` | Subtle resting cards, table rows on hover |
| **Elevation 2** | `--dga-shadow-md` | `0 4px 6px -1px rgba(13, 18, 28, 0.08), 0 2px 4px -1px rgba(13, 18, 28, 0.04)` | Hovering cards, simple dropdown lists, popovers |
| **Elevation 3** | `--dga-shadow-lg` | `0 10px 15px -3px rgba(13, 18, 28, 0.08), 0 4px 6px -2px rgba(13, 18, 28, 0.04)` | Sticky navigation headers, autocomplete popups, tooltips |
| **Elevation 4** | `--dga-shadow-xl` | `0 20px 25px -5px rgba(13, 18, 28, 0.10), 0 10px 10px -5px rgba(13, 18, 28, 0.04)` | Modal dialogs, toast notifications, off-canvas drawers |
| **Elevation 5** | `--dga-shadow-2xl`| `0 25px 50px -12px rgba(13, 18, 28, 0.18)` | Full-screen overlays, system warning dialogs |

```css
:root {
  --dga-shadow-none: none;
  --dga-shadow-sm: 0 1px 3px 0 rgba(13, 18, 28, 0.08), 0 1px 2px 0 rgba(13, 18, 28, 0.04);
  --dga-shadow-md: 0 4px 6px -1px rgba(13, 18, 28, 0.08), 0 2px 4px -1px rgba(13, 18, 28, 0.04);
  --dga-shadow-lg: 0 10px 15px -3px rgba(13, 18, 28, 0.08), 0 4px 6px -2px rgba(13, 18, 28, 0.04);
  --dga-shadow-xl: 0 20px 25px -5px rgba(13, 18, 28, 0.10), 0 10px 10px -5px rgba(13, 18, 28, 0.04);
  --dga-shadow-2xl: 0 25px 50px -12px rgba(13, 18, 28, 0.18);
}
```

---

## Motion & Animation System

Animations on Saudi government portals must be **purposeful, restrained, and performance-oriented (60fps)**. Motion should guide the user's attention without slowing down task completion or causing cognitive distraction.

### Duration Tokens

| Token | Duration | Application |
|-------|----------|-------------|
| `--dga-duration-fast` | `150ms` (`0.15s`) | Micro-interactions: Button hover, focus rings, checkbox check, icon flips |
| `--dga-duration-normal` | `250ms` (`0.25s`) | Medium transitions: Dropdown expansion, accordion toggle, tooltips |
| `--dga-duration-slow` | `350ms` (`0.35s`) | Macro transitions: Modal open/close, off-canvas drawer slide, tab content fade |
| `--dga-duration-deliberate`| `500ms` (`0.50s`) | Complex layout transitions, page skeleton loaders |

### Easing Functions (Cubic-Bezier Curves)

| Token | Easing Curve | CSS Value | Behavior & Use Case |
|-------|--------------|-----------|---------------------|
| `--dga-ease-standard` | Standard / Ease-in-out | `cubic-bezier(0.4, 0.0, 0.2, 1)` | Elements remaining on-screen (size changes, button hover) |
| `--dga-ease-enter` | Decelerate / Ease-out | `cubic-bezier(0.0, 0.0, 0.2, 1)` | Elements entering viewport (modals sliding in, toast arrival) |
| `--dga-ease-exit` | Accelerate / Ease-in | `cubic-bezier(0.4, 0.0, 1, 1)` | Elements leaving viewport (dismissing alert, modal closing) |

```css
:root {
  --dga-duration-fast: 150ms;
  --dga-duration-normal: 250ms;
  --dga-duration-slow: 350ms;

  --dga-ease-standard: cubic-bezier(0.4, 0.0, 0.2, 1);
  --dga-ease-enter: cubic-bezier(0.0, 0.0, 0.2, 1);
  --dga-ease-exit: cubic-bezier(0.4, 0.0, 1, 1);
}
```

---

## Accessibility: Reduced Motion Mandate

> [!IMPORTANT]
> Under **WCAG 2.2 Criterion 2.3.3 (Animation from Interactions)** and Saudi DGA accessibility compliance, every portal must support `prefers-reduced-motion: reduce`. When detected, all animations, transforms, and transitions must immediately be disabled or converted into instant opacity changes.

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

---

## Directional Motion for RTL/LTR

Animations that move horizontally (drawers, sliding panels, tooltips) must flip directionally according to the document direction:

```css
/* Drawer sliding into view from page boundary */
[dir="rtl"] .govsa-drawer {
  transform: translateX(100%); /* Slides from right */
}

[dir="ltr"] .govsa-drawer {
  transform: translateX(-100%); /* Slides from left */
}

.govsa-drawer.govsa-drawer--open {
  transform: translateX(0);
  transition: transform var(--dga-duration-slow) var(--dga-ease-enter);
}
```


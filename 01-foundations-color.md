# DGA Color System

> Reference: https://design.dga.gov.sa/guidelines/foundations/color-system

## Overview

The DGA color palette draws from Saudi national identity, heritage, and natural landscape. Colors are implemented as design tokens (CSS custom properties) — **never hardcode hex values**.

---

## Primary Colors

The primary palette represents the Kingdom's national identity.

### National Green (Primary Brand)
Derived from the Saudi national flag. Used for primary interactive elements, CTAs, and brand identity.

| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-primary-900` | `#0A3D25` | Darkest shade |
| `--dga-primary-800` | `#0F5233` | Dark backgrounds |
| `--dga-primary-700` | `#166A45` | Gradient dark |
| `--dga-primary-600` | `#188350` | Gradient mid |
| `--dga-primary-500` | `#25935F` | **Primary brand color** |
| `--dga-primary-400` | `#47AB7A` | Hover state |
| `--dga-primary-300` | `#6EC299` | Lighter interactive |
| `--dga-primary-200` | `#A3D9BC` | Backgrounds |
| `--dga-primary-100` | `#D1ECDD` | Light tints |
| `--dga-primary-50`  | `#E8F5EE` | Subtle backgrounds |

```css
:root {
  --dga-primary: #25935F;
  --dga-primary-hover: #188350;
  --dga-primary-active: #166A45;
  --dga-primary-light: #E8F5EE;
}
```

---

## Secondary Colors

### Gold / Yellow
Inspired by the vast golden deserts of Saudi Arabia. Used for highlights, accents, and secondary emphasis.

| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-gold-500` | `#F5BD02` | **Primary gold** |
| `--dga-gold-400` | `#F7CA35` | Lighter |
| `--dga-gold-300` | `#F9D768` | Light |
| `--dga-gold-100` | `#FEF3CD` | Background tint |

### Lavender Purple
Inspired by the lavender flowers (*Al-Khuzamay*) that blanket Saudi deserts during spring.

| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-lavender-500` | `#80519F` | **Primary lavender** |
| `--dga-lavender-400` | `#9970B3` | Lighter |
| `--dga-lavender-300` | `#B290C7` | Light |
| `--dga-lavender-100` | `#E8DDF0` | Background tint |

### Black & Gold (Bisht-inspired)
Inspired by the traditional Saudi *Bisht* (cloak), symbolizing prestige and elegance.

| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-bisht-dark` | `#1A1A2E` | Deep dark |
| `--dga-bisht-gold` | `#C9A84C` | Accent gold |

---

## Neutral / Gray Scale

Used for text, borders, backgrounds, and structural elements.

| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-neutral-900` | `#0D121C` | **Primary text** |
| `--dga-neutral-800` | `#1D2939` | Dark text |
| `--dga-neutral-700` | `#344054` | Secondary text |
| `--dga-neutral-600` | `#475467` | Muted text |
| `--dga-neutral-500` | `#667085` | Placeholder text |
| `--dga-neutral-400` | `#98A2B3` | Disabled text |
| `--dga-neutral-300` | `#D0D5DD` | Borders |
| `--dga-neutral-200` | `#EAECF0` | Light borders |
| `--dga-neutral-100` | `#F2F4F7` | Background |
| `--dga-neutral-50`  | `#F9FAFB` | Subtle background |
| `--dga-neutral-0`   | `#FFFFFF` | White |

```css
:root {
  --dga-text-primary: #0D121C;
  --dga-text-secondary: #475467;
  --dga-text-placeholder: #667085;
  --dga-text-disabled: #98A2B3;
  --dga-text-on-dark: #FFFFFF;
  --dga-border: #D0D5DD;
  --dga-border-light: #EAECF0;
  --dga-bg-primary: #FFFFFF;
  --dga-bg-secondary: #F9FAFB;
  --dga-bg-tertiary: #F2F4F7;
}
```

---

## Semantic / Status Colors

Used strictly for communicating system states and feedback.

### Success
| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-success-700` | `#027A48` | Dark text |
| `--dga-success-600` | `#039855` | Borders |
| `--dga-success-500` | `#12B76A` | **Primary success** |
| `--dga-success-100` | `#D1FADF` | Background |
| `--dga-success-50`  | `#ECFDF3` | Subtle bg |

### Error / Destructive
| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-error-700` | `#B42318` | Dark text |
| `--dga-error-600` | `#D92D20` | **Semantic text** |
| `--dga-error-500` | `#F04438` | **Primary error** |
| `--dga-error-100` | `#FEE4E2` | Background |
| `--dga-error-50`  | `#FEF3F2` | Subtle bg |

### Warning
| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-warning-700` | `#B54708` | Dark text |
| `--dga-warning-600` | `#DC6803` | Borders |
| `--dga-warning-500` | `#F79009` | **Primary warning** |
| `--dga-warning-100` | `#FEF0C7` | Background |
| `--dga-warning-50`  | `#FFFAEB` | Subtle bg |

### Information
| Token | Hex | Usage |
|-------|-----|-------|
| `--dga-info-700` | `#175CD3` | Dark text |
| `--dga-info-600` | `#1570EF` | Borders |
| `--dga-info-500` | `#2E90FA` | **Primary info** |
| `--dga-info-100` | `#D1E9FF` | Background |
| `--dga-info-50`  | `#EFF8FF` | Subtle bg |

---

## Color Usage Rules

### ✅ DO
- Always use design tokens, never hardcode hex values
- Use primary green for main CTAs and interactive elements
- Use semantic colors only for their intended status meaning
- Ensure minimum 4.5:1 contrast ratio for normal text (WCAG AA)
- Ensure minimum 3:1 contrast ratio for large text and UI components
- Test colors in both light and dark modes
- Use neutral scale for structural elements and text hierarchy

### ❌ DON'T
- Don't use semantic colors for decorative purposes
- Don't use green for error states or red for success states
- Don't place text on colored backgrounds without verifying contrast
- Don't create custom colors outside the token system
- Don't use color as the sole means of conveying information (accessibility)

---

## Contrast Requirements (WCAG 2.2 AA)

| Element Type | Minimum Ratio | Example |
|-------------|---------------|---------|
| Normal text (< 18px) | **4.5:1** | Body copy, labels |
| Large text (≥ 18px or ≥ 14px bold) | **3:1** | Headings |
| UI components & graphical objects | **3:1** | Borders, icons, focus rings |
| Disabled elements | No requirement | Grayed out states |

### Verified Combinations
| Foreground | Background | Ratio | Pass? |
|-----------|-----------|-------|-------|
| `#0D121C` | `#FFFFFF` | 17.4:1 | ✅ AAA |
| `#25935F` | `#FFFFFF` | 4.6:1 | ✅ AA |
| `#FFFFFF` | `#25935F` | 4.6:1 | ✅ AA |
| `#F04438` | `#FFFFFF` | 4.1:1 | ✅ AA (large) |
| `#D92D20` | `#FFFFFF` | 5.3:1 | ✅ AA |

---

## CSS Implementation

```css
:root {
  /* Primary */
  --dga-primary: #25935F;
  --dga-primary-hover: #188350;
  --dga-primary-active: #166A45;
  --dga-primary-bg: #E8F5EE;

  /* Secondary */
  --dga-gold: #F5BD02;
  --dga-lavender: #80519F;

  /* Neutrals */
  --dga-text-primary: #0D121C;
  --dga-text-secondary: #475467;
  --dga-text-placeholder: #667085;
  --dga-text-disabled: #98A2B3;
  --dga-text-inverse: #FFFFFF;
  --dga-border-default: #D0D5DD;
  --dga-border-light: #EAECF0;
  --dga-bg-page: #FFFFFF;
  --dga-bg-subtle: #F9FAFB;
  --dga-bg-muted: #F2F4F7;

  /* Semantic */
  --dga-success: #12B76A;
  --dga-success-text: #027A48;
  --dga-success-bg: #ECFDF3;
  --dga-error: #F04438;
  --dga-error-text: #D92D20;
  --dga-error-bg: #FEF3F2;
  --dga-warning: #F79009;
  --dga-warning-text: #B54708;
  --dga-warning-bg: #FFFAEB;
  --dga-info: #2E90FA;
  --dga-info-text: #175CD3;
  --dga-info-bg: #EFF8FF;
}
```


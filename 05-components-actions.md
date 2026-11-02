# DGA Components: Actions (Buttons & Links)

> Reference: https://design.dga.gov.sa/guidelines/components/actions/buttons

## Overview

Action components allow users to execute commands, submit transactional data, or navigate across views. Under DGA Platforms Code, buttons follow strict hierarchy levels (high, medium, low emphasis), maintain high contrast ratios (minimum 4.5:1), and feature accessible focus indicators for keyboard navigation.

---

## Button Hierarchy Variants

| Variant | Class Name | Visual Treatment | Intended Role |
|---------|------------|------------------|---------------|
| **Primary** | `.govsa-button--primary` | Solid National Green background (`#25935F`), white text | Main call-to-action (one per view, e.g., "Submit Application", "Pay Fees") |
| **Secondary** | `.govsa-button--secondary` | Subtle tint / neutral border | Supporting action (e.g., "Save Draft", "Export PDF") |
| **Outline** | `.govsa-button--outline` | Transparent fill, 1.5px green/neutral border | Neutral alternative (e.g., "Filter", "View Details") |
| **Ghost** | `.govsa-button--ghost` | Transparent fill, no border, hover background | Low-emphasis inline action (e.g., "Cancel", "Back") |
| **Destructive** | `.govsa-button--destructive` | Solid or outline semantic red (`#F04438`) | Irreversible operations (e.g., "Delete Record", "Revoke License") |
| **Link Button** | `.govsa-button--link` | Underlined text appearance, button semantics | Auxiliary inline actions |

---

## Button Sizing Scale

Touch targets must never fall below `44px × 44px` for mobile accessibility (WCAG 2.5.5 / 2.5.8).

| Size | Class Name | Height | Horizontal Padding | Font Size | Icon Size | Target Use Case |
|------|------------|--------|--------------------|-----------|-----------|-----------------|
| **Large (LG)** | `.govsa-button--lg` | `48px` (`3rem`) | `24px` (`1.5rem`) | `1.125rem` (`18px`) | `20px` | Hero sections, key transactional checkpoints |
| **Medium (MD)** | `.govsa-button--md` | `40px` (`2.5rem`) | `16px` (`1.0rem`) | `1.000rem` (`16px`) | `18px` | **Default:** Standard forms, card actions |
| **Small (SM)** | `.govsa-button--sm` | `32px` (`2.0rem`) | `12px` (`0.75rem`) | `0.875rem` (`14px`) | `16px` | Compact tables, toolbars, search bars |

---

## Button States & Visual Specifications

All buttons must implement seven distinct visual states:

1. **Default:** Crisp baseline styling with standard colors and elevation.
2. **Hover:** Slight color darkening or background tint shift (using `--dga-primary-hover` / `#188350`).
3. **Focus-Visible:** Mandatory accessible focus ring: `2px solid #25935F` with `2px` offset (`outline-offset: 2px`).
4. **Active (Pressed):** Darker active shade (`#166A45`), slight inset depression.
5. **Disabled:** Opacity reduced to `0.5`, background muted (`#EAECF0`), cursor set to `not-allowed`, pointer events disabled.
6. **Loading:** Spinner replaces or sits beside text; button retains original width, `aria-busy="true"` applied.
7. **Selected / Toggle:** Solid filled state with `aria-pressed="true"`.

---

## RTL & Icon Handling

When combining an icon with button text:
* In Arabic (`dir="rtl"`), the leading icon sits on the **right** side of the text, with an inline margin of `8px` (`--dga-space-2`).
* In English (`dir="ltr"`), the leading icon sits on the **left** side of the text.
* Trailing arrows (indicating forward progression) automatically point left in RTL and right in LTR.

```html
<!-- Leading Icon in RTL: Icon displays to the right of text -->
<button class="govsa-button govsa-button--primary govsa-button--md" type="button">
  <svg class="govsa-button__icon" aria-hidden="true" focusable="false" width="18" height="18" viewBox="0 0 24 24">
    <!-- SVG path -->
  </svg>
  <span>تقديم الطلب</span>
</button>

<!-- Trailing Next Arrow in RTL: Arrow points Leftwards (Unicode ←) -->
<button class="govsa-button govsa-button--secondary govsa-button--md" type="button">
  <span>التالي</span>
  <svg class="govsa-button__icon" aria-hidden="true" focusable="false" width="18" height="18" viewBox="0 0 24 24">
    <path d="M14 7l-5 5 5 5V7z"/>
  </svg>
</button>
```

---

## Icon-Only Buttons

Buttons without visible text labels must include an accessible label via `aria-label`:

```html
<button class="govsa-button govsa-button--icon govsa-button--ghost" type="button" aria-label="إغلاق النافذة">
  <svg aria-hidden="true" width="20" height="20" viewBox="0 0 24 24">
    <path d="M19 6.41L17.59 5 12 10.59 6.41 5 5 6.41 10.59 12 5 17.59 6.41 19 12 13.41 17.59 19 19 17.59 13.41 12z"/>
  </svg>
</button>
```

---

## CSS Implementation

```css
/* Base Button Styling */
.govsa-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--dga-space-2);
  border-radius: var(--dga-radius-md);
  font-family: var(--dga-font-family-base);
  font-weight: var(--dga-font-weight-medium);
  text-decoration: none;
  cursor: pointer;
  white-space: nowrap;
  border: 1px solid transparent;
  transition: background-color var(--dga-duration-fast) var(--dga-ease-standard),
              border-color var(--dga-duration-fast) var(--dga-ease-standard),
              color var(--dga-duration-fast) var(--dga-ease-standard),
              box-shadow var(--dga-duration-fast) var(--dga-ease-standard);
  user-select: none;
}

/* Accessible Focus Ring */
.govsa-button:focus-visible {
  outline: 2px solid var(--dga-primary);
  outline-offset: 2px;
}

/* Primary Variant */
.govsa-button--primary {
  background-color: var(--dga-primary);
  color: #FFFFFF;
}
.govsa-button--primary:hover:not(:disabled) {
  background-color: var(--dga-primary-hover);
}
.govsa-button--primary:active:not(:disabled) {
  background-color: var(--dga-primary-active);
}

/* Secondary Variant */
.govsa-button--secondary {
  background-color: var(--dga-neutral-100);
  border-color: var(--dga-border-default);
  color: var(--dga-text-primary);
}
.govsa-button--secondary:hover:not(:disabled) {
  background-color: var(--dga-neutral-200);
  border-color: var(--dga-neutral-400);
}

/* Outline Variant */
.govsa-button--outline {
  background-color: transparent;
  border-color: var(--dga-primary);
  color: var(--dga-primary);
}
.govsa-button--outline:hover:not(:disabled) {
  background-color: var(--dga-primary-bg);
}

/* Destructive Variant */
.govsa-button--destructive {
  background-color: var(--dga-error);
  color: #FFFFFF;
}
.govsa-button--destructive:hover:not(:disabled) {
  background-color: var(--dga-error-text);
}

/* Disabled State */
.govsa-button:disabled,
.govsa-button[aria-disabled="true"] {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

/* Sizing Modifiers */
.govsa-button--lg {
  min-height: 48px;
  padding-inline: var(--dga-space-6);
  font-size: var(--dga-font-size-body-lg);
}
.govsa-button--md {
  min-height: 40px;
  padding-inline: var(--dga-space-4);
  font-size: var(--dga-font-size-body-md);
}
.govsa-button--sm {
  min-height: 32px;
  padding-inline: var(--dga-space-3);
  font-size: var(--dga-font-size-body-sm);
}

/* Icon-only Button */
.govsa-button--icon.govsa-button--md {
  width: 40px;
  padding: 0;
}
```

---

## Best Practices & Guidelines

### ✅ DO
* Have only **one primary action button** in a form or dialog view to avoid cognitive paralysis.
* Position primary actions on the right in Arabic layouts (following RTL reading direction).
* Always provide an `aria-label` for icon-only buttons.
* Maintain minimum touch target size of 44px on mobile devices.

### ❌ DON'T
* Don't use primary green styling for secondary or cancellation actions.
* Don't disable buttons without providing accessible feedback (tooltips or inline error explanations).
* Don't wrap buttons inside anchor tags (`<a><button>...</button></a>`).


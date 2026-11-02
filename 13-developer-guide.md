# DGA Developer & Implementation Guide

> Reference: https://design.dga.gov.sa/guidelines

## Overview

This guide details the technical implementation, package installation, CSS architecture, and framework integrations for developing Saudi DGA-compliant applications.

---

## Package Ecosystem

Depending on your application stack, install the official or community packages:

### 1. Official Core Sass/CSS Package
```bash
npm install govsa-ds
```

### 2. React 19 Component Library & Tokens
The modern component ecosystem providing 65+ accessible React components with native RTL:
```bash
npm install @dev-dga/react @dev-dga/css @dev-dga/tokens
```

### 3. Bootstrap 5 Theme Wrapper
```bash
npm install sdga-ui
```

---

## CSS Architecture & BEM Methodology

DGA stylesheets utilize a strict BEM (Block Element Modifier) naming convention with the `.govsa-` namespace prefix to prevent CSS conflicts across government web properties.

```css
/* Block */
.govsa-card { }

/* Elements */
.govsa-card__header { }
.govsa-card__title { }
.govsa-card__body { }
.govsa-card__footer { }

/* Modifiers */
.govsa-card--interactive { }
.govsa-card--elevated { }
```

---

## Global CSS Tokens (`tokens.css`)

Drop this foundational stylesheet at your application's root:

```css
:root {
  /* Brand Colors */
  --dga-primary-900: #0A3D25;
  --dga-primary-700: #166A45;
  --dga-primary: #25935F;
  --dga-primary-hover: #188350;
  --dga-primary-active: #166A45;
  --dga-primary-bg: #E8F5EE;

  /* Secondary Accents */
  --dga-gold: #F5BD02;
  --dga-lavender: #80519F;

  /* Neutrals */
  --dga-text-primary: #0D121C;
  --dga-text-secondary: #475467;
  --dga-text-placeholder: #667085;
  --dga-text-disabled: #98A2B3;
  --dga-border-default: #D0D5DD;
  --dga-border-light: #EAECF0;
  --dga-bg-page: #FFFFFF;
  --dga-bg-subtle: #F9FAFB;
  --dga-bg-muted: #F2F4F7;

  /* Semantic Feedback */
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

  /* Typography */
  --dga-font-family-base: 'IBM Plex Sans Arabic', 'IBM Plex Sans', system-ui, sans-serif;
  --dga-font-weight-regular: 400;
  --dga-font-weight-medium: 500;
  --dga-font-weight-bold: 700;

  /* Spacing Scale (8px/4px base) */
  --dga-space-1: 0.25rem;  /* 4px */
  --dga-space-2: 0.5rem;   /* 8px */
  --dga-space-3: 0.75rem;  /* 12px */
  --dga-space-4: 1.0rem;   /* 16px */
  --dga-space-5: 1.25rem;  /* 20px */
  --dga-space-6: 1.5rem;   /* 24px */
  --dga-space-8: 2.0rem;   /* 32px */
  --dga-space-12: 3.0rem;  /* 48px */
  --dga-space-16: 4.0rem;  /* 64px */

  /* Border Radii */
  --dga-radius-sm: 4px;
  --dga-radius-md: 8px;
  --dga-radius-lg: 12px;
  --dga-radius-xl: 16px;
  --dga-radius-full: 9999px;

  /* Elevation Shadows */
  --dga-shadow-sm: 0 1px 3px 0 rgba(13, 18, 28, 0.08), 0 1px 2px 0 rgba(13, 18, 28, 0.04);
  --dga-shadow-md: 0 4px 6px -1px rgba(13, 18, 28, 0.08), 0 2px 4px -1px rgba(13, 18, 28, 0.04);
  --dga-shadow-lg: 0 10px 15px -3px rgba(13, 18, 28, 0.08), 0 4px 6px -2px rgba(13, 18, 28, 0.04);
  --dga-shadow-xl: 0 20px 25px -5px rgba(13, 18, 28, 0.10), 0 10px 10px -5px rgba(13, 18, 28, 0.04);
}
```

---

## React / Next.js Setup

### 1. Root Layout (`app/layout.tsx`)
```tsx
import type { Metadata } from 'next';
import '@dev-dga/css';
import './globals.css';

export const metadata: Metadata = {
  title: 'بوابة الخدمات الحكومية | المنصة الوطنية',
  description: 'منصة الخدمات الرقمية المتكاملة لحكومة المملكة العربية السعودية',
};

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="ar" dir="rtl">
      <head>
        <link rel="preconnect" href="https://fonts.googleapis.com" />
        <link
          rel="stylesheet"
          href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Arabic:wght@400;500;600;700&display=swap"
        />
      </head>
      <body>{children}</body>
    </html>
  );
}
```

### 2. Utilizing React Components (`page.tsx`)
```tsx
'use client';

import { useState } from 'react';

export default function ServicePage() {
  const [loading, setLoading] = useState(false);

  return (
    <main className="govsa-container" style={{ paddingBlock: 'var(--dga-space-8)' }}>
      <div className="govsa-card govsa-card--elevated" style={{ maxWidth: '640px', marginInline: 'auto' }}>
        <div className="govsa-card__body">
          <h1 className="govsa-h2">تقديم طلب رخصة جديدة</h1>
          <p className="govsa-body govsa-body--secondary">
            يرجى تعبئة الحقول أدناه بدقة للبدء في إجراءات التحقق وإصدار الوثيقة.
          </p>

          <div className="govsa-form-group">
            <label htmlFor="cr-number" className="govsa-label">
              رقم السجل التجاري <span className="govsa-label__required">*</span>
            </label>
            <input
              id="cr-number"
              type="text"
              className="govsa-input"
              placeholder="1010XXXXXX"
              maxLength={10}
            />
          </div>

          <div className="govsa-form-actions" style={{ display: 'flex', gap: 'var(--dga-space-3)' }}>
            <button
              type="button"
              className="govsa-button govsa-button--primary govsa-button--md"
              disabled={loading}
              onClick={() => setLoading(true)}
            >
              {loading ? 'جاري التحقق...' : 'متابعة الإجراء'}
            </button>
            <button type="button" className="govsa-button govsa-button--ghost govsa-button--md">
              إلغاء
            </button>
          </div>
        </div>
      </div>
    </main>
  );
}
```

---

## Tailwind CSS Configuration (`tailwind.config.js`)

If using Tailwind, bridge the DGA tokens directly into Tailwind's theme:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./app/**/*.{js,ts,jsx,tsx}', './components/**/*.{js,ts,jsx,tsx}'],
  theme: {
    extend: {
      colors: {
        dga: {
          primary: {
            DEFAULT: 'var(--dga-primary)',
            hover: 'var(--dga-primary-hover)',
            active: 'var(--dga-primary-active)',
            bg: 'var(--dga-primary-bg)',
          },
          gold: 'var(--dga-gold)',
          lavender: 'var(--dga-lavender)',
          neutral: {
            text: 'var(--dga-text-primary)',
            muted: 'var(--dga-text-secondary)',
            border: 'var(--dga-border-default)',
            page: 'var(--dga-bg-page)',
            subtle: 'var(--dga-bg-subtle)',
          },
          error: {
            DEFAULT: 'var(--dga-error)',
            text: 'var(--dga-error-text)',
            bg: 'var(--dga-error-bg)',
          },
          success: {
            DEFAULT: 'var(--dga-success)',
            text: 'var(--dga-success-text)',
            bg: 'var(--dga-success-bg)',
          },
        },
      },
      fontFamily: {
        sans: ['var(--dga-font-family-base)'],
      },
      borderRadius: {
        dga: 'var(--dga-radius-md)',
        'dga-lg': 'var(--dga-radius-lg)',
        'dga-xl': 'var(--dga-radius-xl)',
      },
    },
  },
  plugins: [],
};
```

---

## Pre-Deployment Compliance Checklist

Before submitting a government platform for the **Digital Experience Maturity Index** audit:

- [ ] **RTL Native:** Document declares `<html lang="ar" dir="rtl">`.
- [ ] **Contrast Pass:** All text elements meet or exceed 4.5:1 contrast against backgrounds.
- [ ] **Focus Visible:** Focused buttons, links, and inputs show 2px solid outline with 2px offset.
- [ ] **Touch Targets:** All interactive mobile targets measure at least 44px × 44px.
- [ ] **Typography Scale:** Font sizes defined in `rem` and line heights on Arabic body text set to `1.6`.
- [ ] **Zoom Test:** Page zoomed to 200% displays all content with zero horizontal scroll breakage.
- [ ] **Screen Reader Labels:** All icon buttons and graphic elements include `aria-label` or `alt` attributes.
- [ ] **Reduced Motion:** Portals respect `prefers-reduced-motion: reduce`.


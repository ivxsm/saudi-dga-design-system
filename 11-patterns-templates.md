# DGA Patterns & Page Templates

> Reference: https://design.dga.gov.sa/guidelines/patterns

## Overview

Patterns represent standardized, reusable solutions to common user tasks and full-page structures across Saudi government websites. Adhering to these patterns ensures citizens experience predictable, intuitive interactions across all government entities.

---

## 1. Portal Homepage Pattern

The standard blueprint for a Saudi government ministry, agency, or authority portal.

### Visual Hierarchy
1. **Header & Utility Bar:** National branding, accessibility tools, language switcher, Nafath login.
2. **Hero Section with Unified Search:** High-impact banner, search input with popular search tags.
3. **Featured Digital Services Grid:** 4 to 8 top citizen/business services formatted as interactive service cards.
4. **Statistics & National Impact:** Key metric cards highlighting digital maturity, completed transactions.
5. **News & Media Center:** Latest announcements, circulars, and events.
6. **National Footer:** Vision 2030 branding, legal policies, unified government links.

---

## 2. Service Detail Page Pattern (بطاقة الخدمة الإلكترونية)

Every electronic service listed on a government portal must follow this unified information structure:

```text
┌────────────────────────────────────────────────────────────────────────┐
│ Breadcrumb: الرئيسية > الخدمات الإلكترونية > إصدار شهادة المنشأ         │
├────────────────────────────────────────────────────────────────────────┤
│ Title: إصدار شهادة المنشأ الرقمية                   [ابدأ الخدمة الآن] │
│ Subtitle / Summary: خدمة تتيح للمصانع استخراج شهادات المنشأ آلياً      │
├───────────────────────────────────┬────────────────────────────────────┤
│ Main Column (66% Width)           │ Metadata Sidebar (33% Width)       │
│                                   │                                    │
│ • متطلبات الخدمة المسبقة          │ • وقت الاستجابة: فوري (خلال 5 دقائق)│
│ • المستندات والشروط               │ • رسوم الخدمة: 100 ر.س             │
│ • خطوات التقديم (1, 2, 3)         │ • الفئة المستهدفة: قطاع الأعمال    │
│ • قنوات تقديم الخدمة              │ • قنوات الدفع: سداد / مدى          │
│ • الأسئلة الشائعة (Accordion)     │ • خدمة العملاء: 19999              │
└───────────────────────────────────┴────────────────────────────────────┘
```

---

## 3. Transactional Multi-Step Wizard Pattern (معالج المعاملات)

Used for multi-step service applications, registrations, and payment flows.

### Structural Flow
1. **Header with Save & Exit:** Provides an option to save progress and return later.
2. **Stepper Indicator:** Shows total milestones (e.g. Step 2 of 4) and active stage title.
3. **Form Container:** Single-column layout (max width `720px`) for focused input completion.
4. **Action Footer:**
   * **Primary Button (Right in RTL):** "التالي وحفظ" (Next & Save).
   * **Secondary Button (Left of Primary):** "السابق" (Previous).
   * **Ghost Button (Far Left in RTL):** "إلغاء الطلب" (Cancel Application).

---

## 4. Search & Filter Results Pattern

Standard layout for finding services, regulations, open data, or tenders.

### Grid Anatomy
* **Desktop Layout:**
  * **Sidebar (Right in RTL - 25% Width):** Faceted filters (Entity, Category, Date, Status, Fee type) with "تطبيق الفلاتر" (Apply) and "إعادة ضبط" (Reset) buttons.
  * **Main Content Area (75% Width):**
    * Top bar: Total count ("تم العثور على 48 خدمة"), active filter tags (removable chips), sorting dropdown.
    * Result Cards List: Vertical cards with service title, excerpt, metadata badges, and direct links.
    * Bottom: DGA pagination component.

---

## 5. System Error Page Templates

Standardized error layouts that maintain institutional trust and offer clear recovery pathways.

### 404 — Page Not Found (الصفحة غير موجودة)
```html
<main class="govsa-error-page">
  <div class="govsa-container govsa-text-center">
    <div class="govsa-error-page__code">404</div>
    <h1 class="govsa-error-page__title">عذراً، الصفحة المطلوبة غير موجودة</h1>
    <p class="govsa-error-page__desc">
      ربما تم نقل الصفحة، أو تم حذفها، أو أن الرابط الذي استخدمته غير صحيح.
    </p>
    <div class="govsa-error-page__actions">
      <a href="/" class="govsa-button govsa-button--primary govsa-button--md">العودة إلى الصفحة الرئيسية</a>
      <a href="/search" class="govsa-button govsa-button--outline govsa-button--md">البحث في المنصة</a>
    </div>
  </div>
</main>
```

### 500 — Server Error (خطأ غير متوقع في النظام)
```html
<main class="govsa-error-page">
  <div class="govsa-container govsa-text-center">
    <div class="govsa-error-page__code govsa-error-page__code--server">500</div>
    <h1 class="govsa-error-page__title">نعتذر، حدث خطأ غير متوقع في الخادم</h1>
    <p class="govsa-error-page__desc">
      يقوم فريق الدعم الفني بالعمل على حل المشكلة حالياً. يرجى المحاولة مرة أخرى بعد بضع دقائق.
    </p>
    <div class="govsa-error-page__actions">
      <button type="button" onclick="window.location.reload()" class="govsa-button govsa-button--primary govsa-button--md">
        إعادة تحديث الصفحة
      </button>
      <a href="/contact" class="govsa-button govsa-button--ghost govsa-button--md">الإبلاغ عن المشكلة</a>
    </div>
  </div>
</main>
```


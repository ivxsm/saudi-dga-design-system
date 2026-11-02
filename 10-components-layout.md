# DGA Components: Layout Containers (Accordion & Stepper)

> Reference: https://design.dga.gov.sa/guidelines/components

## Overview

Layout components structure complex, multi-stage, or hierarchical content into orderly visual modules. Under DGA Platforms Code, accordions minimize visual clutter in dense informational sections (like FAQs), while steppers guide citizens step-by-step through government transactional services.

---

## 1. Accordion (`.govsa-accordion`)

Collapsible vertically stacked panels used to group related content without overwhelming the viewport.

### Architecture & Interaction
* **Trigger Header:** High-contrast text label paired with a directional chevron that rotates 180° when expanded.
* **Content Panel:** Reveals formatted copy, tables, or sub-forms upon expansion.
* **Single vs Multi-Expand:** Can be configured to allow only one panel open at a time, or multiple simultaneous panels.

> [!WARNING]
> **Strict Rule:** Never nest an accordion inside another accordion. Nested accordions create severe cognitive friction and cause keyboard focus trapping issues.

### HTML Structure
```html
<div class="govsa-accordion" data-allow-multiple="false">
  <!-- Accordion Item 1 (Expanded) -->
  <div class="govsa-accordion__item govsa-accordion__item--expanded">
    <h3 class="govsa-accordion__heading">
      <button
        type="button"
        id="acc-header-1"
        class="govsa-accordion__trigger"
        aria-expanded="true"
        aria-controls="acc-panel-1"
      >
        <span class="govsa-accordion__title">ما هي المستندات المطلوبة لإصدار السجل التجاري؟</span>
        <svg class="govsa-accordion__icon" aria-hidden="true" width="20" height="20" viewBox="0 0 24 24">
          <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/>
        </svg>
      </button>
    </h3>
    <div id="acc-panel-1" class="govsa-accordion__panel" role="region" aria-labelledby="acc-header-1">
      <p>
        يتطلب إصدار السجل التجاري وجود حساب مفعل في منصة أبشر، وألا يقل عمر المتقدم عن 18 عاماً، مع سداد المقابل المالي المقرر نظاماً عبر نظام سداد.
      </p>
    </div>
  </div>

  <!-- Accordion Item 2 (Collapsed) -->
  <div class="govsa-accordion__item">
    <h3 class="govsa-accordion__heading">
      <button
        type="button"
        id="acc-header-2"
        class="govsa-accordion__trigger"
        aria-expanded="false"
        aria-controls="acc-panel-2"
      >
        <span class="govsa-accordion__title">كم يستغرق وقت معالجة الطلب؟</span>
        <svg class="govsa-accordion__icon" aria-hidden="true" width="20" height="20" viewBox="0 0 24 24">
          <path d="M7.41 8.59L12 13.17l4.59-4.58L18 10l-6 6-6-6 1.41-1.41z"/>
        </svg>
      </button>
    </h3>
    <div id="acc-panel-2" class="govsa-accordion__panel" role="region" aria-labelledby="acc-header-2" hidden>
      <p>
        تتم معالجة الطلبات وإصدار السجل إلكترونياً وبشكل فوري فور التحقق من استيفاء المتطلبات وسداد الفاتورة.
      </p>
    </div>
  </div>
</div>
```

---

## 2. Stepper / Process Wizard (`.govsa-stepper`)

Visualizes progress through sequential transactional milestones (e.g. Apply $\rightarrow$ Review Data $\rightarrow$ Payment $\rightarrow$ Completion).

### Milestone States
1. **Completed:** Step circle filled with green (`#12B76A`), containing a white checkmark icon.
2. **Current / Active:** Step circle filled with national green (`#25935F`), white number, bold label.
3. **Pending / Upcoming:** Step circle outlined in neutral gray (`#D0D5DD`), muted number, light text.

### RTL Progression Flow
In Arabic layouts, steps flow from **Right to Left**:
* **Step 1:** Positioned on the **far right**.
* **Step 2, 3, etc.:** Sequence progressively to the **left**.

### HTML Structure
```html
<nav class="govsa-stepper" aria-label="مراحل تقديم الخدمة">
  <ol class="govsa-stepper__list">
    <!-- Step 1: Completed -->
    <li class="govsa-stepper__step govsa-stepper__step--completed">
      <div class="govsa-stepper__indicator" aria-label="المرحلة 1: مكتملة">
        <svg class="govsa-stepper__check" width="16" height="16" viewBox="0 0 24 24" aria-hidden="true">
          <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
        </svg>
      </div>
      <div class="govsa-stepper__content">
        <span class="govsa-stepper__title">بيانات المنشأة</span>
        <span class="govsa-stepper__status">مكتمل</span>
      </div>
      <div class="govsa-stepper__line" aria-hidden="true"></div>
    </li>

    <!-- Step 2: Active (Current) -->
    <li class="govsa-stepper__step govsa-stepper__step--active" aria-current="step">
      <div class="govsa-stepper__indicator">
        <span class="govsa-stepper__number">2</span>
      </div>
      <div class="govsa-stepper__content">
        <span class="govsa-stepper__title">الأنشطة والترخيص</span>
        <span class="govsa-stepper__status">قيد الإجراء</span>
      </div>
      <div class="govsa-stepper__line" aria-hidden="true"></div>
    </li>

    <!-- Step 3: Pending -->
    <li class="govsa-stepper__step govsa-stepper__step--pending">
      <div class="govsa-stepper__indicator">
        <span class="govsa-stepper__number">3</span>
      </div>
      <div class="govsa-stepper__content">
        <span class="govsa-stepper__title">سداد الفاتورة</span>
        <span class="govsa-stepper__status">متبقي</span>
      </div>
      <div class="govsa-stepper__line" aria-hidden="true"></div>
    </li>

    <!-- Step 4: Pending -->
    <li class="govsa-stepper__step govsa-stepper__step--pending">
      <div class="govsa-stepper__indicator">
        <span class="govsa-stepper__number">4</span>
      </div>
      <div class="govsa-stepper__content">
        <span class="govsa-stepper__title">إصدار الوثيقة</span>
        <span class="govsa-stepper__status">متبقي</span>
      </div>
    </li>
  </ol>
</nav>
```

---

## 3. Responsive Stepper Behavior

On mobile screens (`< 576px`), the horizontal multi-step layout transitions into a condensed progress summary:

```html
<div class="govsa-stepper-mobile">
  <div class="govsa-stepper-mobile__header">
    <span class="govsa-stepper-mobile__label">الخطوة 2 من 4</span>
    <span class="govsa-stepper-mobile__title">الأنشطة والترخيص</span>
  </div>
  <div class="govsa-progress-bar" role="progressbar" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
    <div class="govsa-progress-bar__fill" style="width: 50%;"></div>
  </div>
</div>
```


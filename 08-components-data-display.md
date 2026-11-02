# DGA Components: Data Display

> Reference: https://design.dga.gov.sa/guidelines/components/data-display

## Overview

Data display components present structured records, transaction history, metrics, and metadata to users clearly and efficiently. Under DGA Platforms Code, data components are optimized for rapid scanning, strict tabular alignment, and high-contrast readability.

---

## 1. Data Tables (`.govsa-table`)

Used for government records, request histories, transaction lists, and financial statements.

### Alignment Rules in Arabic (RTL)
* **Text / Descriptions / Names:** Align to the **right** (`text-align: right`).
* **Numbers / IDs / Amounts / Dates:** Align to the **left or center** for scanning consistency.
* **Status Badges:** Center aligned.
* **Actions Column:** Anchored to the **far left (end of row in RTL)**.

### HTML Implementation
```html
<div class="govsa-table-container" role="region" aria-label="جدول طلبات التراخيص" tabindex="0">
  <table class="govsa-table govsa-table--striped govsa-table--hover">
    <caption class="govsa-visually-hidden">قائمة طلبات التراخيص المسجلة وحالاتها</caption>
    <thead class="govsa-table__head">
      <tr>
        <th scope="col" class="govsa-table__th">رقم الطلب</th>
        <th scope="col" class="govsa-table__th">نوع الخدمة</th>
        <th scope="col" class="govsa-table__th">تاريخ التقديم</th>
        <th scope="col" class="govsa-table__th govsa-text-center">حالة الطلب</th>
        <th scope="col" class="govsa-table__th govsa-text-left">الإجراءات</th>
      </tr>
    </thead>
    <tbody class="govsa-table__body">
      <tr class="govsa-table__row">
        <td class="govsa-table__td"><strong>#REQ-2026-9041</strong></td>
        <td class="govsa-table__td">إصدار سجل تجاري فرعي</td>
        <td class="govsa-table__td">2026-10-15</td>
        <td class="govsa-table__td govsa-text-center">
          <span class="govsa-badge govsa-badge--success">معتمد ومكتمل</span>
        </td>
        <td class="govsa-table__td govsa-text-left">
          <a href="/requests/9041" class="govsa-button govsa-button--ghost govsa-button--sm">عرض التفاصيل</a>
        </td>
      </tr>
      <tr class="govsa-table__row">
        <td class="govsa-table__td"><strong>#REQ-2026-8812</strong></td>
        <td class="govsa-table__td">تحديث بيانات المنشأة</td>
        <td class="govsa-table__td">2026-10-22</td>
        <td class="govsa-table__td govsa-text-center">
          <span class="govsa-badge govsa-badge--warning">قيد المراجعة</span>
        </td>
        <td class="govsa-table__td govsa-text-left">
          <a href="/requests/8812" class="govsa-button govsa-button--ghost govsa-button--sm">متابعة الطلب</a>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```

---

## 2. Cards (`.govsa-card`)

Modular containers grouping related service information, metrics, or navigation entry points.

### Variations
1. **Service Card:** Includes leading service icon, title, description, and "ابدأ الخدمة" (Start Service) button.
2. **Interactive Card:** Fully clickable card with hover elevation.
3. **Stat / Metric Card:** Displays large number, label, and trend indicator.

### Service Card HTML
```html
<div class="govsa-card govsa-card--interactive">
  <div class="govsa-card__header">
    <div class="govsa-card__icon-wrapper" aria-hidden="true">
      <svg class="govsa-card__icon" width="24" height="24" viewBox="0 0 24 24">
        <!-- Service SVG Icon -->
      </svg>
    </div>
    <span class="govsa-badge govsa-badge--info">خدمة فورية</span>
  </div>
  <div class="govsa-card__body">
    <h3 class="govsa-card__title">إصدار شهادة المنشأ الرقمية</h3>
    <p class="govsa-card__desc">
      خدمة إلكترونية تتيح للمصدرين والمصانع الوطنية استخراج وتصديق شهادات المنشأ لمنتجاتهم آلياً خلال دقائق.
    </p>
  </div>
  <div class="govsa-card__footer">
    <a href="/services/origin-certificate" class="govsa-button govsa-button--primary govsa-button--sm">
      ابدأ الخدمة الآن
    </a>
  </div>
</div>
```

---

## 3. Badges (`.govsa-badge`)

Small status or numerical indicators communicating state.

| Badge Variant | Semantic Token | Color Combination | Example Meaning |
|---------------|----------------|-------------------|-----------------|
| **Success** | `.govsa-badge--success` | Green `#ECFDF3` bg, `#027A48` text | معتمد, نشط, مدفوع |
| **Warning** | `.govsa-badge--warning` | Yellow `#FFFAEB` bg, `#B54708` text | قيد التدقيق, ينتهي قريباً |
| **Error / Danger**| `.govsa-badge--error` | Red `#FEF3F2` bg, `#D92D20` text | مرفوض, ملغي, منتهي الصلاحية |
| **Info** | `.govsa-badge--info` | Blue `#EFF8FF` bg, `#175CD3` text | جديد, مسودة |
| **Neutral** | `.govsa-badge--neutral`| Gray `#F2F4F7` bg, `#344054` text | أرشيف, غير محدد |

```html
<span class="govsa-badge govsa-badge--success">
  <span class="govsa-badge__dot" aria-hidden="true"></span>
  <span>نشط ومفعل</span>
</span>
```

---

## 4. Tags & Filter Chips (`.govsa-tag`)

Used for categorization, search facets, or removable active filters.

```html
<!-- Interactive Filter Tag -->
<button type="button" class="govsa-tag govsa-tag--removable" aria-label="إزالة فلتر: منطقة الرياض">
  <span>منطقة الرياض</span>
  <span class="govsa-tag__remove" aria-hidden="true">×</span>
</button>
```

---

## 5. Avatars (`.govsa-avatar`)

Represents users, government officials, or organizations.

| Size | Token | Dimensions | Usage |
|------|-------|------------|-------|
| Small | `.govsa-avatar--sm` | `32px × 32px` | Table rows, compact comments |
| Medium | `.govsa-avatar--md` | `40px × 40px` | Header profile pill, user cards |
| Large | `.govsa-avatar--lg` | `64px × 64px` | Profile overview pages |

```html
<!-- Avatar with Image -->
<div class="govsa-avatar govsa-avatar--md">
  <img src="/avatars/user-12.jpg" alt="صورة الملف الشخصي: خالد العتيبي" class="govsa-avatar__img" />
</div>

<!-- Avatar with Initials Fallback -->
<div class="govsa-avatar govsa-avatar--md govsa-avatar--initials" aria-label="الملف الشخصي: خالد العتيبي">
  <span>خ.ع</span>
</div>
```

---

## 6. Tooltips & Popovers

* **Tooltip (`.govsa-tooltip`):** Non-interactive contextual label displayed on hover or keyboard focus.
* **Popover (`.govsa-popover`):** Rich interactive card triggered by click containing links or actions.

```html
<div class="govsa-tooltip-wrapper">
  <button type="button" class="govsa-button govsa-button--ghost govsa-button--icon" aria-describedby="tooltip-info-1">
    <svg width="20" height="20" aria-hidden="true">...</svg>
  </button>
  <div id="tooltip-info-1" class="govsa-tooltip" role="tooltip">
    رقم السجل التجاري المكون من 10 أرقام والصادر من وزارة التجارة
  </div>
</div>
```

---

## 7. Dividers (`.govsa-divider`)

Visually segments content sections or inline list items.

```html
<!-- Horizontal Divider -->
<hr class="govsa-divider" />

<!-- Horizontal Divider with Text Label -->
<div class="govsa-divider-with-text" role="separator">
  <span>أو يمكنك الدخول عبر</span>
</div>
```


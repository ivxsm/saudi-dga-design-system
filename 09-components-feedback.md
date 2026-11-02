# DGA Components: Feedback & Overlays

> Reference: https://design.dga.gov.sa/guidelines/components/feedback

## Overview

Feedback components communicate system status, task outcomes, background processing, and confirmations. Under DGA Platforms Code, feedback elements must never rely solely on color, must announce state changes to assistive technologies via ARIA live regions, and must manage focus properly during modal dialogues.

---

## 1. Inline Alerts (`.govsa-alert`)

Prominent contextual banners displayed within the page flow to inform users of critical updates, successes, warnings, or errors.

### Alert Variants
1. **Success (`.govsa-alert--success`):** Confirms successful submission or completed process.
2. **Error (`.govsa-alert--error`):** Informs of submission failure or critical blocker.
3. **Warning (`.govsa-alert--warning`):** Alerts of impending expiration or required upcoming action.
4. **Info (`.govsa-alert--info`):** General guidance or service advisory.

### HTML Structure
```html
<div class="govsa-alert govsa-alert--success" role="status">
  <div class="govsa-alert__icon" aria-hidden="true">
    <svg width="24" height="24" viewBox="0 0 24 24">
      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
    </svg>
  </div>
  <div class="govsa-alert__content">
    <h4 class="govsa-alert__title">تم استلام طلبك بنجاح</h4>
    <p class="govsa-alert__desc">
      تم تسجيل معاملتك برقم <strong>#2026-8812</strong>. سيتم إشعارك عبر الرسائل النصية عند تحديث حالة الطلب.
    </p>
  </div>
  <button type="button" class="govsa-alert__close" aria-label="إغلاق التنبيه">
    <span aria-hidden="true">×</span>
  </button>
</div>
```

---

## 2. Toast Notifications (`.govsa-toast`)

Transient, floating notification cards that appear in a corner of the screen to communicate lightweight feedback.

### Positioning & Behavior
* **Placement in RTL:** Top-left or bottom-left of the viewport (`inset-inline-start: 24px`).
* **Duration:** Auto-dismisses after 4 to 6 seconds; pauses timer on hover or keyboard focus.
* **Accessibility:** Wrapped in an `aria-live="polite"` container.

```html
<div class="govsa-toast-container" aria-live="polite" aria-atomic="true">
  <div class="govsa-toast govsa-toast--info" role="alert">
    <div class="govsa-toast__icon" aria-hidden="true">
      <svg width="20" height="20">...</svg>
    </div>
    <div class="govsa-toast__text">
      <span class="govsa-toast__title">تم حفظ المسودة</span>
      <span class="govsa-toast__time">منذ لحظات</span>
    </div>
    <button type="button" class="govsa-toast__close" aria-label="إغلاق الإشعار">×</button>
  </div>
</div>
```

---

## 3. Modal Dialogs (`.govsa-modal`)

Focused dialogue boxes that interrupt user workflow to capture confirmation or display critical decisions.

### Accessibility Requirements
* **Focus Trapping:** Keyboard focus must cycle exclusively within the modal while open (`Tab` / `Shift+Tab`).
* **Backdrop Dimming:** Semi-transparent overlay (`rgba(13, 18, 28, 0.6)`).
* **Escape Key:** Pressing `Esc` closes the dialog immediately.
* **Focus Restoration:** Returning focus to the button that triggered the modal upon dismissal.

### HTML Structure
```html
<div class="govsa-modal-backdrop" id="confirmation-modal" role="dialog" aria-modal="true" aria-labelledby="modal-title" aria-describedby="modal-desc" hidden>
  <div class="govsa-modal govsa-modal--md">
    <div class="govsa-modal__header">
      <h3 id="modal-title" class="govsa-modal__title">تأكيد إلغاء السجل التجاري</h3>
      <button type="button" class="govsa-modal__close" aria-label="إغلاق النافذة">
        <span aria-hidden="true">×</span>
      </button>
    </div>
    
    <div class="govsa-modal__body">
      <p id="modal-desc">
        هل أنت متأكد من رغبتك في إلغاء السجل التجاري رقم <strong>1010998877</strong>؟ هذه العملية نهائية ولا يمكن التراجع عنها بعد التأكيد.
      </p>
    </div>
    
    <div class="govsa-modal__footer">
      <button type="button" class="govsa-button govsa-button--destructive govsa-button--md">
        نعم، تأكيد الإلغاء
      </button>
      <button type="button" class="govsa-button govsa-button--ghost govsa-button--md">
        تراجع
      </button>
    </div>
  </div>
</div>
```

---

## 4. Progress Bars (`.govsa-progress`)

Linear indicators showing the status of ongoing tasks or multi-step form completions.

```html
<div class="govsa-progress-wrapper">
  <div class="govsa-progress-info">
    <span class="govsa-progress-label">اكتمال ملف المنشأة</span>
    <span class="govsa-progress-percentage">75%</span>
  </div>
  <div
    class="govsa-progress-bar"
    role="progressbar"
    aria-valuenow="75"
    aria-valuemin="0"
    aria-valuemax="100"
    aria-label="نسبة اكتمال ملف المنشأة"
  >
    <div class="govsa-progress-bar__fill" style="width: 75%;"></div>
  </div>
</div>
```

---

## 5. Loading Spinners (`.govsa-spinner`)

Circular indicators communicating asynchronous operations.

```html
<!-- Inline Button Spinner -->
<button class="govsa-button govsa-button--primary govsa-button--md" disabled aria-busy="true">
  <span class="govsa-spinner govsa-spinner--sm" aria-hidden="true"></span>
  <span>جاري معالجة الطلب...</span>
</button>

<!-- Page Loader Block -->
<div class="govsa-loading-state" role="status" aria-live="polite">
  <div class="govsa-spinner govsa-spinner--lg"></div>
  <p class="govsa-loading-state__text">جاري استرجاع البيانات من السجلات الوطنية...</p>
</div>
```

---

## 6. Empty States (`.govsa-empty-state`)

Shown when a container, table, or search result has zero items. Reassures users that the system is operating normally and guides them toward next steps.

```html
<div class="govsa-empty-state">
  <div class="govsa-empty-state__icon-wrapper" aria-hidden="true">
    <svg width="64" height="64" viewBox="0 0 24 24" class="govsa-empty-state__icon">
      <path d="M19 3H5c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h14c1.1 0 2-.9 2-2V5c0-1.1-.9-2-2-2zm-5 14H7v-2h7v2zm3-4H7v-2h10v2zm0-4H7V7h10v2z"/>
    </svg>
  </div>
  <h3 class="govsa-empty-state__title">لا توجد طلبات مسجلة حالياً</h3>
  <p class="govsa-empty-state__desc">
    لم تقم بتقديم أي طلبات خدمة حتى الآن. يمكنك البدء بتقديم طلب جديد من خلال دليل الخدمات الإلكترونية.
  </p>
  <div class="govsa-empty-state__actions">
    <a href="/services" class="govsa-button govsa-button--primary govsa-button--md">
      استعراض الخدمات المتاحة
    </a>
  </div>
</div>
```


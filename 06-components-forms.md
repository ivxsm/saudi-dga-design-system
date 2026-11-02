# DGA Components: Forms & Inputs

> Reference: https://design.dga.gov.sa/guidelines/components/forms

## Overview

Form elements in Saudi government portals collect essential citizen, business, and administrative data. Under DGA Platforms Code, forms must prioritize **error prevention, clarity, unambiguous validation, and full RTL accessibility**.

---

## Form Component Architecture

A complete DGA form control adheres to the following structural layers:

```text
┌────────────────────────────────────────────────────────┐
│ Label Text * (مسمى الحقل)                              │
│ Sub-label / Hint Text (تعليمات إضافية)                 │
├────────────────────────────────────────────────────────┤
│ [Prefix] [Leading Icon]  [Input Area]  [Trailing Icon] │
├────────────────────────────────────────────────────────┤
│ Helper Text / Error Message (رسالة توضيحية أو خطأ)     │
└────────────────────────────────────────────────────────┘
```

---

## 1. Text Input Field (`.govsa-input`)

Standard single-line text input for names, national ID, phone numbers, email, and queries.

### Anatomy & Classes
* `.govsa-form-group`: Outer container binding label, input, and helper text.
* `.govsa-label`: Field title, bold/medium font, required marker (`*`) colored in semantic error red.
* `.govsa-input`: The native `<input>` element with standard border and focus states.
* `.govsa-helper-text`: Microcopy assisting the user with format requirements.
* `.govsa-error-message`: High-contrast error message tied to `aria-describedby`.

### Variations
1. **Standard Input:** Plain text entry box.
2. **Input with Icon:** Directional leading icon (e.g., search magnifier, user badge).
3. **Prefix / Suffix Input:** Contextual unit badges attached inline (e.g., country code `+966` or currency `ر.س`).
4. **Password Input with Reveal:** Suffix button toggles text visibility with `aria-label`.

### HTML Implementation (RTL-Native)
```html
<div class="govsa-form-group">
  <label for="national-id" class="govsa-label">
    رقم الهوية الوطنية أو الإقامة
    <span class="govsa-label__required" aria-hidden="true">*</span>
  </label>
  <span id="id-hint" class="govsa-hint">أدخل 10 أرقام تبدأ بـ 1 أو 2</span>
  
  <div class="govsa-input-wrapper">
    <input
      type="text"
      id="national-id"
      name="national_id"
      class="govsa-input"
      maxlength="10"
      pattern="[1-2][0-9]{9}"
      inputmode="numeric"
      aria-describedby="id-hint"
      required
    />
  </div>
</div>
```

---

## 2. Textarea (`.govsa-textarea`)

Multi-line text entry for comments, descriptions, and addresses.

```html
<div class="govsa-form-group">
  <label for="notes" class="govsa-label">الملاحظات أو التفاصيل</label>
  <textarea
    id="notes"
    name="notes"
    class="govsa-textarea"
    rows="4"
    maxlength="500"
    placeholder="اكتب التفاصيل هنا..."
  ></textarea>
  <div class="govsa-form-group__footer">
    <span class="govsa-hint">الحد الأقصى 500 حرف</span>
    <span class="govsa-char-count" aria-live="polite">متبقي 500</span>
  </div>
</div>
```

---

## 3. Select / Dropdown (`.govsa-select`)

Dropdown selection for choosing one item from a predefined list.

```html
<div class="govsa-form-group">
  <label for="region-select" class="govsa-label">المنطقة الإدارية</label>
  <div class="govsa-select-wrapper">
    <select id="region-select" name="region" class="govsa-select" required>
      <option value="" disabled selected>اختر المنطقة...</option>
      <option value="riyadh">منطقة الرياض</option>
      <option value="makkah">منطقة مكة المكرمة</option>
      <option value="eastern">المنطقة الشرقية</option>
      <option value="madinah">منطقة المدينة المنورة</option>
    </select>
    <svg class="govsa-select__chevron" aria-hidden="true" width="16" height="16" viewBox="0 0 24 24">
      <path d="M7 10l5 5 5-5z"/>
    </svg>
  </div>
</div>
```

---

## 4. Selection Controls: Checkbox & Radio

### Checkboxes (`.govsa-checkbox`)
Used for multi-selection lists or standalone confirmation toggles (e.g. Terms & Conditions).

```html
<div class="govsa-checkbox-group">
  <label class="govsa-checkbox">
    <input type="checkbox" name="terms" class="govsa-checkbox__input" required />
    <span class="govsa-checkbox__box" aria-hidden="true">
      <svg class="govsa-checkbox__icon" viewBox="0 0 24 24">
        <path d="M9 16.17L4.83 12l-1.42 1.41L9 19 21 7l-1.41-1.41z"/>
      </svg>
    </span>
    <span class="govsa-checkbox__label">أوافق على الشروط والأحكام وسياسة الخصوصية</span>
  </label>
</div>
```

### Radio Buttons (`.govsa-radio`)
Used for mutually exclusive options within a group.

```html
<fieldset class="govsa-fieldset">
  <legend class="govsa-legend">طريقة الدفع المفضلة</legend>
  
  <div class="govsa-radio-group">
    <label class="govsa-radio">
      <input type="radio" name="payment_method" value="mada" class="govsa-radio__input" checked />
      <span class="govsa-radio__circle" aria-hidden="true"></span>
      <span class="govsa-radio__label">بطاقة مدى البنكية</span>
    </label>
    
    <label class="govsa-radio">
      <input type="radio" name="payment_method" value="sadad" class="govsa-radio__input" />
      <span class="govsa-radio__circle" aria-hidden="true"></span>
      <span class="govsa-radio__label">نظام سداد للمدفوعات</span>
    </label>
  </div>
</fieldset>
```

---

## 5. Toggle Switch (`.govsa-switch`)

An instant-action binary control (on/off) that applies settings without needing a separate form submission.

```html
<label class="govsa-switch">
  <input type="checkbox" class="govsa-switch__input" role="switch" aria-checked="false" />
  <span class="govsa-switch__track" aria-hidden="true">
    <span class="govsa-switch__thumb"></span>
  </span>
  <span class="govsa-switch__label">تفعيل الإشعارات عبر الرسائل النصية (SMS)</span>
</label>
```

---

## 6. File Upload Dropzone (`.govsa-file-upload`)

For uploading documents (National IDs, commercial licenses, official attachments).

```html
<div class="govsa-form-group">
  <label class="govsa-label">إرفاق المستندات الداعمة</label>
  <div class="govsa-dropzone" tabindex="0" role="button" aria-label="منطقة رفع الملفات">
    <input type="file" id="file-upload" class="govsa-dropzone__input" multiple accept=".pdf,.png,.jpg" />
    <svg class="govsa-dropzone__icon" aria-hidden="true" width="40" height="40" viewBox="0 0 24 24">
      <path d="M19.35 10.04C18.67 6.59 15.64 4 12 4 9.11 4 6.6 5.64 5.35 8.04 2.34 8.36 0 10.91 0 14c0 3.31 2.69 6 6 6h13c2.76 0 5-2.24 5-5 0-2.64-2.05-4.78-4.65-4.96zM14 13v4h-4v-4H7l5-5 5 5h-3z"/>
    </svg>
    <div class="govsa-dropzone__text">
      <span class="govsa-dropzone__title">اسحب الملفات وأفلتها هنا أو <span class="govsa-dropzone__browse">تصفح من جهازك</span></span>
      <span class="govsa-dropzone__hint">صيغ الملفات المدعومة: PDF, PNG, JPG (الحد الأقصى: 10 ميجابايت)</span>
    </div>
  </div>
</div>
```

---

## 7. Date Picker (`.govsa-datepicker`)

Handles Gregorian and Hijri (Umm al-Qura) calendar inputs, standardizing government date selection.

```html
<div class="govsa-form-group">
  <label for="dob" class="govsa-label">تاريخ الميلاد</label>
  <div class="govsa-input-wrapper govsa-input-wrapper--with-icon">
    <input
      type="text"
      id="dob"
      name="dob"
      class="govsa-input"
      placeholder="يوم / شهر / سنة (هـ / م)"
      autocomplete="off"
    />
    <button type="button" class="govsa-input__icon-button" aria-label="اختر التاريخ من التقويم">
      <svg aria-hidden="true" width="20" height="20" viewBox="0 0 24 24">
        <path d="M19 4h-1V2h-2v2H8V2H6v2H5c-1.11 0-1.99.9-1.99 2L3 20a2 2 0 0 0 2 2h14c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 16H5V10h14v10zM9 14H7v-2h2v2zm4 0h-2v-2h2v2zm4 0h-2v-2h2v2z"/>
      </svg>
    </button>
  </div>
</div>
```

---

## Validation & Error States

When validation fails, three visual and programmatic cues must trigger simultaneously:

1. **Border Color Change:** Input border turns semantic error red (`#F04438`).
2. **Error Message Display:** Inline message rendered directly beneath input, colored `#D92D20`.
3. **ARIA Linkage:** Input updated with `aria-invalid="true"` and `aria-describedby="error-id"`.

```html
<div class="govsa-form-group govsa-form-group--error">
  <label for="phone" class="govsa-label">
    رقم الجوال
    <span class="govsa-label__required" aria-hidden="true">*</span>
  </label>
  
  <div class="govsa-input-wrapper">
    <input
      type="tel"
      id="phone"
      name="phone"
      class="govsa-input govsa-input--error"
      value="041234567"
      aria-invalid="true"
      aria-describedby="phone-error"
    />
  </div>
  
  <div id="phone-error" class="govsa-error-message" role="alert">
    <svg aria-hidden="true" width="16" height="16" viewBox="0 0 24 24">
      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm1 15h-2v-2h2v2zm0-4h-2V7h2v6z"/>
    </svg>
    <span>رقم الجوال غير صحيح. يجب أن يبدأ بـ 05 ويتكون من 10 أرقام.</span>
  </div>
</div>
```

---

## Form CSS Architecture

```css
/* Form Container */
.govsa-form-group {
  display: flex;
  flex-direction: column;
  margin-block-end: var(--dga-space-5);
}

/* Labels */
.govsa-label {
  font-family: var(--dga-font-family-base);
  font-size: var(--dga-font-size-body-sm);
  font-weight: var(--dga-font-weight-medium);
  color: var(--dga-text-primary);
  margin-block-end: var(--dga-space-2);
}

.govsa-label__required {
  color: var(--dga-error);
  margin-inline-start: var(--dga-space-1);
}

/* Hints */
.govsa-hint {
  font-size: var(--dga-font-size-caption);
  color: var(--dga-text-secondary);
  margin-block-end: var(--dga-space-2);
}

/* Text Input & Textarea */
.govsa-input,
.govsa-textarea,
.govsa-select {
  width: 100%;
  min-height: 44px;
  padding: var(--dga-space-2) var(--dga-space-3);
  font-family: var(--dga-font-family-base);
  font-size: var(--dga-font-size-body-md);
  color: var(--dga-text-primary);
  background-color: var(--dga-bg-page);
  border: 1px solid var(--dga-border-default);
  border-radius: var(--dga-radius-md);
  outline: none;
  transition: border-color var(--dga-duration-fast) var(--dga-ease-standard),
              box-shadow var(--dga-duration-fast) var(--dga-ease-standard);
}

/* Input Focus */
.govsa-input:focus,
.govsa-textarea:focus,
.govsa-select:focus {
  border-color: var(--dga-primary);
  box-shadow: 0 0 0 3px rgba(37, 147, 95, 0.2);
}

/* Input Error */
.govsa-input--error,
.govsa-form-group--error .govsa-input {
  border-color: var(--dga-error);
}
.govsa-input--error:focus,
.govsa-form-group--error .govsa-input:focus {
  border-color: var(--dga-error);
  box-shadow: 0 0 0 3px rgba(240, 68, 56, 0.2);
}

/* Error Message */
.govsa-error-message {
  display: flex;
  align-items: center;
  gap: var(--dga-space-2);
  font-size: var(--dga-font-size-caption);
  font-weight: var(--dga-font-weight-medium);
  color: var(--dga-error-text);
  margin-block-start: var(--dga-space-2);
}
```

---

## Best Practices & Guidelines

### ✅ DO
* Clearly indicate mandatory fields with an asterisk `*` and explain it in the form intro.
* Use appropriate `inputmode` attributes (`numeric`, `email`, `tel`) to display optimal keyboards on mobile devices.
* Connect error messages with inputs using `aria-describedby` so screen readers announce errors immediately upon focus.
* Group related radio buttons or checkboxes inside `<fieldset>` with a descriptive `<legend>`.

### ❌ DON'T
* Don't rely on placeholder text as a replacement for `<label>`. Placeholders disappear when typed into.
* Don't display ambiguous error messages like "خطأ في الإدخال" (Input error); explain specifically how to fix it.
* Don't clear user-filled fields upon an error. Retain all correctly entered data.


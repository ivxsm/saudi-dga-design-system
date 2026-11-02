# DGA Components: Navigation

> Reference: https://design.dga.gov.sa/guidelines/components/navigation

## Overview

Navigation components guide citizens, businesses, and government employees seamlessly across complex digital architectures. Under DGA Platforms Code, navigation structures are **Arabic-first (RTL)**, responsive, fully accessible via keyboard (`Tab`, `Arrow` keys, `Escape`), and integrate Saudi national identity marks.

---

## 1. Government Header (`.govsa-header`)

The standard header comprises two primary tiers: the **Top Utility Bar** and the **Main Navigation Bar**.

```text
┌────────────────────────────────────────────────────────────────────────┐
│ [Language Toggle: English] [Accessibility: A+ A-]   [Kingdom National Seal]│ Top Utility Bar
├────────────────────────────────────────────────────────────────────────┤
│ [Login / Profile] [Search Bar]   [Services] [About] [Home]   [Entity Logo]│ Main Nav Bar
└────────────────────────────────────────────────────────────────────────┘
```

### RTL Layout Sequence
* **Far Right (RTL):** Government entity logo and national portal identity.
* **Center (RTL):** Primary navigation links.
* **Far Left (RTL):** Global search, notification indicators, user account / Nafath SSO login button.

### HTML Structure
```html
<header class="govsa-header" role="banner">
  <!-- Top Utility Bar -->
  <div class="govsa-header__top-bar">
    <div class="govsa-container govsa-header__top-container">
      <div class="govsa-header__national-brand">
        <span class="govsa-header__flag-icon" aria-hidden="true">🇸🇦</span>
        <span>المملكة العربية السعودية — بوابة رسمية</span>
      </div>
      <div class="govsa-header__utility-controls">
        <!-- Accessibility Controls -->
        <div class="govsa-a11y-controls" aria-label="أدوات سهولة الوصول">
          <button type="button" class="govsa-a11y-btn" aria-label="تكبير الخط">A+</button>
          <button type="button" class="govsa-a11y-btn" aria-label="الخط الافتراضي">A</button>
          <button type="button" class="govsa-a11y-btn" aria-label="تصغير الخط">A-</button>
        </div>
        <!-- Language Switcher -->
        <a href="?lang=en" class="govsa-lang-switch" lang="en" dir="ltr" aria-label="Switch to English">English</a>
      </div>
    </div>
  </div>

  <!-- Main Navigation Bar -->
  <div class="govsa-header__main">
    <div class="govsa-container govsa-header__main-container">
      <!-- Entity Identity (Right in RTL) -->
      <a href="/" class="govsa-header__brand" aria-label="الصفحة الرئيسية لهيئة الحكومة الرقمية">
        <img src="/assets/dga-logo.svg" alt="شعار هيئة الحكومة الرقمية" class="govsa-header__logo" />
      </a>

      <!-- Primary Desktop Navigation -->
      <nav class="govsa-header__nav" role="navigation" aria-label="القائمة الرئيسية">
        <ul class="govsa-header__menu">
          <li><a href="/" class="govsa-header__link govsa-header__link--active" aria-current="page">الرئيسية</a></li>
          <li><a href="/services" class="govsa-header__link">الخدمات الإلكترونية</a></li>
          <li><a href="/initiatives" class="govsa-header__link">المبادرات والمشاريع</a></li>
          <li><a href="/regulations" class="govsa-header__link">الأنظمة واللوائح</a></li>
          <li><a href="/contact" class="govsa-header__link">تواصل معنا</a></li>
        </ul>
      </nav>

      <!-- Action Utilities (Left in RTL) -->
      <div class="govsa-header__actions">
        <button type="button" class="govsa-button govsa-button--ghost govsa-button--icon" aria-label="بحث في المنصة">
          <svg aria-hidden="true" width="20" height="20" viewBox="0 0 24 24"><path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/></svg>
        </button>
        <a href="/login" class="govsa-button govsa-button--primary govsa-button--sm">تسجيل الدخول عبر نفاذ</a>
        <!-- Mobile Menu Trigger -->
        <button type="button" class="govsa-header__mobile-toggle" aria-expanded="false" aria-controls="mobile-menu" aria-label="فتح القائمة">
          <span class="govsa-header__hamburger"></span>
        </button>
      </div>
    </div>
  </div>
</header>
```

---

## 2. Government Footer (`.govsa-footer`)

Mandatory for all government digital portals. Incorporates entity accreditation, related government links, Vision 2030 badge, copyright statement, and mandatory privacy/terms policies.

### HTML Structure
```html
<footer class="govsa-footer" role="contentinfo">
  <div class="govsa-container">
    <!-- Top Footer Links Grid -->
    <div class="govsa-row govsa-footer__grid">
      <!-- Entity Overview -->
      <div class="govsa-col-12 govsa-col-lg-4 govsa-footer__col">
        <img src="/assets/dga-logo-white.svg" alt="شعار الهيئة" class="govsa-footer__logo" />
        <p class="govsa-footer__desc">
          الجهة المختصة بكل ما يتعلق بالحكومة الرقمية وتطوير الخدمات الوطنية المشتركة في المملكة العربية السعودية.
        </p>
      </div>

      <!-- Quick Links -->
      <div class="govsa-col-6 govsa-col-lg-2 govsa-footer__col">
        <h4 class="govsa-footer__title">روابط سريعة</h4>
        <ul class="govsa-footer__links">
          <li><a href="/services">دليل الخدمات</a></li>
          <li><a href="/open-data">البيانات المفتوحة</a></li>
          <li><a href="/participation">المشاركة الرقمية</a></li>
          <li><a href="/careers">التوظيف</a></li>
        </ul>
      </div>

      <!-- Related Portals -->
      <div class="govsa-col-6 govsa-col-lg-3 govsa-footer__col">
        <h4 class="govsa-footer__title">بوابات حكومية ذات علاقة</h4>
        <ul class="govsa-footer__links">
          <li><a href="https://my.gov.sa" target="_blank" rel="noopener">المنصة الوطنية الموحدة (GOV.SA)</a></li>
          <li><a href="https://etimad.sa" target="_blank" rel="noopener">منصة اعتماد</a></li>
          <li><a href="https://absher.sa" target="_blank" rel="noopener">منصة أبشر</a></li>
        </ul>
      </div>

      <!-- Contact & Vision 2030 -->
      <div class="govsa-col-12 govsa-col-lg-3 govsa-footer__col govsa-footer__vision-col">
        <img src="/assets/vision-2030-logo.svg" alt="شعار رؤية المملكة 2030" class="govsa-footer__vision-logo" />
        <div class="govsa-footer__social">
          <a href="#" aria-label="حساب منصة إكس"><svg width="20" height="20">...</svg></a>
          <a href="#" aria-label="حساب لنكد إن"><svg width="20" height="20">...</svg></a>
          <a href="#" aria-label="حساب يوتيوب"><svg width="20" height="20">...</svg></a>
        </div>
      </div>
    </div>

    <!-- Sub-footer / Legal -->
    <div class="govsa-footer__bottom">
      <p class="govsa-footer__copy">
        جميع الحقوق محفوظة لهيئة الحكومة الرقمية © 2026 المملكة العربية السعودية
      </p>
      <ul class="govsa-footer__legal-links">
        <li><a href="/privacy">سياسة الخصوصية</a></li>
        <li><a href="/terms">الشروط والأحكام</a></li>
        <li><a href="/sla">اتفاقية مستوى الخدمة</a></li>
        <li><a href="/sitemap">خريطة الموقع</a></li>
      </ul>
    </div>
  </div>
</footer>
```

---

## 3. Breadcrumbs (`.govsa-breadcrumb`)

Provides contextual trail from the homepage down to the active service page.

```html
<nav class="govsa-breadcrumb" aria-label="مسار التنقل">
  <ol class="govsa-breadcrumb__list">
    <li class="govsa-breadcrumb__item">
      <a href="/" class="govsa-breadcrumb__link">الرئيسية</a>
      <span class="govsa-breadcrumb__separator" aria-hidden="true">‹</span>
    </li>
    <li class="govsa-breadcrumb__item">
      <a href="/services" class="govsa-breadcrumb__link">الخدمات الإلكترونية</a>
      <span class="govsa-breadcrumb__separator" aria-hidden="true">‹</span>
    </li>
    <li class="govsa-breadcrumb__item" aria-current="page">
      <span class="govsa-breadcrumb__current">إصدار ترخيص تجاري</span>
    </li>
  </ol>
</nav>
```

---

## 4. Tabs (`.govsa-tabs`)

Organizes distinct panels of related content without page reloading.

### RTL Keyboard Navigation Standard
* `ArrowLeft`: Move focus to the *next* tab in RTL.
* `ArrowRight`: Move focus to the *previous* tab in RTL.
* `Home` / `End`: Jump to first / last tab.
* `Space` / `Enter`: Activate selected tab panel.

```html
<div class="govsa-tabs">
  <div class="govsa-tabs__list" role="tablist" aria-label="أقسام الخدمة">
    <button
      role="tab"
      id="tab-1"
      class="govsa-tabs__tab govsa-tabs__tab--active"
      aria-selected="true"
      aria-controls="panel-1"
      tabindex="0"
    >
      نظرة عامة على الخدمة
    </button>
    <button
      role="tab"
      id="tab-2"
      class="govsa-tabs__tab"
      aria-selected="false"
      aria-controls="panel-2"
      tabindex="-1"
    >
      الشروط والمتطلبات
    </button>
    <button
      role="tab"
      id="tab-3"
      class="govsa-tabs__tab"
      aria-selected="false"
      aria-controls="panel-3"
      tabindex="-1"
    >
      الرسوم وقنوات الدفع
    </button>
  </div>

  <div id="panel-1" class="govsa-tabs__panel" role="tabpanel" aria-labelledby="tab-1" tabindex="0">
    <p>تمكن هذه الخدمة المواطنين والمقيمين من تقديم طلبات التراخيص بصورة رقمية فورية.</p>
  </div>
  <div id="panel-2" class="govsa-tabs__panel" role="tabpanel" aria-labelledby="tab-2" tabindex="0" hidden>
    <p>1. وجود هوية وطنية سارية. 2. ألا يقل العمر عن 18 عاماً.</p>
  </div>
  <div id="panel-3" class="govsa-tabs__panel" role="tabpanel" aria-labelledby="tab-3" tabindex="0" hidden>
    <p>رسوم الخدمة: 500 ريال سعودي تدفع عبر سداد أو مدى.</p>
  </div>
</div>
```

---

## 5. Pagination (`.govsa-pagination`)

Splits large data tables or result lists into digestible numbered pages.

```html
<nav class="govsa-pagination" aria-label="ترقيم الصفحات">
  <ul class="govsa-pagination__list">
    <!-- Next button in RTL points Left (Forward progression) -->
    <li>
      <button class="govsa-pagination__btn govsa-pagination__btn--prev" disabled aria-label="الصفحة السابقة">
        <span aria-hidden="true">›</span>
        <span>السابق</span>
      </button>
    </li>
    
    <li><button class="govsa-pagination__page govsa-pagination__page--active" aria-current="page">1</button></li>
    <li><button class="govsa-pagination__page">2</button></li>
    <li><button class="govsa-pagination__page">3</button></li>
    <li><span class="govsa-pagination__ellipsis" aria-hidden="true">…</span></li>
    <li><button class="govsa-pagination__page">18</button></li>
    
    <li>
      <button class="govsa-pagination__btn govsa-pagination__btn--next" aria-label="الصفحة التالية">
        <span>التالي</span>
        <span aria-hidden="true">‹</span>
      </button>
    </li>
  </ul>
</nav>
```

---

## 6. Side Navigation (`.govsa-side-nav`)

Used for administration dashboards, multi-step portals, and user accounts.

```html
<nav class="govsa-side-nav" aria-label="القائمة الجانبية للخدمات">
  <ul class="govsa-side-nav__list">
    <li class="govsa-side-nav__item">
      <a href="/dashboard" class="govsa-side-nav__link govsa-side-nav__link--active" aria-current="page">
        <svg class="govsa-side-nav__icon" aria-hidden="true" width="20" height="20">...</svg>
        <span>لوحة التحكم الرئيسية</span>
      </a>
    </li>
    <li class="govsa-side-nav__item">
      <a href="/requests" class="govsa-side-nav__link">
        <svg class="govsa-side-nav__icon" aria-hidden="true" width="20" height="20">...</svg>
        <span>الطلبات والمعاملات</span>
        <span class="govsa-badge govsa-badge--info">4</span>
      </a>
    </li>
    <li class="govsa-side-nav__item">
      <a href="/documents" class="govsa-side-nav__link">
        <svg class="govsa-side-nav__icon" aria-hidden="true" width="20" height="20">...</svg>
        <span>المستندات والتراخيص</span>
      </a>
    </li>
    <li class="govsa-side-nav__item">
      <a href="/settings" class="govsa-side-nav__link">
        <svg class="govsa-side-nav__icon" aria-hidden="true" width="20" height="20">...</svg>
        <span>إعدادات الحساب</span>
      </a>
    </li>
  </ul>
</nav>
```


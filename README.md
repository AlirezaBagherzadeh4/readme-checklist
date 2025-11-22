<div dir="auto">

# 📋 Project Checklist

_**این چک‌لیست برای کنترل کیفیت و آماده‌سازی نهایی پروژه استفاده می‌شود.  
هر سکشن شامل موارد ضروری برای بررسی است.**_

---

## 📈 1. SEO

- #### Meta Tags و ساختار HTML
  - [ ] `<title></title>` مناسب (50-60 characters)
  - [ ] `<meta name="description" content="">` مرتبط برای هر صفحه (150-160 characters)
  - [ ] `<meta name="robots">` (برای صفحات بلاک‌شده یا غیر indexable)
  - [ ] `<link rel="canonical" href=""https://example.com/>` برای جلوگیری از duplicate content
  - [ ] `<meta name="viewport">` برای رسپانسیو
- #### Social Media
  - [ ] `og:title`
  - [ ] `og:description`
  - [ ] `og:image`
  - [ ] `og:url`
  - [ ] `og:type`
  - [ ] `og:card`
  - [ ] `twitter:title`
  - [ ] `twitter:description`
  - [ ] `twitter:card`
- #### Schema Markup / Structured Data
  - [ ] WebSite
  - [ ] BreadcrumbList
  - [ ] Organization
  - [ ] Article / BlogPosting
  - [ ] FAQ
- #### Sitemap & Robots.txt
  - [ ] `Sitemap.xml` به‌روز و صحیح
  - [ ] فایل `robot.txt`
  - [ ] Dynamic Sitemap برای صفحات داینامیک
- #### Technical SEO (Next.js)
  - [ ] استفاده از `<Link>` برای لینک داخلی
  - [ ] کنترل صفحات تکراری برای جلوگیری از رندر چندباره
  - [ ] جلوگیری از رندر ناقص سمت کلاینت که باعث indexing ناقص می‌شود
- #### Content SEO
  - [ ] فقط یک `<h1>` برای هر صفحه
  - [ ] ساختار _heading_ منطقی (h1 → h2 → h3 → h4 → h5 → h6) [نمونه](https://substackcdn.com/image/fetch/$s_!JKn7!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fba08fa28-745a-458d-8c23-29acb08e2cef_1600x836.png)
  - [ ] _semantic HTML structure_: `<header>, <footer>, <main>, <article>, <section>, <aside>, <nav>, <figure>`
  - [ ] تصاویر همراه با _alt text_
- #### Link Strategy
  - [ ] لینک خوانا، برای مثال: `<Link href="/seo-best-practices">` [نمونه](https://substackcdn.com/image/fetch/$s_!fOM2!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0dfd32c6-e2f8-433b-bdb1-5b9cf88717ba_1600x500.png)
  - [ ] لینک‌های خارجی با `rel="noopener noreferrer"`
  - [ ] 404 نشدن لینک‌ها
- #### International SEO (در صورت استفاده از i18n)
  - [ ] استفاده از `hreflang`
  - [ ] ساخت _sitemap_ جدا برای هر زبان
  - [ ] مسیرهای داینامیک سازگار با _locale_

---

## 🔒 2. Security

- #### Authentication & Authorization
  - [ ] ذخیره‌نکردن توکن در _localStorage_ (استفاده از [HttpOnly Cookie](https://nextjs.org/docs/app/api-reference/functions/cookies))
  - [ ] محدودسازی تعداد تلاش‌های ورود (_Rate Limit_)
  - [ ] بررسی دسترسی‌ها قبل از هر روت و در _route handler_ ها
  - [ ] بررسی توکن کاربر در `middleware.ts`
  - [ ] [ACL](https://medium.com/@mesutas.dev/rbac-in-next-js-with-nextauth-b438fe59eeeb) (بررسی دسترسی‌ها)
- #### Input Validation & Sanitization
  - [ ] Validation سمت سرور با _Zod_
  - [ ] Validate کامل body, query, params
  - [ ] پاکسازی ورودی کاربر (_Sanitization_), استفاده از [DOMPurify](https://github.com/cure53/DOMPurify) یا `dangerouslySetInnerHTML`
  - [ ] جلوگیری از درج _HTML user-generated_
  - [ ] انتقال اجرای توابع حساس و امنیتی به سمت سرور
- #### Password & Credential Security
  - [ ] ممنوعیت ذخیره plain passwords
  - [ ] بررسی حداقل طول و پیچیدگی رمز
- #### Dependency Security
  - [ ] اجرای مرتب `npm audit`
  - [ ] حذف پکیج‌های بلااستفاده
- #### File Upload Security
  - [ ] بررسی نوع فایل [(MIME)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/MIME_types/Common_types)
  - [ ] محدودیت حجم فایل
  - [ ] جلوگیری از اجرای فایل روی سرور
- #### Session & Cookies
  - [ ] زمان انقضای مناسب _session_
  - [ ] استفاده از _SameSite Cookies_: `SameSite=Lax` یا `Strict`
- #### Infrastructure & Hosting
  - [ ] محیط _production_ از _dev_ جدا باشد
  - [ ] _Secret-ENV_ ها فقط در سرور قرار بگیرند

---

## 📝 3. Documentation

- #### README file
  - [ ] توضیح کامل پروژه
  - [ ] دستور نصب و اجرا
  - [ ] ساختار پوشه‌ها
  - [ ] API Routing
  - [ ] توضیح تکنولوژی‌ها
  - [ ] نحوه _Build_ و _Deploy_
- #### Architecture Docs
  - [ ] Folder structure توضیح
  - [ ] Data Flow
  - [ ] Routing Flow
- #### API Documentation
  - [ ] توضیح *endpoint*ها
  - [ ] ورودی‌ها و خروجی‌ها
  - [ ] توضیح status codeها
- #### Contribution Guide
  - [ ] قوانین _commit_
  - [ ] قوانین _branch_
- #### CHANGELOG
  - [ ] نسخه‌ها و تغییرات
  - [ ] اضافه شدن قابلیت‌ها
  - [ ] رفع باگ‌ها
- #### Dev Notes
  - [ ] *TODO*های Developer

---

## 4. Logs

- [ ] ساختار مشخص لاگ‌ها
- [ ] سطح‌بندی (info, warn, error)
- [ ] ذخیره‌سازی امن لاگ‌ها
- [ ] لاگ‌گیری از خطاهای حساس
- [ ] امکان غیرفعال‌سازی لاگ در prod

---

## 5. Services

- [ ] تمام سرویس‌ها مستندسازی شده
- [ ] Retry و Timeout بررسی شده
- [ ] Error Handling کامل
- [ ] سوییچ محیط dev/prod
- [ ] تست Callهای API

---

## 6. Performance

- [ ] Lighthouse Performance Score
- [ ] Code splitting
- [ ] Lazy-loading
- [ ] کش سمت کلاینت/سرور
- [ ] بهینه‌سازی تصویر
- [ ] استفاده از CDN

---

## 7. Dependency

- [ ] حذف پکیج‌های غیرضروری
- [ ] آپدیت وابستگی‌ها
- [ ] امنیت نسخه‌ها
- [ ] قفل نسخه (lockfile)

---

## 8. Accessibility

- [ ] تگ‌های ARIA
- [ ] کنتراست رنگ‌ها
- [ ] Keyboard Navigation
- [ ] فوکوس‌ها قابل دیدن
- [ ] تست Lighthouse A11y

---

## 9. Test

- [ ] تست واحد (Unit)
- [ ] تست integration
- [ ] تست E2E
- [ ] پوشش تست‌ها (Coverage)
- [ ] تست رگرسیون

---

## 10. UI

- [ ] رعایت Design System
- [ ] واکنش‌گرایی (Responsive)
- [ ] انیمیشن‌های سبک
- [ ] رعایت Padding/Spacing
- [ ] RTL/LTR در صورت نیاز

---

## 11. Deploy

- [ ] Pipeline آماده
- [ ] Build بدون خطا
- [ ] ENVهای لازم ست شده
- [ ] Health-check
- [ ] مانیتورینگ فعال

---

## 12. Versioning

- [ ] رعایت Semantic Versioning
- [ ] Tagهای منتشر شده
- [ ] تغییرات در CHANGELOG ثبت شده

---

## 13. Flow

- [ ] نمودار جریان (Flow Diagram)
- [ ] نقشه مسیر کاربر (User Flow)
- [ ] Edge-caseها بررسی شده
- [ ] رفتار خطا در جریان مشخص

---

## 14. Code Review

- [ ] خوانایی کد
- [ ] حذف کدهای مرده (Dead Code)
- [ ] استانداردهای ESLint رعایت شده
- [ ] پوشش تست مناسب
- [ ] نام‌گذاری واضح متغیرها و تابع‌ها

---

</div>

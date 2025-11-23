<div dir="auto">

# 📋 Project Checklist

**این چک‌لیست برای کنترل کیفیت و آماده‌سازی نهایی پروژه استفاده می‌شود.  
هر سکشن شامل موارد ضروری برای بررسی است.**

> [!TIP]
> < / > الگو‌های پیاده‌سازی برای توسعه‌دهندگان ➜ [UX Patterns for Devs](https://uxpatterns.dev/en)

## ☰ لیست موارد

- [📈 SEO](#-1-seo)
- [🔒 Security](#-2-security)
- [📝 Documentation](#-3-documentation)
- [Logs](#-4-logs)
- [Services](#-5-services)
- [📊 Performance](#-6-performance)
- [Dependency](#-7-dependency)
- [🌐 Accessibility](#-8-accessibility)
- [Test](#-9-test)
- [UI](#-10-ui)
- [Deploy](#-11-deploy)
- [Versioning](#-12-versioning)
- [Flow](#-13-flow)
- [👨‍💻 Code Review](#-14-code-review)

---

## 📈 1. SEO

- #### Meta Tags و ساختار HTML
  - [ ] `<title></title>` مناسب (max 60)
  - [ ] `<meta name="description" content="">` مرتبط برای هر صفحه (max 160 characters)
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
- #### Link Strategy
  - [ ] لینک خوانا، برای مثال: `<Link href="/seo-best-practices">` [نمونه](https://substackcdn.com/image/fetch/$s_!fOM2!,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F0dfd32c6-e2f8-433b-bdb1-5b9cf88717ba_1600x500.png)
  - [ ] لینک‌های خارجی با `rel="noopener noreferrer"`
  - [ ] 404 نشدن لینک‌ها
- #### International SEO (در صورت استفاده از i18n)
  - [ ] استفاده از `hreflang`
  - [ ] ساخت _sitemap_ جدا برای هر زبان
  - [ ] مسیرهای داینامیک سازگار با _locale_

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 🔒 2. Security

- #### Authentication & Authorization
  - [ ] ذخیره نکردن توکن در _localStorage_ (استفاده از [HttpOnly Cookie](https://nextjs.org/docs/app/api-reference/functions/cookies))
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

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 📝 3. Documentation

- #### README file
  - [ ] توضیح کامل پروژه
  - [ ] دستور نصب و اجرا
  - [ ] ساختار پوشه‌ها
  - [ ] API Routing
  - [ ] توضیح تکنولوژی‌ها
  - [ ] نحوه _Build_ و _Deploy_
  - [ ] _Node_ version
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

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 4. Logs

- [ ] ساختار مشخص لاگ‌ها
- [ ] سطح‌بندی (info, warn, error)
- [ ] ذخیره‌سازی امن لاگ‌ها
- [ ] لاگ‌گیری از خطاهای حساس
- [ ] امکان غیرفعال‌سازی لاگ در prod

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 5. Services

- [ ] تمام سرویس‌ها مستندسازی شده
- [ ] Retry و Timeout بررسی شده
- [ ] Error Handling کامل
- [ ] سوییچ محیط dev/prod
- [ ] تست Callهای API

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 📊 6. Performance

- #### Code Performance
  - [x] جلوگیری از _re-render_ اضافی
  - [ ] [dynamic imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import)
  - [ ] انتقال logic به [RSC](https://dev.to/hasunnilupul/react-server-components-rsc-a-deep-dive-with-examples-and-diagrams-3g4c)، برای کاهش بار جاوا اسکریپت
  - [ ] کش کردن داده با [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Request/cache)
  - [ ] _Event Listeners_ [clean ups](https://refine.dev/blog/useeffect-cleanup/#introduction)
  - [ ] [Code Splitting](https://developer.mozilla.org/en-US/docs/Glossary/Code_splitting)
- #### Page Load
  - [ ] استفاده بهینه از _SSG/SSR_
  - [ ] استفاده از [Next/Image](https://nextjs.org/docs/pages/getting-started/images)
  - [ ] استفاده از [Next/Font](https://nextjs.org/docs/pages/getting-started/fonts)
  - [ ] کاهش Layout Shift با width/height تصاویر, skeleton loader, placeholder blur
- #### Image Loading
  - [ ] تصویر LCP با `priority={true}`
  - [ ] لوگوی سایت، تصویر Hero و اسلایدر بالای صفحه به صورت `loading="eager"`
  - [ ] تصاویر کارد بلاگ‌ها، مقالات، داخل مدال، فوتر به صورت `loading="lazy"`
- #### Lighthouse
  - [ ] LCP زیر ۲.۵ ثانیه
  - [ ] CLS < 0.1

> [!TIP]
> < / > [موارد تکمیلی](https://github.com/ms-fadaei/Front-End-Performance-Checklist)

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 7. Dependency

- [ ] حذف پکیج‌های غیرضروری
- [ ] آپدیت وابستگی‌ها
- [ ] امنیت نسخه‌ها
- [ ] قفل نسخه (lockfile)

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 🌐 8. Accessibility

- [ ] استفاده از _alt text_ تصاویر، به‌جز برای تصاویر تزئینی (بک‌گراند، آیکون‌های کنار متن)
- [ ] استفاده از _ARIA Attributes_ به جز برای *Semantic Tag*ها
- [ ] استفاده از Focus State، [مثال Tailwind](https://Tailwindcss.com/docs/hover-focus-and-other-states)
- [ ] کنتراست رنگ‌ها طبق استاندارد [WCAG](https://webaim.org/resources/contrastchecker/)
- [ ] استفاده از `<label />` برای فیلدها
- [ ] مشخص کردن زبان برنامه `<html lang="fa">`
- [ ] استفاده از [Skip Navigation Link](https://webaim.org/techniques/skipnav/)، [کاربرد Tailwind](https://stackoverflow.com/questions/74226815/how-to-add-a-skip-to-main-content-link-that-only-shows-to-screen-readers-usin)
- [ ] کاربرد منطقی از [_Tabindex_](https://webaim.org/techniques/keyboard/tabindex), استفاده فقط برای _non-semantic clickable elements_

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 9. Test

- [ ] تست واحد (Unit)
- [ ] تست integration
- [ ] تست E2E
- [ ] پوشش تست‌ها (Coverage)
- [ ] تست رگرسیون

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 10. UI

- [ ] رعایت Design System
- [ ] واکنش‌گرایی (Responsive)
- [ ] انیمیشن‌های سبک
- [ ] رعایت Padding/Spacing
- [ ] RTL/LTR در صورت نیاز

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 11. Deploy

- [ ] Pipeline آماده
- [ ] Build بدون خطا
- [ ] ENVهای لازم ست شده
- [ ] Health-check
- [ ] مانیتورینگ فعال

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 12. Versioning

- [ ] رعایت Semantic Versioning
- [ ] Tagهای منتشر شده
- [ ] تغییرات در CHANGELOG ثبت شده

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 13. Flow

- [ ] نمودار جریان (Flow Diagram)
- [ ] نقشه مسیر کاربر (User Flow)
- [ ] Edge-caseها بررسی شده
- [ ] رفتار خطا در جریان مشخص

**[⬆ بازگشت به بالا](#-لیست-موارد)**

---

## 👨‍💻 14. Code Review

- #### Readability & Naming
  - [ ] نام‌گذاری بر اساس [استاندارد‌ها](https://github.com/kettanaito/naming-cheatsheet)
  - [ ] عدم استفاده از مخفف‌های بی‌معنی (`tmp`, `val`, `obj`), [نمونه](https://github.com/hamettio/clean-code-javascript)
  - [ ] استفاده از [JSDoc](https://jsdoc.app/tags-example)
- #### Component Structure
  - [ ] کامپوننت کوچک و تک‌وظیفه‌ای ([Single Responsibility](https://dev.to/mikhaelesa/single-responsibility-principle-in-react-10oc))
  - [ ] استفاده حداکثری از RSC در صورت نبود interactivity
  - [ ] استفاده از Client Component فقط در صورت نیاز (state / effect / events)
- #### Clean Code & Maintainability
  - [ ] استفاده از توابع کوتاه و تک‌هدفه
  - [ ] استفاده از [early return](https://javascript.plainenglish.io/early-return-with-react-hooks-f96fa4a33124)ها
  - [ ] استفاده از async/await به جای then/catch زنجیره‌ای
  - [ ] error handling در سطح کامپوننت و API
- #### TypeScript Quality
  - [ ] عدم استفاده از any
  - [ ] پیاده‌سازی type برای تمام توابع
  - [ ] استفاده از unknown برای ورودی‌های ناشناخته
- #### CSS & Styling Consistency
  - [ ] استفاده از Tailwind (طبق ترجیح پروژه) — بدون inline style
  - [ ] عدم وجود فایل CSS بزرگ و پیچیده
  - [ ] پیاده‌سازی تم و رنگ‌ها در فایل کانفیگ Tailwind
- #### Code Accessibility
  - [ ] عدم استفاده از clickable `div`
  - [ ] استفاده از `<label />` برای فیلد‌ها
  - [ ] استفاده از ARIA attributes برای کامپوننت‌های interactive
- #### Error Boundaries & Edge Cases
  - [ ] استفاده از Next Error Handling
  - [ ] پیاده‌سازی صفحات خطا، و حالات loading / empty / error

**[⬆ بازگشت به بالا](#-لیست-موارد)**

</div>

<div dir="auto">

# 📋 Project Checklist

**این چک‌لیست برای کنترل کیفیت و آماده‌سازی نهایی پروژه استفاده می‌شود.  
هر سکشن شامل موارد ضروری برای بررسی است.**

> ‎🛠 الگوهای پیاده‌سازی برای توسعه‌دهندگان ➜ [UX Patterns for Devs](https://uxpatterns.dev/en)

## 💡 نحوه استفاده

**موارد هر بخش در دو درجه اهمیت از لحاظ بررسی قرار گرفته‌اند که به‌شرح زیر هستند:**

- 🔴 مشخص می‌کند این مورد حتماً نیاز به‌رعایت شدن دارد
- 🟡 مشخص می‌کند این مورد بر اساس نیازمندی‌های پروژه و هماهنگی با مسئول مربوطه نیاز به بررسی دارد

**در مقابل هر مورد ممکن است رفرنسی قرار گرفته باشد یا خود عنوان/سرفصل در قالب لینک نوشته شده باشد.
قالب رفرنس‌ها در بخش‌های زیر دسته‌بندی شده‌اند.**

- 📚: documentation or article
- 🛠️: online tool / testing tool
- 🖼️: media or video content

---

## ☰ لیست موارد

- [📈 SEO](#-seo)
- [🔒 Security](#-security)
- [📝 Documentation](#-documentation)
- [Logs](#-logs)
- [Services](#-services)
- [📊 Performance](#-performance)
- [📦 Dependency](#-dependency)
- [🌐 Accessibility](#-accessibility)
- [🔬 Test](#-test)
- [UI](#-ui)
- [Deploy](#-deploy)
- [🏷️ Versioning](#-versioning)
- [Flow](#-flow)
- [👨🏻‍💻 Code Review](#-code-review)

---

## 📈 SEO

- #### Meta Tags و ساختار HTML
  - [ ] `<title></title>` مناسب (max 60)
  - [ ] `<meta name="description" content="">` مرتبط برای هر صفحه (max 160 characters)
  - [ ] `<meta name="robots">` (برای صفحات بلاک‌شده یا غیر indexable)
  - [ ] `<link rel="canonical" href=""https://example.com/>` برای جلوگیری از duplicate content
  - [ ] `<meta name="viewport">` برای رسپانسیو
- #### [Social Media](https://ogp.me/)
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

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 🔒 Security

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

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 📝 Documentation

- #### README file
  - [ ] توضیح کامل پروژه
  - [ ] دستور نصب و اجرا
  - [ ] ساختار پوشه‌ها
  - [ ] API Routing
  - [ ] توضیح packageها
  - [ ] نحوه _Build_ و _Deploy_
  - [ ] _Node_ version
  - [ ] *TODO*های Developer
- #### Architecture Docs
  - [ ] Folder structure توضیح
  - [ ] Data Flow
  - [ ] Routing Flow
- #### Contribution Guide
  - [ ] قوانین _commit_
  - [ ] قوانین _branch_
- #### CHANGELOG
  - [ ] نسخه‌ها و تغییرات
  - [ ] اضافه شدن قابلیت‌ها
  - [ ] رفع باگ‌ها

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## Logs

- [ ] ساختار مشخص لاگ‌ها
- [ ] سطح‌بندی (info, warn, error)
- [ ] ذخیره‌سازی امن لاگ‌ها
- [ ] لاگ‌گیری از خطاهای حساس
- [ ] امکان غیرفعال‌سازی لاگ در prod

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## Services

- [ ] تمام سرویس‌ها مستندسازی شده
- [ ] Retry و Timeout بررسی شده
- [ ] Error Handling کامل
- [ ] سوییچ محیط dev/prod
- [ ] تست Callهای API

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 📊 Performance

- #### Code Performance

  - [x] جلوگیری از _re-render_ اضافی
  - [ ] [dynamic imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import)
  - [ ] _Event Listeners_ [clean ups](https://refine.dev/blog/useeffect-cleanup/#introduction)
  - [ ] [Code Splitting](https://developer.mozilla.org/en-US/docs/Glossary/Code_splitting)

- #### Page Load
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

> [موارد تکمیلی](https://github.com/ms-fadaei/Front-End-Performance-Checklist)

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 📦 Dependency

- [ ] بررسی Dependencyهای غیر ضروری با دستور `npx depcheck`
- [ ] بررسی نسخه‌های جدید با دستور `npm update`
- [ ] بررسی امنیت نسخه‌ها با دستور `npm audit`
- [ ] بررسی حجم Dependency در [Bundlephobia](https://bundlephobia.com/)
- [ ] دسته‌بندی صحیح Packageها در دو دسته‌بندی `dependencies` و `devDependencies`
- [ ] بررسی [Transitive Dependencies](https://lexi-lambda.github.io/blog/2016/08/24/understanding-the-npm-dependency-model/) با دستور `npm ls`

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 🌐 Accessibility

- [ ] استفاده از _alt text_ تصاویر، به‌جز برای تصاویر تزئینی (بک‌گراند، آیکون‌های کنار متن)
- [ ] استفاده از _ARIA Attributes_ به جز برای *Semantic Tag*ها
- [ ] استفاده از Focus State، [مثال Tailwind](https://Tailwindcss.com/docs/hover-focus-and-other-states)
- [ ] کنتراست رنگ‌ها طبق استاندارد [WCAG](https://webaim.org/resources/contrastchecker/)
- [ ] استفاده از `<label />` برای فیلدها
- [ ] مشخص کردن زبان برنامه `<html lang="fa">`
- [ ] استفاده از [Skip Navigation Link](https://webaim.org/techniques/skipnav/)، [کاربرد Tailwind](https://tailwindcss.com/docs/display#screen-reader-only)
- [ ] کاربرد منطقی از [_Tabindex_](https://webaim.org/techniques/keyboard/tabindex), استفاده فقط برای _non-semantic clickable elements_

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 🔬 Test

- [ ] تست‌نویسی برای توابعی که دارای logic هستند

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## UI

- [ ] رعایت Design System
- [ ] واکنش‌گرایی (Responsive)
- [ ] انیمیشن‌های سبک
- [ ] رعایت Padding/Spacing
- [ ] RTL/LTR در صورت نیاز

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## Deploy

- [ ] Pipeline آماده
- [ ] Build بدون خطا
- [ ] ENVهای لازم ست شده
- [ ] Health-check
- [ ] مانیتورینگ فعال

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 🏷️ Versioning {#-versioning}

- #### Readability & Naming
  - [ ] رعایت اصول [Semantic Versioning](https://www.geeksforgeeks.org/software-engineering/introduction-semantic-versioning/)
- #### CHANGELOG / Release Notes
  - [ ] ثبت تغییرات هر نسخه در CHANGELOG
- #### Versioning داخل پروژه
  - [ ] آپدیت نسخه در `package.json`
- #### Documentation Update
  - [ ] آپدیت هر نسخه جدید در README/Docs

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## Flow

- [ ] نمودار جریان (Flow Diagram)
- [ ] نقشه مسیر کاربر (User Flow)
- [ ] Edge-caseها بررسی شده
- [ ] رفتار خطا در جریان مشخص

**[⇡ بازگشت به بالا](#-لیست-موارد)**

---

## 👨🏻‍💻 Code Review

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

**[⇡ بازگشت به بالا](#-لیست-موارد)**

</div>

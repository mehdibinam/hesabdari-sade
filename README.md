# سیستم انبارگردانی آسان و هوشمند

**نسخه: ۱.۱.۰**

ابزاری سبک، رایگان و تک فایلی (Single-file) برای ثبت موجودی انبار، ارزیابی ارزش خرید و فروش کالا ها و تغییر قیمت گروهی. تمام منطق برنامه درون یک فایل `index.html` قرار دارد؛ نیازی به نصب، سرور، دیتابیس یا حساب کاربری نیست. کافی است فایل را در مرورگر باز کنید.

> تمام پردازش ها در مرورگر همان دستگاه انجام می شود و هیچ اطلاعاتی به بیرون ارسال نمی شود.

**نسخه آنلاین:** https://mehdibinam.github.io/hesabdari-sade/

<img width="1919" height="861" alt="hesabdari sade" src="https://github.com/user-attachments/assets/4b2a030e-2bcf-42f3-9122-034c458634f6" />

---

## فهرست مطالب

- [شروع سریع](#شروع-سریع)
- [امکانات به تفصیل](#امکانات-به-تفصیل)
  - [ثبت و ویرایش کالا](#ثبت-و-ویرایش-کالا)
  - [کپی کردن کالا](#کپی-کردن-کالا)
  - [جدول انبار و محاسبات آن](#جدول-انبار-و-محاسبات-آن)
  - [جستجو و فیلتر هوشمند](#جستجو-و-فیلتر-هوشمند)
  - [مرتب سازی و صفحه بندی](#مرتب-سازی-و-صفحه-بندی)
  - [داشبورد آمار](#داشبورد-آمار)
  - [تغییر قیمت دسته جمعی](#تغییر-قیمت-دسته-جمعی)
  - [ورود اطلاعات (Import)](#ورود-اطلاعات-import)
  - [خروجی گرفتن (Export)](#خروجی-گرفتن-export)
  - [ریست کردن داده ها](#ریست-کردن-داده-ها)
  - [رابط کاربری، تم و زبان](#رابط-کاربری-تم-و-زبان)
  - [ذخیره سازی و میانبرها](#ذخیره-سازی-و-میانبرها)
- [قالب فایل ورودی](#قالب-فایل-ورودی)
- [محدودیت ها و نکات مهم](#محدودیت-ها-و-نکات-مهم)
- [فناوری های مورد استفاده](#فناوری-های-مورد-استفاده)
- [لایسنس](#لایسنس)
- [English Documentation](#english-documentation)

---

## شروع سریع

1. فایل `index.html` را در هر مرورگر مدرن (Chrome، Edge، Firefox) باز کنید یا از [نسخه آنلاین](https://mehdibinam.github.io/hesabdari-sade/) استفاده نمایید.
2. روی دکمه **«ثبت کالای جدید»** (سمت راست فیلد جستجو) کلیک کنید یا کلید `F2` را بفشارید.
3. نام، قیمت خرید، قیمت فروش و تعداد را وارد کنید. کد کالا، دسته بندی و بارکد اختیاری اند.
4. روی **«تایید و ثبت نهایی»** کلیک کنید؛ کالا بلافاصله در جدول و آمار ظاهر می شود.
5. برای بارگذاری انبوه از **«بارگذاری فایل»** و برای پشتیبان گیری از **«خروجی گرفتن»** استفاده کنید.

---

## امکانات به تفصیل

### ثبت و ویرایش کالا

فرم ثبت کالا شامل فیلد های زیر است:

<table dir="rtl">
  <thead>
    <tr><th>فیلد</th><th>نوع</th><th>اجباری</th><th>توضیح</th></tr>
  </thead>
  <tbody>
    <tr><td>نام کامل محصول</td><td>متن</td><td>بله</td><td>نام نمایشی کالا در جدول و جستجو</td></tr>
    <tr><td>قیمت خرید واحد</td><td>عدد (تومان)</td><td>بله</td><td>حداقل صفر؛ با جداکننده هزارگان به صورت زنده نمایش داده می شود</td></tr>
    <tr><td>قیمت فروش واحد</td><td>عدد (تومان)</td><td>بله</td><td>حداقل صفر؛ نمایش زنده هنگام تایپ</td></tr>
    <tr><td>تعداد کالا (موجودی)</td><td>عدد</td><td>بله</td><td>حداقل صفر؛ مبنای محاسبه ارزش ها</td></tr>
    <tr><td>کد کالا</td><td>متن</td><td>خیر</td><td>شناسه یکتا؛ در صورت خالی بودن «—» نمایش داده می شود</td></tr>
    <tr><td>دسته بندی</td><td>متن / پیشنهادی</td><td>خیر</td><td>با لیست دسته بندی های موجود تکمیل خودکار می شود؛ در صورت خالی بودن «متفرقه» ثبت می شود</td></tr>
    <tr><td>بارکد محصول</td><td>متن</td><td>خیر</td><td>برای فیلتر مستقیم بارکدخوان ها</td></tr>
  </tbody>
</table>

قوانین و رفتارها:

- **اعتبار سنجی تکراری بودن کد:** فقط زمانی که کد وارد شده باشد بررسی می شود و کالای هم کد (با در نظرگیری حروف کوچک و بزرگ) رد می گردد.
- **محاسبات زنده:** ارزش کل خرید = `تعداد × قیمت خرید` و ارزش کل فروش = `تعداد × قیمت فروش`، بلافاصله زیر فرم محاسبه و نمایش داده می شوند.
- **ویرایش:** با کلیک بر آیکن مداد، فرم با اطلاعات کالا پر می شود؛ شناسه داخلی کالا حفظ می گردد.
- **حذف:** با پنجره تأیید SweetAlert همراه است و نام و کد کالا در پیام نمایش داده می شود.
- **دکمه انصراف:** به رنگ قرمز (rose) طراحی شده تا از کلیک اشتباه و از دست رفتن فرم جلوگیری کند.

### کپی کردن کالا

آیکن کپی (سبز) در ستون عملیات، فرم ثبت کالا را با مشخصات همان کالا باز می کند. تفاوت ها:

- کد کالا به صورت خودکار با پسوند `-copy` ساخته می شود؛ اگر این کد هم وجود داشته باشد، پسوندهای `-copy2`، `-copy3` و … تا رسیدن به کد آزاد امتحان می شوند.
- اگر کالای اصلی کدی نداشته باشد، کد کپی هم خالی می ماند.
- بقیه فیلد ها (نام، دسته بندی، قیمت ها، تعداد و بارکد) دقیقاً کپی می شوند و تنها کافی است تغییرات مورد نظر را اعمال و تأیید کنید.

### جدول انبار و محاسبات آن

جدول دارای ۱۱ ستون است: ردیف، کد کالا، نام محصول، دسته بندی، قیمت خرید، قیمت فروش، تعداد، ارزش کل خرید، ارزش کل فروش، بارکد و عملیات.

- **ارزش کل خرید** = `تعداد × قیمت خرید واحد` (با رنگ سبز).
- **ارزش کل فروش** = `تعداد × قیمت فروش واحد` (با رنگ آبی).
- **هشدار موجودی:** تعداد صفر با نشان قرمز، و تعداد کمتر از ۵ با نشان زرد برجسته می شود.
- **سرستون های چسبنده:** هنگام اسکرول عمودی، سرستون جدول در بالا باقی می ماند.
- **تغییر عرض ستون ها:** با کشیدن لبه سمت چپ هر سرستون می توان عرض آن را تنظیم کرد (ستون عملیات از این قابلیت مستثناست).
- **نمایش مقادیر خالی:** کد کالا و بارکد خالی به صورت «—» نمایش داده می شوند.
- محتوای وارد شده توسط کاربر قبل از نمایش، HTML-escaped می شود (جلوگیری از تزریق HTML).

### جستجو و فیلتر هوشمند

- **جستجوی متنی:** روی نام و کد کالا به صورت هم زمان عمل می کند. عبارت جستجو به کلمات تشکیل دهنده تقسیم می شود و هر کلمه باید در نام یا کد یافت شود (بنابراین ترتیب کلمات مهم نیست).
- **نرمال سازی فارسی:** حروف `آ / ا / أ / إ`، `ی / ي` و `ک / ك` یکسان در نظر گرفته می شوند؛ فاصله، خط تیره، زیرخط، اسلش، کاما و پرانتز نادیده گرفته می شوند.
- **فیلتر بارکد:** جستجوی رشته ای ساده و مستقیم روی مقدار بارکد.
- **فیلتر دسته بندی:** لیست کشویی که به صورت پویا از دسته بندی های موجود در انبار ساخته می شود.
- سه فیلتر به صورت `AND` ترکیب می شوند و با تایپ، جدول بلافاصله به روز می شود.

### مرتب سازی و صفحه بندی

- مرتب سازی با کلیک بر سرستون های کد، نام، دسته بندی، قیمت خرید، قیمت فروش، تعداد و بارکد (کلیک مجدد معکوس می کند).
- آیکن کنار سرستون فعال جهت صعودی یا نزولی را نشان می دهد.
- **مرتب سازی طبیعی (Natural sort)** برای کدها: `ap-1`، `ap-2`، `ap-10` به ترتیب درست قرار می گیرند.
- صفحه بندی با دکمه های قبلی و بعدی، شماره صفحات و خلاصه «نمایش کالا ها از X تا Y از کل Z کالا».
- منوی **«نمایش در هر صفحه»**: ۵۰ کالا (پیش فرض) یا «همه اقلام».
- تغییر فیلتر یا مرتب سازی، شماره صفحه را به ۱ بازنشانی می کند.

### داشبورد آمار

چهار کارت آماری در بالای صفحه:

1. **تنوع کالا ها** — تعداد رکورد های ثبت شده.
2. **کل موجودی فیزیکی** — مجموع `تعداد` تمام کالا ها.
3. **ارزش خرید کل انبار** — جمع `تعداد × قیمت خرید` برای تمام کالا ها.
4. **ارزش فروش کل انبار** — جمع `تعداد × قیمت فروش` برای تمام کالا ها.

اعداد با قالب فارسی (`Intl.NumberFormat('fa-IR')`) و جداکننده هزارگان نمایش داده می شوند.

### تغییر قیمت دسته جمعی

پنجره مخصوص با تنظیمات زیر:

<table dir="rtl">
  <thead>
    <tr><th>تنظیم</th><th>گزینه ها</th></tr>
  </thead>
  <tbody>
    <tr><td>محدوده اعمال</td><td>همه کالا ها / فقط کالا های فیلتر شده فعلی</td></tr>
    <tr><td>قیمت هدف</td><td>قیمت خرید / قیمت فروش / هر دو</td></tr>
    <tr><td>نوع عملیات</td><td>افزایش (+) / کاهش (−)</td></tr>
    <tr><td>روش اعمال</td><td>درصدی (٪) / مبلغ ثابت (تومان)</td></tr>
    <tr><td>مقدار</td><td>عدد مثبت (پیشنویس زنده نمایش داده می شود)</td></tr>
  </tbody>
</table>

قوانین محاسبه:

- حالت درصدی: `قیمت جدید = قیمت قدیم × (۱ ± مقدار / ۱۰۰)`.
- حالت مبلغ ثابت: `قیمت جدید = قیمت قدیم ± مقدار`.
- نتیجه **گرد می شود** (به نزدیک ترین عدد صحیح تومان) و در حالت کاهش، حداقل صفر در نظر گرفته می شود (قیمت منفی نمی شود).
- قبل از اعمال، پنجره تأیید دوم با ذکر تعداد کالا ها، نوع عملیات، مقدار و قیمت هدف نمایش داده می شود.
- عملیات مستقیم و **غیر قابل بازگشت** است؛ توصیه می شود پیش از آن خروجی پشتیبان تهیه کنید.

### ورود اطلاعات (Import)

فرمت های پذیرفته شده: `.xlsx`، `.xls`، `.csv` و `.json` (پشتیبان صادر شده توسط همین ابزار).

- سرستون ها می توانند فارسی یا انگلیسی باشند و به صورت هوشمند شناسایی می شوند (نگاه کنید به جدول [قالب فایل ورودی](#قالب-فایل-ورودی)).
- تنها **نام محصول** اجباری است؛ سطر های فاقد نام رد می شوند.
- مقادیر عددی تمیز می شوند (جداکننده ها و واحد ها حذف می شوند)؛ مقادیر خالی صفر در نظر گرفته می شوند.
- دسته بندی خالی به «متفرقه» تبدیل می شود.
- پس از خواندن فایل، پنجره پیشنویس با سه گزینه ظاهر می شود:
  - **جایگزینی کامل:** لیست فعلی پاک و کالا های فایل جایگزین می شوند.
  - **ادغام:** کالا های هم کد به روز رسانی می شوند و کالا های جدید اضافه می گردند (گزارش تعداد کالا های جدید نمایش داده می شود).
  - **انصراف:** هیچ تغییری اعمال نمی شود.
- فایل JSON پشتیبان، شناسه های داخلی (`id`) اصلی را حفظ می کند.

### خروجی گرفتن (Export)

<table dir="rtl">
  <thead>
    <tr><th>فرمت</th><th>توضیح</th></tr>
  </thead>
  <tbody>
    <tr><td><strong>XLSX</strong></td><td>فایل اکسل رسمی با جهت چپ به راست (RTL) مناسب نمایش فارسی؛ شامل تمام ستون ها و مبالغ محاسبه شده</td></tr>
    <tr><td><strong>CSV</strong></td><td>متن ساده با BOM یونیکد (<code>\uFEFF</code>) تا فارسی ها در اکسل خراب نشوند</td></tr>
    <tr><td><strong>JSON</strong></td><td>پشتیبان کامل ساختاریافته شامل شناسه ها و تمام فیلد ها، مناسب انتقال به دستگاه دیگر</td></tr>
  </tbody>
</table>

سرستون های خروجی بسته به زبان فعال (فارسی یا انگلیسی) تولید می شوند.

### ریست کردن داده ها

- دکمه **«ریست کردن»** در نوار ابزار (سمت چپ) قرار دارد.
- پنجره تأیید هشدار می دهد که تمام N کالا پاک شده و عملیات غیر قابل بازگشت است.
- با تأیید: لیست کالا ها، سه فیلتر جستجو و بارکد و دسته بندی، شماره صفحه و ذخیره سازی مرورگر خالی می شوند.
- پیام موفقیت به صورت toast نمایش داده می شود.

### رابط کاربری، تم و زبان

- **حالت تاریک و روشن:** آیکن ماه یا خورشید در سمت چپ هدر، تم را تغییر می دهد؛ تمام کارت ها، جدول، مودال ها و پیام ها پوشش داده می شوند.
- **تغییر زبان:** دکمه `FA / EN` متن های ثابت رابط را ترجمه می کند؛ متن های پویا (ردیف ها، پیام ها، دکمه ها) نیز بر اساس زبان فعال ساخته می شوند.
- **جهت چینش:** در حالت فارسی `rtl` و در حالت انگلیسی `ltr` تنظیم می شود؛ آیکن قبلی و بعدی صفحه بندی نیز برعکس می گردد.
- **طراحی واکنشگرا:** چیدمان بر اساس اندازه صفحه (موبایل، تبلت، دسکتاپ) تنظیم می شود.
- **راهنمای ماوس:** آیکن ها و برخی عناوین دارای tooltip توضیحی اند.

### ذخیره سازی و میانبرها

<table dir="rtl">
  <thead>
    <tr><th>کلید localStorage</th><th>محتوا</th></tr>
  </thead>
  <tbody>
    <tr><td><code>inventory_data_toman</code></td><td>آرایه کالا ها (ذخیره سازی اصلی)</td></tr>
    <tr><td><code>inventory_lang</code></td><td>زبان انتخاب شده (<code>fa</code> یا <code>en</code>)</td></tr>
    <tr><td><code>inventory_theme</code></td><td>تم انتخاب شده (<code>light</code> یا <code>dark</code>)</td></tr>
  </tbody>
</table>

- **میانبر `F2`:** باز کردن سریع فرم ثبت کالای جدید.
- تمام تغییرات (افزودن، ویرایش، حذف، کپی، تغییر قیمت، ریست) بلافاصله در localStorage ذخیره می شوند.

---

## قالب فایل ورودی

سطر اول فایل باید سرستون باشد. نامهای قابل قبول (فارسی و انگلیسی):

<table dir="rtl">
  <thead>
    <tr><th>ستون</th><th>نام های قابل قبول</th><th>اجباری</th></tr>
  </thead>
  <tbody>
    <tr><td>نام محصول</td><td>نام محصول، نام کالا، نام، عنوان، product، name</td><td>بله</td></tr>
    <tr><td>کد کالا</td><td>کد کالا، کد، شناسه، code، id</td><td>خیر</td></tr>
    <tr><td>دسته بندی</td><td>دسته بندی، دسته، گروه، category، group</td><td>خیر</td></tr>
    <tr><td>قیمت خرید</td><td>قیمت خرید، خرید، purchase، buy</td><td>خیر</td></tr>
    <tr><td>قیمت فروش</td><td>قیمت فروش، فروش، selling، sell</td><td>خیر</td></tr>
    <tr><td>تعداد</td><td>تعداد کالا، تعداد، موجودی، qty، quantity، count</td><td>خیر</td></tr>
    <tr><td>بارکد</td><td>بارکد محصول، بارکد، barcode</td><td>خیر</td></tr>
  </tbody>
</table>

مثال سطر سرستون:

```csv
کد کالا,نام محصول,دسته بندی,قیمت خرید,قیمت فروش,تعداد,بارکد
ap-1,گوشی شیائومی Redmi Note 12,الکترونیک,4500000,5200000,15,6260112345678
```

---

## محدودیت ها و نکات مهم

- داده ها فقط در مرورگر همان دستگاه ذخیره می شوند و بین دستگاه ها به صورت خودکار همگام سازی نمی شوند؛ برای انتقال از خروجی JSON استفاده کنید.
- پاک کردن اطلاعات مرورگر (Clear site data) یا زدن دکمه ریست، داده ها را حذف می کند.
- ابزار چند کاربره یا مبتنی بر سرور نیست و دارای حساب کاربری یا سطح دسترسی نمی باشد.
- واحد پول تمام مبالغ **تومان** است و نرخ ارز یا تبدیل خودکار ندارد.
- محاسبه سود یا زیان به صورت جداگانه در داشبورد وجود ندارد؛ می توانید ارزش فروش منهای ارزش خرید را به صورت دستی محاسبه کنید.
- کتابخانه ها از طریق CDN بارگذاری می شوند؛ بنابراین **اولین اجرا به اتصال اینترنت نیاز دارد**. پس از بارگذاری، خود ابزار به صورت محلی کار می کند.
- باز کردن فایل محلی با برخی مرورگرها محدودیت دارد؛ در صورت بروز مشکل، فایل را از طریق یک local server ساده (مثلاً `python -m http.server`) باز کنید یا از [نسخه آنلاین](https://mehdibinam.github.io/hesabdari-sade/) استفاده نمایید.

---

## فناوری های مورد استفاده

- **HTML5 / CSS3 / JavaScript خالص** (بدون framework سمت سرور)
- [Tailwind CSS](https://tailwindcss.com) — طراحی رابط و تم ها (CDN)
- [Font Awesome](https://fontawesome.com) — آیکن ها (CDN)
- [Vazir Font](https://github.com/rastikerdar/vazir-font) — فونت فارسی (CDN)
- [SweetAlert2](https://sweetalert2.github.io) — پنجره ها و اعلان ها (CDN)
- [SheetJS](https://sheetjs.com) — خواندن و نوشتن Excel و CSV (CDN)

---

## لایسنس

این ابزار تحت لایسنس **MIT** منتشر شده است. استفاده، کپی، تغییر، توزیع و استفاده تجاری آزاد است، مشروط بر حفظ اخطار کپی رایت. جزئیات کامل در فایل [`LICENSE`](LICENSE) موجود است.

---

# English Documentation

## Overview

**Easy & Smart Inventory System** (v1.1.0) is a free, single-file inventory and accounting tool. Everything lives in `index.html` — no installation, server, database, or account required. Open the file in a browser or use the [online version](https://mehdibinam.github.io/hesabdari-sade/) and start recording stock.

All processing happens locally in your browser; no data is ever sent to a server.

## Quick start

1. Open `index.html` in a modern browser (or use the online version).
2. Click **Add New Product** (to the right of the search box) or press `F2`.
3. Fill in name, purchase price, selling price, and quantity. Code, category, and barcode are optional.
4. Click **Confirm and save**. The product appears immediately in the table and dashboard.
5. Use **Import File** for bulk loading and **Export** for backups.

## Feature reference

- **Product management** — add, edit, duplicate, and delete products. Only name, prices, and quantity are required. Empty codes display as `—`; empty categories default to *Misc*.
- **Duplicate** — copies all fields into the form and auto-generates a unique code with a `-copy`, `-copy2`, … suffix (or leaves it empty if the original had none).
- **Inventory table** — 11 columns with live `quantity × price` totals, stock badges (red = 0, amber = < 5), sticky header, sortable headers, and drag-to-resize columns. User content is HTML-escaped.
- **Smart Persian search** — matches name and code word-by-word, ignoring word order and normalizing Persian/Arabic letter variants (`ی/ي`, `ک/ك`, `آ/ا`) and punctuation.
- **Filters & sorting** — direct barcode filter, dynamic category dropdown, natural numeric sorting for codes (`ap-2` before `ap-10`), pagination (50 items or all), and auto-reset to page 1 on filter changes.
- **Dashboard** — product variety, total physical stock, total purchase value, and total selling value, formatted with Persian numerals.
- **Bulk price change** — all products or filtered ones; purchase, selling, or both prices; increase/decrease by percentage or fixed Toman; results rounded and clamped at zero; double confirmation before applying (irreversible).
- **Import** — XLSX, XLS, CSV, and JSON backups; Persian or English headers; replace-all or merge-by-code strategies with a confirmation dialog.
- **Export** — XLSX (RTL sheet), CSV (UTF-8 BOM for Persian), and full structured JSON backup; headers follow the active UI language.
- **Reset** — clears all table data and filters after a confirmation warning.
- **UI** — dark/light theme toggle and Persian/English language toggle in the header (localized text, `rtl`/`ltr` direction, reversed pagination arrows), responsive layout, and tooltips.
- **Persistence** — data stored under `inventory_data_toman`; preferences under `inventory_lang` and `inventory_theme`. `F2` opens the add form.

## Import header names

Only **Name** is required. Accepted aliases: Name (`نام محصول`, `نام کالا`, `name`, `product`), Code (`کد کالا`, `code`, `id`), Category (`دسته بندی`, `category`), Purchase (`قیمت خرید`, `buy`, `purchase`), Selling (`قیمت فروش`, `sell`, `selling`), Quantity (`تعداد`, `qty`, `quantity`), Barcode (`بارکد`, `barcode`).

## Notes & limitations

- Local-only storage: no automatic sync between devices — use the JSON backup to transfer data.
- Clearing browser data or using Reset permanently deletes records.
- Not a multi-user/server solution; no accounts or permissions.
- All amounts are in **Toman**; no currency conversion.
- CDN dependencies require an internet connection on first load.

## License

Released under the [MIT License](LICENSE) — free for personal and commercial use, modification, and distribution.

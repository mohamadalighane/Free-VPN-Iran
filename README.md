# 🚀 Poogo - AI Prompts Platform

یک پلتفرم تمام‌عیار برای مدیریت و اشتراک‌گذاری پرومپت‌های AI با رابط کاربری فارسی (RTL)، تبلیغات، و پنل مدیریت حرفه‌ای.

## ✨ ویژگی‌ها

### 🎨 رابط کاربری
- **طراحی مدرن**: رابط‌شناس و زیبا با Tailwind CSS
- **پشتیبانی کامل RTL**: طراحی اصلی برای زبان فارسی
- **پاسخ‌گو**: کامل‌اً قابل‌تطبیق برای دسکتاپ و موبایل
- **حالت روشن**: رنگ‌های روشن و شفاف

### 📝 مدیریت پرومپت‌ها
- **ایجاد/ویرایش/حذف**: مدیریت کامل پرومپت‌های AI
- **طبقه‌بندی**: سازمان‌دهی پرومپت‌ها بر اساس دسته‌بندی
- **تصاویر تولیدشده**: نمایش و مدیریت تصاویر AI
- **آمار بازدید**: ردیابی محبوبیت هر پرومپت

### 💰 مدیریت تبلیغات
- **موقعیت‌های متعدد**: بالا، کناری، میان‌صفحه، پایین
- **زمان‌بندی تبلیغات**: تاریخ شروع و پایان
- **آمار تبلیغات**: تعداد نمایش‌ها و کلیک‌ها
- **نرخ کلیک (CTR)**: محاسبۀ خودکار کارایی

### 🔐 پنل مدیریت
- **داشبورد مکمل**: دسترسی کامل به تمام عناصر
- **کنترل دسترسی**: سیستم احراز‌هویت ایمن
- **تجزیه‌وتحلیل**: گزارشات تفصیلی و آمار
- **واجهۀ ادمین Django**: تمام ابزارهای استاندارد Django

### 🔍 ویژگی‌های جستجو
- **جستجوی فوری**: بر اساس عنوان و توصیف
- **فیلتر بر اساس دسته**: دسترسی سریع به دسته‌بندی‌ها
- **نتایج یافت‌شده**: نمایش تعداد نتایج

## 🛠️ فناوری‌های استفاده‌شده

- **Django 4.2**: فریم‌ورک وب مقیاس‌پذیر
- **SQLite**: پایگاه‌داده‌ی سبک‌وزن (می‌تواند به PostgreSQL تغییر یابد)
- **Tailwind CSS**: طراحی Utility-First
- **Font Awesome**: نمادهای عالی
- **Chart.js**: نمودارهای تعاملی
- **Python 3.13**: نسخۀ جدید Python

## 📦 نصب

### الزامات
- Python 3.7+
- pip
- virtualenv (اختیاری اما توصیه‌شده)

### مراحل نصب

```bash
# کلون کردن یا بارگذاری پروژه
cd poogo

# ایجاد محیط مجازی
python -m venv .venv

# فعال‌کردن محیط مجازی
.venv\Scripts\activate  # در ویندوز
source .venv/bin/activate  # در مک/لینوکس

# نصب وابستگی‌ها
pip install Django==4.2.0 psycopg2-binary==2.9.6 Pillow==10.0.0 python-dotenv==1.0.0

# اعمال مایگریشن‌ها
python manage.py migrate

# ایجاد کاربر ادمین
python manage.py createsuperuser

# اضافه‌کردن داده‌های نمونه
python populate_data.py

# راه‌اندازی سرور
python manage.py runserver
```

## 🚀 استفاده

### راه‌اندازی سرور توسعه
```bash
python manage.py runserver
```

سرور بر روی `http://localhost:8000` اجرا می‌شود.

### دسترسی به پنل مدیریت
```
http://localhost:8000/admin
نام کاربری: admin
رمز: admin123
```

## 📁 ساختار پروژه

```
poogo/
├── poogo_config/          # تنظیمات Django
│   ├── settings.py       # تنظیمات پروژه
│   ├── urls.py          # مسیرهای URL
│   └── wsgi.py          # تنظیمات WSGI
├── prompts/              # تطبیق اصلی
│   ├── models.py        # مدل‌های پایگاه‌داده
│   ├── views.py         # منطق نمایش
│   ├── admin.py         # تنظیمات پنل مدیریت
│   ├── urls.py          # مسیرهای تطبیق
│   └── migrations/       # مایگریشن‌های دیتابیس
├── templates/           # فایل‌های HTML
│   ├── base.html       # قالب اصلی
│   └── prompts/        # قالب‌های سفارشی تطبیق
├── static/             # فایل‌های استاتیک (CSS, JS)
├── media/              # فایل‌های رسانه‌ای (تصاویر)
├── manage.py           # فایل‌های مدیریت Django
└── populate_data.py    # اسکریپت افزودن داده

```

## 🎯 مدل‌های پایگاه‌داده

### Category (دسته‌بندی)
```python
- name: نام دسته‌بندی
- description: توصیف
```

### Prompt (پرومپت)
```python
- title: عنوان
- description: متن کامل
- category: دسته‌بندی
- author: نویسنده
- views_count: تعداد بازدید
- is_featured: برجسته یا خیر
- created_at: تاریخ ایجاد
- updated_at: تاریخ بروزرسانی
```

### PromptImage (تصویر پرومپت)
```python
- prompt: ارجاع به پرومپت
- image: فایل تصویر
- image_url: آدرس تصویر
- is_approved: تایید‌شده یا خیر
- generated_at: تاریخ ایجاد
```

### Advertisement (تبلیغ)
```python
- title: عنوان تبلیغ
- content: محتوای توضیحی
- image: تصویر تبلیغ
- link: لینک مقصد
- position: موقعیت (top, sidebar, between, bottom)
- is_active: فعال یا خیر
- priority: اولویت نمایش
- start_date: تاریخ شروع
- end_date: تاریخ پایان
- impressions: تعداد نمایش
- clicks: تعداد کلیک
```

### ViewAnalytics (آمار بازدید)
```python
- prompt: ارجاع به پرومپت
- views: تعداد بازدیدها
- date: تاریخ
```

### AdClickAnalytics (آمار تبلیغات)
```python
- advertisement: ارجاع به تبلیغ
- clicks: تعداد کلیک‌ها
- impressions: تعداد نمایش‌ها
- date: تاریخ
```

## 🌐 مسیرهای URL

- `/` - صفحۀ اصلی
- `/prompt/<id>/` - جزئیات پرومپت
- `/category/<id>/` - پرومپت‌های یک دسته
- `/search/` - جستجو
- `/admin/` - پنل مدیریت
- `/track/impression/<ad_id>/` - ردیابی نمایش تبلیغ
- `/track/click/<ad_id>/` - ردیابی کلیک تبلیغ

## 📊 ویژگی‌های پیشرفتۀ پنل مدیریت

### مدیریت پرومپت‌ها
- افزودن/ویرایش/حذف پرومپت‌ها
- مدیریت تصاویر درون‌صفحه
- مشاهدۀ آمار 7 روز اخیر

### مدیریت تبلیغات
- تعیین موقعیت و اولویت
- مدیریت تاریخ شروع و پایان
- مشاهدۀ نمایش‌ها، کلیک‌ها، و CTR

### آمار و تجزیه‌وتحلیل
- آمار بازدیدهای روزانه
- آمار کلیک‌های تبلیغات
- افزودن خودکار شامل محافظت

## 🔄 دستورات مفید

```bash
# ایجاد مایگریشن جدید
python manage.py makemigrations

# اعمال مایگریشن‌ها
python manage.py migrate

# ایجاد کاربر ادمین
python manage.py createsuperuser

# جمع‌آوری فایل‌های استاتیک
python manage.py collectstatic

# نمایش SQL درخواست
python manage.py sqlmigrate prompts 0001
```

## 🎨 سفارشی‌سازی

### تغییر رنگ‌ها
رنگ‌ها در `templates/base.html` و `poogo_config/settings.py` تعریف شده‌اند:

```css
:root {
    --primary-color: #6366f1;      /* نیلی */
    --secondary-color: #8b5cf6;    /* بنفش */
    --accent-color: #ec4899;       /* صورتی */
}
```

### افزودن دسته‌بندی جدید
از طریق پنل مدیریت `/admin/` یک دسته جدید اضافه کنید یا از طریق Django Shell:

```python
python manage.py shell
from prompts.models import Category
Category.objects.create(name="دسته‌بندی جدید", description="توضیح")
```

## 🔒 امنیت

- **CSRF Protection**: فعال‌شده‌است برای تمام فرم‌ها
- **SQL Injection Prevention**: استفاده از ORM Django
- **XSS Protection**: استفاده از Template auto-escaping
- **Session Management**: مدیریت ایمن سشن‌ها

## 📝 لایسنس

این پروژه برای استفادۀ تجاری و شخصی آزاد است.

## 👥 نویسندگان

توسعه‌یافته توسط **GitHub Copilot** برای **Poogo**

## 📞 پشتیبانی

برای مشکلات و سوالات:
- ایمیل: support@poogo.com
- تلگرام: @poogo_support

## 🚀 نسخۀ آینده

- [ ] ادغام OpenAI API برای تولید پرومپت خودکار
- [ ] ثبت‌نام و حساب کاربری
- [ ] صفحات یا قلم‌های مورد علاقه
- [ ] نظرات و رتبه‌بندی
- [ ] صادرات PDF/CSV
- [ ] سیستم اعلان‌ها
- [ ] تاریک حالت (Dark Mode)
- [ ] API RESTful کامل

---

**نسخه: 1.0.0**  
**تاریخ: 2026**
#   g h  
 
# Data-Mining-OnlineShope

# 🛒 Online Retail Customer Churn Prediction
### From Raw Transactions to Customer Retention Intelligence

<p align="center">
  <img src="https://img.shields.io/badge/PROJECT-Data%20Mining-306998?style=for-the-badge&logo=databricks&logoColor=white" />
  <img src="https://img.shields.io/badge/PYTHON-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/WORKFLOW-CRISP--DM-7C3AED?style=for-the-badge" />
  <img src="https://img.shields.io/badge/STATUS-In%20Progress-F59E0B?style=for-the-badge" />
</p>

<p align="center">
  <b>Turning customer transaction data into actionable insights for predicting churn and improving customer retention.</b>
</p>

---

### تحلیل رفتار مشتریان، کشف الگوهای خرید و شناسایی مشتریان در معرض ریزش

<div dir="rtl">

## 📌 معرفی پروژه

در این پروژه، رفتار مشتریان یک فروشگاه آنلاین بین‌المللی با استفاده از تکنیک‌های داده‌کاوی بررسی می‌شود. هدف اصلی، کشف الگوهای رفتاری مشتریان و تقسیم آن‌ها به گروه‌هایی با ویژگی‌های مشابه است تا بتوان برای هر گروه راهبرد مناسب‌تری طراحی کرد.

در کنار خوشه‌بندی، از مدل‌های پیش‌بینی نیز برای شناسایی مشتریانی که احتمال دارد در آینده خرید خود را متوقف کنند استفاده می‌شود.

**تمرکز اصلی پروژه بر Clustering است و Classification به‌عنوان روشی مکمل به کار می‌رود.**

## 🎯 اهداف پروژه

- شناسایی الگوهای پنهان در رفتار خرید مشتریان
- گروه‌بندی مشتریان بر اساس ویژگی‌های رفتاری و ارزش خرید
- شناسایی مشتریان در معرض ریزش
- بررسی عوامل مرتبط با کاهش فعالیت مشتریان
- پیشنهاد راهبردهای مناسب برای هر گروه رفتاری
- اولویت‌بندی مشتریان برای اجرای کمپین حفظ مشتری
- بررسی ارزش اقتصادی و اثربخشی احتمالی اقدامات پیشنهادی

## 🧠 روش‌های داده‌کاوی

### ۱. Clustering — روش اصلی

از خوشه‌بندی برای شناسایی گروه‌های رفتاری مشابه استفاده می‌کنیم. در این روش، از قبل برچسب مشخصی برای مشتریان نداریم و الگوریتم بر اساس شباهت ویژگی‌ها، آن‌ها را در گروه‌های مختلف قرار می‌دهد.

الگوریتم اصلی این بخش:

- **K-Means**

برای انتخاب تعداد مناسب خوشه‌ها از روش‌هایی مانند Elbow و Silhouette استفاده می‌شود.

هدف این بخش، شناخت انواع رفتار مشتریان و کمک به طراحی راهبرد مناسب برای هر گروه است.

### ۲. Classification — روش مکمل

خوشه‌بندی به‌تنهایی نمی‌تواند مشخص کند کدام مشتری در آینده خرید خود را متوقف خواهد کرد. به همین دلیل، از Classification برای برآورد ریسک ریزش مشتریان نیز استفاده می‌کنیم.

در این بخش، برچسب ریزش با بررسی رفتار خرید مشتری در ۹۰ روز آینده ساخته می‌شود.

الگوریتم‌های مورد بررسی:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting

**نکته:** خوشه‌های رفتاری لزوماً معادل گروه مشتریان ریزشی و غیرریزش‌یافته نیستند. این دو روش دو دیدگاه مکمل از رفتار مشتری ارائه می‌دهند.

## 📊 دیتاست

داده‌های پروژه از دیتاست **Online Retail** تهیه شده‌اند که شامل تراکنش‌های یک فروشگاه آنلاین مستقر در بریتانیا است.

اطلاعات اصلی دیتاست:

| ستون | توضیحات |
|---|---|
| InvoiceNo | شماره فاکتور |
| StockCode | شناسه محصول |
| Description | توضیحات محصول |
| Quantity | تعداد کالا |
| InvoiceDate | تاریخ ثبت تراکنش |
| UnitPrice | قیمت واحد |
| CustomerID | شناسه مشتری |
| Country | کشور مشتری |

**منبع دیتاست:** UCI Machine Learning Repository

[دریافت دیتاست Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)

## 🔄 مسیر اجرای پروژه (CRISP-DM)

پروژه بر اساس چارچوب CRISP-DM پیش می‌رود.

| فاز | فعالیت‌ها |
|---|---|
| **Business Understanding** | تعریف مسئله کسب‌وکار، تعیین اهداف، شناسایی ذی‌نفعان، KPIها، محدودیت‌ها و برنامه پروژه |
| **Data Understanding** | بررسی ساختار دیتاست، شناخت ویژگی‌ها، تحلیل توزیع‌ها و شناسایی مشکلات داده |
| **Data Preparation** | انتخاب ویژگی‌ها، پاک‌سازی و ممیزی داده، ساخت ویژگی‌های رفتاری، ایجاد برچسب ریزش و آماده‌سازی دیتاست |
| **Modeling** | اجرای الگوریتم‌های خوشه‌بندی و طبقه‌بندی، تنظیم مدل‌ها و مقایسه نتایج |

## 🧩 ویژگی‌های رفتاری (Feature Engineering)

برای تبدیل داده‌های خام تراکنشی به اطلاعات قابل‌استفاده در تحلیل رفتار مشتریان، ویژگی‌های مختلفی ساخته می‌شوند.

| ویژگی | مفهوم |
|---|---|
| Recency | فاصله زمانی از آخرین خرید مشتری |
| Frequency | تعداد خریدهای مشتری |
| Monetary | مجموع ارزش خرید مشتری |
| Average Order Value | میانگین ارزش هر سفارش |
| Unique Products | تعداد محصولات منحصربه‌فرد خریداری‌شده |
| Active Days | تعداد روزهایی که مشتری خرید داشته است |
| Active Months | تعداد ماه‌های دارای خرید |
| Purchase Interval | میانگین فاصله زمانی بین خریدها |
| Tenure | مدت‌زمان سابقه مشتری |
| Frequency Change | تغییر تعداد خرید در بازه‌های زمانی |
| Spend Change | تغییر میزان هزینه‌کرد مشتری |
| Cancel Rate | نرخ فاکتورهای لغو یا مرجوعی |

این ویژگی‌ها به ما کمک می‌کنند مشتریان را از نظر ارزش خرید، نظم خرید، تنوع محصولات و تغییر رفتار بررسی کنیم.

## ⚙️ فناوری‌ها و ابزارهای مورد استفاده

| ابزار | کاربرد |
|---|---|
| Python | زبان اصلی برنامه‌نویسی |
| NumPy | محاسبات عددی و عملیات آرایه‌ای |
| Pandas | پردازش و تحلیل داده‌ها |
| Matplotlib | رسم نمودارها |
| Seaborn | مصورسازی و تحلیل توزیع‌ها |
| Scikit-learn | پیاده‌سازی و ارزیابی الگوریتم‌های یادگیری ماشین |
| Jupyter Notebook | محیط توسعه و مستندسازی |
| Git & GitHub | مدیریت نسخه و نگهداری پروژه |

## 📈 ارزیابی مدل‌ها

### ارزیابی Clustering

برای بررسی کیفیت خوشه‌بندی از معیارهای زیر استفاده می‌شود:

- **Silhouette Score:** بررسی میزان تفکیک و انسجام خوشه‌ها
- **Davies-Bouldin Index:** بررسی شباهت و پراکندگی خوشه‌ها
- **Calinski-Harabasz Index:** بررسی نسبت پراکندگی بین خوشه‌ها به پراکندگی درون آن‌ها
- **Behavioral Interpretation:** بررسی معنا و ارزش تجاری هر خوشه

### ارزیابی Classification

برای بررسی عملکرد مدل‌های پیش‌بینی از معیارهای زیر استفاده می‌شود:

- Precision
- Recall
- F1-score
- PR-AUC
- ROC-AUC
- Confusion Matrix
- Precision@500

با توجه به محدودیت ظرفیت کمپین، شناسایی مشتریان پرریسک در میان ۵۰۰ مشتری اول اهمیت ویژه‌ای دارد.

## 💼 خروجی مورد انتظار پروژه

در نهایت، هدف این است که با ترکیب نتایج خوشه‌بندی و پیش‌بینی ریسک، اطلاعات قابل‌استفاده‌ای برای تصمیم‌گیری کسب‌وکار فراهم شود.

خروجی‌های مورد انتظار:

1. گروه‌های رفتاری مشتریان همراه با تفسیر ویژگی‌های هر گروه
2. شناسایی مشتریان در معرض ریزش
3. رتبه‌بندی مشتریان بر اساس ریسک
4. پیشنهاد اقدام مناسب برای هر گروه رفتاری
5. فهرست ۵۰۰ مشتری اولویت‌دار برای کمپین حفظ مشتری
6. تحلیل اقتصادی کمپین و بررسی فرضیات مالی

## ⚠️ ملاحظات و محدودیت‌ها

- دیتاست فاقد برچسب آماده برای ریزش مشتری است؛ بنابراین برچسب باید با استفاده از رفتار خرید آینده ساخته شود.
- تراکنش‌های لغوشده، مرجوعی‌ها و مقادیر منفی باید پیش از محاسبه رفتار مشتری بررسی شوند.
- اطلاعات ناقص مشتریان می‌تواند بر تحلیل مشتری‌محور اثر بگذارد.
- ویژگی‌های مدل باید فقط از اطلاعات موجود پیش از تاریخ مرجع ساخته شوند تا از Data Leakage جلوگیری شود.
- ارزیابی مدل باید با توجه به ترتیب زمانی داده‌ها انجام شود.
- شناسایی ارتباط بین یک ویژگی و ریزش، به‌تنهایی به معنی اثبات رابطه علت و معلولی نیست.
- اثربخشی واقعی کمپین حفظ مشتری نیازمند اجرای آزمایش‌هایی مانند A/B Testing است.

</div>


## 🚀 Project Roadmap

- [x] Business Understanding
- [x] Data Understanding
- [x] Data Preparation
  - [x] Data Selection
  - [x] Data Cleaning
  - [x] Data Construction
  - [x] Data Integration
  - [x] Data Formatting
  - [x] Data Reduction
  - [x] Data Transformation
  - [x] Dataset Validation
- [x] Modeling
  - [x] Customer Behavioral Clustering
  - [x] Optimal Number of Clusters
  - [x] Cluster Interpretation
  - [x] Churn Classification
  - [x] Model Comparison
  - [x] Temporal Evaluation
  - [x] Customer Prioritization
  - [x] Campaign Analysis

## 📚 References

- [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online+retail)
- [CRISP-DM Methodology](https://www.ibm.com/docs/en/spss-modeler)
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [NumPy Documentation](https://numpy.org/doc/)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)

---

<div align="center">

**Developed as a Data Mining Project**

</div>
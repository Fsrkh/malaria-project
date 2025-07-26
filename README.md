
<div dir="rtl">

# 🧠 پروژه تشخیص مالاریا با شبکه‌های عصبی

**شرح پروژه**  
در این پروژه با استفاده از تصاویر سلولی از دیتاست مالاریا (Kaggle) و مدل CNN (با VGG16)، سلول‌های مبتلا به انگل مالاریا را شناسایی کردیم. مراحل اصلی شامل پیش‌پردازش، آموزش، ارزیابی و تولید گزارش جامع بوده است.

---

## 📌 ساختار پروژه

```
.
├── data/
│   └── cell_images/
│       ├── Parasitized/
│       └── Uninfected/
├── notebooks/
│   ├── training.ipynb
│   └── evaluation.ipynb
├── models/
│   └── best_model.keras
├── reports/
│   ├── confusion_matrix.png
│   ├── roc_curve.png
│   ├── pr_curve.png
│   └── metrics_report.txt
└── README.md
```

---

## 🚀 مراحل اجرای پروژه

### ۱. پیش‌پردازش (Preprocessing)
– بارگذاری تصاویر  
– نرمال‌سازی (`rescale=1./255`)  
– تقسیم داده به **Train / Validation** با نسبت ۸۰/۲۰  

### ۲. آموزش مدل
```python
from tensorflow.keras.applications import VGG16
# مدل پایه با weights=None
base = VGG16(weights=None, include_top=False, input_shape=(128,128,3))
# افزودن لایه‌های Dense و Dropout، تنظیم learning_rate
```

### ۳. ارزیابی نتایج
– محاسبه accuracy و loss  
– رسم confusion matrix، نمودار ROC و Precision–Recall  
– محاسبه دقیق Precision، Recall، F1 و MCC

### ۴. گزارش نهایی
– ذخیره تصاویر و نمودارها در پوشه reports/  
– تولید فایل متنی تحلیل با اعداد دقیق برای فصل نتایج پایان‌نامه  

## 📊 نمودارها و گزارش‌ها

| فایل | شرح |
|------|------|
| `confusion_matrix.png` | ماتریس سردرگمی با شمارش و درصد |
| `roc_curve.png` | نمودار ROC همراه با AUC |
| `pr_curve.png` | Precision‑Recall با Average Precision |
| `metrics_report.txt` | گزارش کامل عددی (دقت، F1، MCC) |

## 🧾 نمونه کد تولید گزارش عددی
```python
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, classification_report, matthews_corrcoef

acc = accuracy_score(y_true, y_pred)
prec = precision_score(y_true, y_pred)
rec = recall_score(y_true, y_pred)
f1 = f1_score(y_true, y_pred)
mcc = matthews_corrcoef(y_true, y_pred)

print(f"Accuracy: {acc:.4f}")
print(f"Precision: {prec:.4f}")
print(f"Recall: {rec:.4f}")
print(f"F1 Score: {f1:.4f}")
print(f"MCC: {mcc:.4f}\n")
print(classification_report(y_true, y_pred, target_names=labels))
```

## ✍️ نحوه استفاده از پروژه
- کل دیتاست را در مسیر `data/cell_images` قرار دهید.
- در `notebooks/training.ipynb` کد آموزش مدل را اجرا کنید.
- پس از ذخیره مدل، `evaluation.ipynb` را برای تولید نمودارها و گزارش اجرا کنید.
- خروجی‌ها در پوشه `reports/` ذخیره می‌شوند.
- فایل `metrics_report.txt` را می‌توانید در فصل نتایج پایان‌نامه کپی و تحلیل کنید.

## 📚 منابع و مراجع
- استفاده از VGG16 به‌صورت از-scratch
- معیارهای ارزیابی متداول در تشخیص بیماری (ROC AUC، F1، MCC)

## 🎯 نتیجه‌گیری
این پروژه با ارائه گزارش‌های تصویری و عددی کامل، مناسب برای قرار دادن در GitHub به‌عنوان نمونه کار و همچنین استفاده در فصل نتایج پایان‌نامه است.

هرگونه سوال یا اصلاح لازم بود بفرمایید، با عشق انجام می‌دم ❤️

</div>

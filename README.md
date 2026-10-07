# Churn bashorati va mijozlar segmentatsiyasi

Ikki mustaqil mashinaviy o'qitish loyihasi, ikkalasi ham Jupyter notebook ko'rinishida:

| # | Loyiha | Usul | Notebook |
|---|---|---|---|
| 1 | Bank mijozlarining ketishini (churn) bashorat qilish | Supervised learning, klassifikatsiya | [`01_bank_customer_churn.ipynb`](notebooks/01_bank_customer_churn.ipynb) |
| 2 | Ulgurji mijozlarni xarajat turlariga qarab segmentlash | Unsupervised learning, klasterlash | [`02_wholesale_customer_segmentation.ipynb`](notebooks/02_wholesale_customer_segmentation.ipynb) |

## 1. Bank mijozlari churn bashorati

Bank mijozlarining qaysilari xizmatdan voz kechishini oldindan aniqlaymiz, shunda ularni ushlab qolish choralarini o'z vaqtida ko'rish mumkin.

- **Dataset:** Kaggle, *Churn Modelling* (10 000 mijoz, target: `Exited`).
- **Ma'lumotni tayyorlash:** bo'sh qiymat va dublikatlarni tekshirish, keraksiz identifikator ustunlarni olib tashlash, `Geography` va `Gender` ni one-hot encoding qilish, `StandardScaler`.
- **Modellar:** Logistic Regression, SVM, Decision Tree, Random Forest, XGBoost.
- **Baholash:** Accuracy, Precision, Recall, F1-score, confusion matrix, belgilar muhimligi.
- **Eslatma:** klasslar nomutanosib bo'lgani uchun asosiy e'tibor Recall va F1 ga qaratiladi.

## 2. Ulgurji mijozlarni segmentlash

Mijozlarni ular sarflaydigan mahsulot turlariga qarab guruhlarga ajratamiz va har bir guruh uchun marketing tavsiyalari beramiz.

- **Dataset:** UCI, [Wholesale customers](https://archive.ics.uci.edu/ml/datasets/wholesale+customers) (440 mijoz).
- **Ma'lumotni tayyorlash:** `Channel` va `Region` klasterlashga kiritilmaydi, xarajatlar `log1p` va `StandardScaler` bilan normallashtiriladi (xarajat taqsimoti kuchli assimetrik bo'lgani uchun).
- **Klasterlash:** K-means, k ni Elbow va Silhouette orqali tanlaymiz.
- **Vizualizatsiya:** PCA scatter plot, pairplot, segmentlar bo'yicha o'rtacha xarajatlar diagrammasi, nisbiy profil heatmap'i, segmentlarning kanal va hudud bilan bog'liqligi.

## Loyiha tuzilishi

```
churn-va-segmentatsiya/
├── notebooks/
│   ├── 01_bank_customer_churn.ipynb
│   └── 02_wholesale_customer_segmentation.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

## Ishga tushirish

**Google Colab.** Notebook'ni Colab'da oching (File → Upload notebook yoki GitHub orqali). Kerakli kutubxonalar Colab'da o'rnatilgan, shuning uchun Runtime → Run all bosish yetarli.

**Lokal kompyuterda:**

```bash
git clone <repo-manzili>
cd churn-va-segmentatsiya

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt

jupyter notebook notebooks/
```

Datasetlar notebook ichida to'g'ridan-to'g'ri URL orqali yuklanadi, ularni alohida yuklab olish shart emas (internet kerak).

## Texnologiyalar

Python, pandas, NumPy, scikit-learn, XGBoost, matplotlib, seaborn.

## Natijalar

Metrikalar jadvali, grafiklar va segmentlar tavsifi har bir notebook'ning tegishli bo'limlarida chiqadi.

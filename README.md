# 🎓 Öğrenci Performansı Analizi & Tahmin Modeli

Bu proje, öğrenci üretkenlik verilerini kullanarak **sınav notunu (exam_score)** tahmin eden bir makine öğrenmesi regresyon pipeline'ı içermektedir.

---

## 📊 Veri Seti

| Özellik | Detay |
|---------|-------|
| **Kaynak** | Ultimate Student Productivity Dataset (Kaggle) |
| **Kayıt Sayısı** | 5.000 |
| **Hedef Değişken** | `exam_score` (sürekli — regresyon) |

---

## 🗂️ Notebook Yapısı

| Bölüm | Açıklama |
|-------|----------|
| **1. Kütüphane Yükleme** | NumPy, Pandas, Matplotlib, Seaborn, Scikit-learn, XGBoost |
| **2. Veri Yükleme** | CSV dosyasının okunması ve boyut kontrolü |
| **3. Keşifçi Veri Analizi (EDA)** | Hedef değişken dağılımı, nümerik/kategorik görselleştirmeler, korelasyon analizi |
| **4. Ön İşleme** | Eksik değer kontrolü, encoding, ölçeklendirme (RobustScaler), log1p dönüşümü |
| **5. Model Eğitimi** | 7 farklı model karşılaştırması (bkz. aşağıda) |
| **6. Model Değerlendirme** | RMSE, MAE, R² metrikleri; Feature Importance |
| **7. Çapraz Doğrulama** | 5-Fold KFold CV ile kararlılık testi |
| **8. Hiperparametre Optimizasyonu** | RandomizedSearchCV → GridSearchCV ile XGBoost fine-tuning |
| **9. Özet & Sonuç** | Baseline vs. Fine-Tuned model karşılaştırması |

---

## 🤖 Kullanılan Modeller

- Linear Regression
- Ridge Regression
- Lasso Regression
- Decision Tree Regressor
- K-Nearest Neighbors (KNN)
- Random Forest Regressor
- Gradient Boosting Regressor
- **XGBoost Regressor** *(en iyi performans)*

---

## ⚙️ Hiperparametre Optimizasyonu (XGBoost)

İki aşamalı optimizasyon stratejisi uygulanmıştır:

1. **RandomizedSearchCV** — 60 iterasyon, 5-fold CV ile geniş parametre uzayı taranmıştır.
2. **GridSearchCV** — RandomizedSearchCV sonuçları merkez alınarak daraltılmış ızgarada hassas arama yapılmıştır.

Aranan parametreler: `n_estimators`, `max_depth`, `learning_rate`, `subsample`, `colsample_bytree`, `min_child_weight`, `gamma`, `reg_alpha`, `reg_lambda`

---

## 📈 Sonuç

Fine-Tuned XGBoost modeli, baseline XGBoost'a kıyasla daha düşük RMSE/MAE ve daha yüksek R² skoru elde etmiştir. Model production kullanımına hazır olarak değerlendirilmektedir.

---

## 🛠️ Gereksinimler

```bash
pip install numpy pandas matplotlib seaborn scikit-learn xgboost
```

---

## 🚀 Kullanım

```bash
# Kaggle ortamında çalıştırmak için
# Notebook'u Kaggle'a yükleyin ve aşağıdaki veri setini ekleyin:
# amar5693/student-performance-dataset
```

> **Not:** Notebook Kaggle ortamı için tasarlanmıştır. Yerel ortamda çalıştırmak için `DATA_PATH` değişkenini güncellemeniz gerekmektedir.

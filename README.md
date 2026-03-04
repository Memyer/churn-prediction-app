# 🛒 Customer Churn Prediction – E-Commerce India

Aplikasi Streamlit untuk memprediksi churn pelanggan e-commerce India menggunakan **LightGBM** dengan optimasi threshold.

## 🔗 Live App
**[→ Buka Aplikasi Streamlit](https://your-app-link.streamlit.app)**  
*(Update link ini setelah deploy ke Streamlit Cloud)*

---

## 📋 Tentang Project

| Item | Detail |
|------|--------|
| Dataset | E-Commerce Customer Churn (India) – 5.630 pelanggan |
| Model | LightGBM + Threshold Optimization (OOF CV) |
| Recall | **97%** (hanya 6 dari 190 churn yang terlewat) |
| PR-AUC | **0.9983** |
| ROC-AUC | **0.9996** |
| Penghematan | **78%** biaya vs skenario tanpa intervensi |

---

## 🗂️ Struktur Aplikasi

```
streamlit/
├── app.py                    ← Streamlit multi-page app (5 halaman)
├── train_model.py            ← Script training & export model.pkl
├── model.pkl                 ← Saved LightGBM pipeline + metadata
├── E_Commerce_Dataset1.xlsx  ← Dataset
├── requirements.txt          ← Dependencies
└── README.md                 ← Dokumentasi ini
```

---

## 📄 Halaman Aplikasi

| # | Halaman | Deskripsi |
|---|---------|-----------|
| 1 | 🏠 **Home & Overview** | Business problem, siapa pengguna, skenario penggunaan, panduan navigasi |
| 2 | 📊 **EDA & Insights** | Distribusi churn, analisis fitur numerik & kategorik, korelasi |
| 3 | 🤖 **Model Performance** | Perbandingan 6 model, confusion matrix, PR/ROC curve, feature importance |
| 4 | 🎯 **Predict Churn** | Form input data pelanggan → prediksi real-time + rekomendasi aksi |
| 5 | 💰 **Business Impact** | Cost-benefit simulation 3 skenario dengan parameter interaktif |

---

## 👥 Target Pengguna & Skenario

| Pengguna | Skenario Utama | Keputusan yang Dibantu |
|----------|---------------|----------------------|
| Tim Marketing | Campaign retensi bulanan | Segmentasi low/medium/high-risk |
| Tim CRM | Monitoring mingguan | Intervensi proaktif sebelum pelanggan pergi |
| Customer Service | Pasca komplain | Prioritas penanganan at-risk customers |
| Management | Perencanaan strategis | Insight faktor utama churn & ROI retensi |

---

## 🚀 Cara Menjalankan Lokal

```bash
# 1. Clone repo / masuk ke folder
cd streamlit

# 2. Buat virtual environment
python -m venv .venv
.venv\Scripts\activate          # Windows
# source .venv/bin/activate     # Linux/Mac

# 3. Install dependencies
pip install -r requirements.txt

# 4. Train model (sekali saja)
python train_model.py

# 5. Jalankan Streamlit
streamlit run app.py
```

Buka browser: **http://localhost:8501**

---

## 📊 Hasil Model

```
=== Final Model: LightGBM (threshold=0.270) ===
              precision    recall  f1-score   support

   Not Churn       0.99      1.00      1.00       936
       Churn       0.98      0.97      0.98       190

    accuracy                           0.99      1126

Confusion Matrix: TP=184  FP=3  FN=6  TN=933
PR-AUC  : 0.9983
ROC-AUC : 0.9996
```

### Cost-Benefit Simulation (₹CAC=1500, ₹CRC=300):
| Skenario | Biaya |
|----------|-------|
| No Action (semua churn hilang) | ₹285,000 |
| Retensi Massal (semua pelanggan) | ₹622,800 |
| **Model Targeted** | **₹63,900** |
| **Penghematan vs No Action** | **₹221,100 (77.6%)** |

---

## 🔑 Key Findings

1. **Tenure** adalah faktor dominan — pelanggan baru (<4 bulan) 3.4× lebih rentan churn
2. **Complain** — satu komplain sudah menaikkan risiko churn 3× lipat (31.7% vs 10.9%)
3. **CashbackAmount** — pelanggan yang dapat cashback lebih tinggi lebih loyal
4. **Segmen tertinggi**: Single + COD + Mobile Phone + City Tier 3

---

## 🛠️ Tech Stack

- **Python 3.10+** | **Streamlit 1.55** | **LightGBM 4.x**
- **scikit-learn** | **plotly** | **pandas** | **shap**

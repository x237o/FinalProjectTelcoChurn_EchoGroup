Analisis dan Prediksi Customer Churn (Telco)

Proyek ini bertujuan untuk mengidentifikasi, memodelkan, dan memprediksi pelanggan berisiko tinggi (churn) pada perusahaan telekomunikasi (Telco) dengan fokus pada *pelanggan layanan internet. Tujuan utamanya adalah meminimalkan kerugian finansial akibat *churn melalui identifikasi dini pelanggan yang akan pergi (True Positive) dan meminimalkan pelanggan yang luput (False Negative).

---

## 🚀 Metodologi & Model Terbaik

Analisis ini menggunakan data Telco_customer_churn.xlsx - Telco_Churn.csv.

### Pra-Pemrosesan Data Kunci

1.  *Filtering Data:* Semua pelanggan yang tidak memiliki layanan internet (Internet Service = 'No') dihapus untuk meningkatkan fokus model pada fitur-fitur yang menjadi pendorong churn terbesar.
2.  *Encoding & Scaling:* Fitur kategorikal di-encode (One-Hot Encoding) untuk model berbasis jarak (KNN, Regresi Logistik).

### Perbandingan Model

Berbagai model klasifikasi diuji, dengan fokus pada metrik *Recall* (meminimalkan kerugian/FN) dan *Precision* (memaksimalkan efisiensi biaya/FP).

                 Model   ROC AUC  Precision    Recall  F1 Score
1  LightGBM             0.870180  0.703422   0.570988  0.630324
2  Logistic Regression  0.867759  0.706564   0.564815  0.627787
3  XGBoost              0.853724  0.661597   0.537037  0.592845
4  Random Forest        0.844646  0.692982   0.487654  0.572464
5  KNN                  0.808623  0.607143   0.524691  0.562914
6  Decision Tree        0.682165  0.529412   0.527778  0.528594

### Kesimpulan Pemodelan

*Model LightGBM* dipilih sebagai model produksi terbaik. Dengan presisi yang tinggi, model ini dapat di deploy untuk mengurangi Churn pada pelanggan Telco

---

## 🎯 Insight Bisnis Utama

Analisis mendalam terhadap Churn Reason mengungkapkan bahwa masalah churn terbesar terbagi menjadi dua bidang:

### 1. Krisis Sikap Pelayanan (The Trigger)

Alasan churn tunggal yang paling sering disebutkan adalah *"Attitude of service provider" (Sikap penyedia layanan)*.

* *Insight:* Meskipun persaingan adalah faktor utama, sikap buruk dari agen layanan pelanggan bertindak sebagai *pemicu emosional* yang mempercepat keputusan pelanggan untuk beralih.
* *Aksi:* Investasi segera harus dialokasikan untuk pelatihan agen, peningkatan metrik *CSAT* (Customer Satisfaction), dan mengikat KPI agen dengan kualitas interaksi, bukan hanya kecepatan panggilan.

### 2. Dominasi Persaingan (The Root Cause)

Secara agregat, alasan yang berkaitan dengan kompetisi (harga, kecepatan, perangkat) menyumbang *sekitar 67%* dari semua kasus churn.

* *Insight:* Perusahaan menghadapi tekanan harga dan kualitas produk yang ekstrim.
* *Aksi:* Model *LightGBM* harus digunakan untuk mengidentifikasi *832pelanggan True Positive (TP)* secara proaktif. Pelanggan ini harus segera dihubungi dengan penawaran retensi yang kompetitif (diskon atau upgrade layanan) sebelum mereka beralih.

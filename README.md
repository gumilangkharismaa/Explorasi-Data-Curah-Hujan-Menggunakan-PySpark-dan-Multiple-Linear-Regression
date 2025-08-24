# Explorasi Data Curah Hujan Menggunakan PySpark dan Multiple Linear Regression

## Deskripsi Proyek
Proyek ini bertujuan untuk membangun model regresi linear berganda (Multiple Linear Regression) untuk menganalisis curah hujan berdasarkan berbagai fitur numerik. Data yang digunakan mencakup curah hujan harian (`rfh`), rata-rata curah hujan sebelumnya (`rfh_avg`, `r1h_avg`, `r3h_avg`), serta beberapa kuantitas curah hujan lainnya (`rfq`, `r1q`, `r3q`).  

Model dibuat menggunakan Apache PySpark agar dapat menangani dataset besar dan memanfaatkan kemampuan distributed computing.

> ⚠️ Catatan: Model ini dibuat untuk analisis historis dan pemodelan hubungan antar fitur.
---

## Dataset
Contoh data:

| date       | adm2_id | n_pixels | rfh      | rfh_avg | r1h     | r1h_avg | r3h     | r3h_avg | rfq     | r1q     | r3q     |
|------------|---------|----------|----------|---------|---------|---------|---------|---------|---------|---------|---------|
| 1981-01-01 | 1006955 | 15       | 45.9333  | 68.2756 | 217.26  | 216.26  | 651.32  | 648.21  | 69.51   | 100.99  | 100.85  |
| 1981-04-21 | 1006955 | 15       | 97.4667  | 95.0578 | 317.73  | 267.75  | 654.87  | 683.35  | 102.41  | 117.99  | 95.89   |
| 2024-04-21 | 1006696 | 82       | 110.6463 | 88.4516 | 309.73  | 246.53  | 795.13  | 667.50  | 123.75  | 124.64  | 118.83  |

Fitur utama yang digunakan dalam model:
- `n_pixels`
- `rfh_avg`
- `r1h_avg`
- `r3h_avg`
- `rfq`
- `r1q`
- `r3q`

Target (label) yang diprediksi:
- `rfh` (curah hujan)

---

## Metode
1. **Persiapan Data**
   - Menggabungkan fitur numerik ke dalam kolom vektor.
   - Membagi data menjadi train (80%) dan test (20%).

2. **Modeling**
   - Menggunakan Multiple Linear Regression dari PySpark MLlib.
   - Melatih model pada data train.
   - Mengevaluasi model menggunakan RMSE, MAE, dan R-squared.

3. **Evaluasi**
   - Root Mean Squared Error (RMSE) = 18.9985  
   - Mean Absolute Error (MAE) = 11.6789  
   - R-squared (R²) = 0.8716  

---

## Hasil Koefisien Model

| Fitur       | Koefisien            |
|------------|---------------------|
| n_pixels   | 0.000498            |
| rfh_avg    | 0.995974            |
| r1h_avg    | -0.000318           |
| r3h_avg    | 0.001265            |
| rfq        | 0.652802            |
| r1q        | -0.070999           |
| r3q        | -0.004205           |

- Intercept: -58.5942

---

## Kesimpulan
- Model regresi linear berganda menunjukkan fit yang cukup baik terhadap data historis (R² = 0.87), sehingga mampu menangkap hubungan antara fitur dan curah hujan.
- Model saat ini tidak digunakan untuk prediksi masa depan, tetapi dapat menjadi dasar untuk eksperimen prediksi jika data input baru tersedia.

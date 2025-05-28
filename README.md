# Mental Illness Prevalence Prediction

Proyek ini merupakan implementasi machine learning untuk memprediksi prevalensi penyakit mental **Schizophrenia** berdasarkan prevalensi gangguan mental lain dari berbagai negara.

---

##  Ringkasan Proyek

* **Tipe model**: Regresi
* **Target prediksi**: Prevalensi Schizophrenia
* **Metode utama**: Linear Regression
* **Dataset**: Kombinasi dataset prevalensi gangguan mental global
* **Tools**: Python, Pandas, Scikit-learn, Matplotlib, Seaborn, Plotly

---

##  Latar Belakang Masalah

Penyakit mental menjadi isu kesehatan global. Sayangnya, data untuk beberapa penyakit seperti schizophrenia tidak selalu tersedia di seluruh negara. Padahal, untuk pengambilan kebijakan, data seperti ini sangat dibutuhkan. Oleh karena itu, dibutuhkan model prediksi berbasis data gangguan mental lain seperti depresi mayor, gangguan bipolar, dsb.

---

##  Tujuan Proyek

Memprediksi prevalensi schizophrenia berdasarkan fitur gangguan mental lain agar negara-negara yang tidak memiliki data lengkap tetap dapat melakukan estimasi dengan akurat.

---

##  Dataset

Beberapa file yang digunakan:

* `mental-illnesses-prevalence.csv`
* `adult-population-covered-in-primary-data.csv`
* `depressive-symptoms-across-us-population.csv`
* `number-of-countries-with-primary-data.csv`

**Karakteristik Dataset:**

* Jumlah sampel: > 500
* Tipe data: Kuantitatif
* Fitur:

  * Entity (negara)
  * Major depression
  * Bipolar disorder
  * Dysthymia
  * Eating disorders
  * Anxiety disorders
  * Schizophrenia (target)

---

##  Visualisasi dan Cuplikan Tabel

###  Cuplikan Dataset Awal

```text
| Entity      | Code | Year | Schizophrenia | Depression | Anxiety | Bipolar | Eating |
|-------------|------|------|---------------|------------|---------|---------|--------|
| Afghanistan | AFG  | 1990 | 0.223206      | 4.996118   | 4.713314| 0.703023| 0.1277 |
| Afghanistan | AFG  | 1991 | 0.222454      | 4.989290   | 4.702100| 0.702069| 0.1232 |
| Afghanistan | AFG  | 1992 | 0.221751      | 4.981346   | 4.683743| 0.700792| 0.1188 |
| Afghanistan | AFG  | 1993 | 0.220987      | 4.976958   | 4.673549| 0.700087| 0.1150 |
| Afghanistan | AFG  | 1994 | 0.220183      | 4.977782   | 4.670810| 0.699898| 0.1118 |
```

###  Dataset Setelah Prapemrosesan

```text
| Schizophrenia | Depression | Anxiety | Bipolar | Eating |
|---------------|------------|---------|---------|--------|
| 0.223206      | 4.996118   | 4.713314| 0.703023| 0.1277 |
| 0.222454      | 4.989290   | 4.702100| 0.702069| 0.1232 |
| 0.221751      | 4.981346   | 4.683743| 0.700792| 0.1188 |
| 0.220987      | 4.976958   | 4.673549| 0.700087| 0.1150 |
| 0.220183      | 4.977782   | 4.670810| 0.699898| 0.1118 |
```

###  Dataset Setelah Normalisasi Min-Max

```text
| Bipolar_2 | Anxiety_2 | Depression_2 | Schizophrenia_2 | Asli_Schizophrenia |
|-----------|-----------|--------------|------------------|---------------------|
| 0.494242  | 22.215329 | 24.961195    | 0.049821         | 0.223206            |
| 0.492901  | 22.109744 | 24.893013    | 0.049486         | 0.222454            |
| 0.491109  | 21.937448 | 24.813805    | 0.049174         | 0.221751            |
| 0.490122  | 21.842057 | 24.770114    | 0.048835         | 0.220987            |
| 0.489857  | 21.816466 | 24.778314    | 0.048481         | 0.220183            |
```

---

##  Alur Proyek

### 1. Data Understanding

* Menyusun dan mengeksplorasi data dari berbagai sumber
* Mengecek null value dan anomali (`<0.1`) kemudian mengganti dengan `0.1`
* Analisis korelasi antar fitur

### 2. Data Preparation

* Menghapus kolom non-kuantitatif
* Normalisasi skala data jika diperlukan
* Split data: 80% train, 20% test

### 3. Pemodelan

Model yang digunakan adalah **Linear Regression** dari `scikit-learn`.

```python
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train, y_train)
```

### 4. Evaluasi Model

Metrik evaluasi yang digunakan:

* MAE (Mean Absolute Error)
* MSE (Mean Squared Error)
* R2 Score (Koefisien Determinasi)

Contoh hasil evaluasi:

```text
MAE : 0.03637501748971194
MSE : 0.0031479673672910663
R2 Score : 0.8808354730442264
```

### 5. Visualisasi

Menampilkan scatter plot prediksi vs aktual dengan garis ideal:

```python
plt.scatter(y_test, y_pred, alpha=0.7)
plt.plot([min, max], [min, max], 'r--')
```

---

##  Tools dan Library

* Python 3
* Pandas, NumPy
* scikit-learn
* Matplotlib, Seaborn
* Plotly Express

---

##  Hasil Akhir

* Model regresi memberikan prediksi cukup akurat dengan R2 Score > 0.85
* Dapat diimplementasikan untuk mengisi kekosongan data schizophrenia di negara-negara yang tidak memiliki data tersebut

---

##  Kesesuaian Submission Dicoding

| Kriteria                          | Status |
| --------------------------------- | ------ |
| Proyek dikerjakan sendiri         | ✅      |
| Belum pernah digunakan sebelumnya | ✅      |
| Data kuantitatif > 500 sampel     | ✅      |
| Pendekatan ML (regresi)           | ✅      |
| Dokumentasi text cell di notebook | ✅      |
| Visualisasi dan evaluasi lengkap  | ✅      |

---

##  Draft Laporan (Outline)

1. Problem Domain
2. Data Collection
3. Data Understanding
4. Data Preparation
5. Modeling
6. Evaluation
7. Kesimpulan

---

##  Author

**Nama**: [Raffi Arya Putra Prabowo]
**Cohort ID**	  : MC211D5Y1608
**Submission**: Dicoding - Machine Learning Terapan

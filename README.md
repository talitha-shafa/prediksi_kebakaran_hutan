# 🔥 Prediksi Terjadinya Kebakaran Hutan Berdasarkan Faktor Cuaca dan Indeks Cuaca Kebakaran Menggunakan AdaBoost

---

## 1. 📌 Judul

**Prediksi Terjadinya Kebakaran Hutan Berdasarkan Faktor Cuaca dan Indeks Cuaca Kebakaran Menggunakan AdaBoost**

Proyek ini merupakan Tugas Besar mata kuliah Machine Learning yang membangun model klasifikasi biner untuk memprediksi apakah suatu kondisi cuaca dan indeks FWI (Fire Weather Index) akan menyebabkan terjadinya kebakaran hutan atau tidak.

---

## 2. 📄 Deskripsi Proyek

Kebakaran hutan merupakan bencana alam yang memberikan dampak serius terhadap ekosistem, kesehatan masyarakat, dan perekonomian. Dataset yang digunakan berasal dari Taman Alam Montesinho, Portugal, dan mencatat berbagai kondisi cuaca serta komponen Fire Weather Index (FWI) dari setiap kejadian kebakaran.

Pendekatan dalam proyek ini mengubah masalah dari **regresi** (memprediksi luas area terbakar) menjadi **klasifikasi biner**:

- `1` → Terjadi kebakaran (`area > 0` hektar)
- `0` → Tidak terjadi kebakaran (`area = 0`)

Model dibangun menggunakan algoritma **AdaBoost (Adaptive Boosting)** dengan base estimator Decision Tree, dioptimasi menggunakan **GridSearchCV**, serta dilengkapi analisis imbalance data menggunakan **SMOTE** dan **feature engineering** berbasis domain knowledge FWI.

---

## 3. 🎯 Tujuan

1. Membangun model klasifikasi biner untuk memprediksi terjadinya kebakaran hutan berdasarkan faktor cuaca dan indeks FWI
2. Mengoptimalkan hyperparameter model AdaBoost secara otomatis menggunakan GridSearchCV
3. Menganalisis distribusi kelas dan menangani potensi ketidakseimbangan data (class imbalance)
4. Menerapkan feature engineering untuk meningkatkan kemampuan diskriminasi model
5. Mengidentifikasi fitur cuaca dan FWI yang paling berpengaruh terhadap prediksi kebakaran hutan
6. Membandingkan performa model utama dengan pendekatan SMOTE

---

## 4. 🗂️ Struktur Notebook

Notebook `Prediksi_Kebakaran_Hutan_AdaBoost.ipynb` disusun dengan urutan sebagai berikut:

| Bagian | Isi |
|--------|-----|
| **1. Judul** | Judul penelitian |
| **2. Latar Belakang / Urgensi** | Motivasi dan pentingnya prediksi kebakaran hutan |
| **3. Gap Penelitian / Novelty** | Kebaruan dibanding penelitian sebelumnya |
| **4. Tujuan** | Target yang ingin dicapai |
| **5. Metode** | Ringkasan pipeline metodologi |
| **5.1 Import Library** | Seluruh library yang digunakan |
| **5.2 Load & Eksplorasi Dataset** | Membaca data, shape, info, dan missing values |
| **5.3 Preprocessing Data** | Pembuatan label target, seleksi fitur |
| **5.4 Analisis Distribusi Kelas** | Cek imbalance dan visualisasi kelas |
| **5.5 Feature Engineering** | Penambahan fitur turunan FWI |
| **5.6 Split Data** | Pembagian 80% training, 20% testing |
| **5.7 Training AdaBoost + GridSearchCV** | Pencarian hyperparameter terbaik |
| **5.8 Evaluasi Model Utama** | Accuracy, Precision, Recall, F1, ROC-AUC |
| **5.9 Visualisasi Confusion Matrix** | Heatmap confusion matrix |
| **5.10 Feature Importance** | Kontribusi setiap fitur terhadap model |
| **6. Analisis Akurasi Rendah** | Penyebab dan upaya peningkatan performa |
| **6.3 Percobaan SMOTE** | Training ulang dengan data sintetis SMOTE |
| **6.4 Perbandingan Model** | Tabel dan grafik perbandingan semua model |
| **7. Kesimpulan** | Analisis hasil dan kesimpulan akhir |

---

## 5. 📊 Dataset

| Atribut | Keterangan |
|---------|------------|
| **Nama** | Forest Fires Dataset |
| **Sumber** | UCI Machine Learning Repository |
| **Lokasi** | Taman Alam Montesinho, Portugal (2000–2003) |
| **Jumlah Data** | 517 baris |
| **Jumlah Kolom** | 13 kolom (asli) |
| **File** | `forestfires.csv` |

### Kolom Dataset

| Kolom | Tipe | Keterangan | Digunakan |
|-------|------|------------|-----------|
| `X` | Integer | Koordinat spasial sumbu X | ❌ Tidak |
| `Y` | Integer | Koordinat spasial sumbu Y | ❌ Tidak |
| `month` | String | Bulan kejadian | ❌ Tidak |
| `day` | String | Hari kejadian | ❌ Tidak |
| `FFMC` | Float | Fine Fuel Moisture Code (Indeks FWI) | ✅ Ya |
| `DMC` | Float | Duff Moisture Code (Indeks FWI) | ✅ Ya |
| `DC` | Float | Drought Code (Indeks FWI) | ✅ Ya |
| `ISI` | Float | Initial Spread Index (Indeks FWI) | ✅ Ya |
| `temp` | Float | Suhu udara (°C) | ✅ Ya |
| `RH` | Integer | Kelembapan relatif (%) | ✅ Ya |
| `wind` | Float | Kecepatan angin (km/h) | ✅ Ya |
| `rain` | Float | Curah hujan (mm/m²) | ✅ Ya |
| `area` | Float | Luas area terbakar (ha) — diubah jadi label biner | ✅ Target |

> **Catatan:** Kolom `X`, `Y`, `month`, dan `day` sengaja tidak digunakan karena tidak merepresentasikan faktor cuaca maupun kondisi fisik yang relevan dengan judul penelitian.

### Distribusi Kelas Target

| Kelas | Label | Jumlah | Persentase |
|-------|-------|--------|------------|
| `0` | Tidak terjadi kebakaran | 247 | 47.8% |
| `1` | Terjadi kebakaran | 270 | 52.2% |
| | **Rasio imbalance** | **1.09** | Relatif seimbang |

---

## 6. 🛠️ Tech Stack & Library

| Library | Versi | Fungsi |
|---------|-------|--------|
| `Python` | ≥ 3.8 | Bahasa pemrograman utama |
| `pandas` | — | Manipulasi dan eksplorasi data |
| `numpy` | — | Operasi numerik dan array |
| `matplotlib` | — | Visualisasi grafik dan chart |
| `scikit-learn` | — | Model ML, preprocessing, dan evaluasi |
| `imbalanced-learn` | — | Teknik SMOTE untuk oversampling |

### Detail Modul scikit-learn

```
sklearn.model_selection    → train_test_split, GridSearchCV
sklearn.tree               → DecisionTreeClassifier (base estimator)
sklearn.ensemble           → AdaBoostClassifier
sklearn.metrics            → accuracy_score, balanced_accuracy_score,
                             precision_score, recall_score, f1_score,
                             confusion_matrix, classification_report,
                             roc_auc_score
```

### Instalasi Library

```bash
pip install pandas numpy matplotlib scikit-learn imbalanced-learn
```

---

## 7. ⚙️ Preprocessing

Tahapan preprocessing yang dilakukan:

### 7.1 Pembuatan Label Target
Kolom `area` (luas area terbakar) dikonversi menjadi label biner:
```python
df['fire_occurred'] = df['area'].apply(lambda x: 1 if x > 0 else 0)
```

### 7.2 Seleksi Fitur
Hanya 8 fitur yang dipilih sebagai input model — faktor cuaca dan indeks FWI:
```python
X = df[['FFMC', 'DMC', 'DC', 'ISI', 'temp', 'RH', 'wind', 'rain']]
```

### 7.3 Analisis Imbalance
Distribusi kelas dicek menggunakan rasio imbalance. Hasilnya menunjukkan data **relatif seimbang** (rasio ≈ 1.09), sehingga imbalance bukan penyebab utama rendahnya akurasi.

### 7.4 Feature Engineering
Tiga fitur turunan ditambahkan untuk memperkaya representasi data:

| Fitur Baru | Formula | Makna |
|------------|---------|-------|
| `FWI_total` | `FFMC + DMC + DC + ISI` | Akumulasi total indeks FWI |
| `heat_stress` | `temp × (100 - RH) / 100` | Tekanan panas berdasarkan suhu dan kelembapan |
| `wind_rain_ratio` | `wind / (rain + 0.1)` | Rasio angin terhadap hujan |

### 7.5 Split Data
```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42, stratify=y
)
```
- Training set: **413 data (80%)**
- Testing set : **104 data (20%)**
- `stratify=y` memastikan proporsi kelas sama di training dan testing

---

## 8. 🧠 Arsitektur Model

### Algoritma Utama: AdaBoost (Adaptive Boosting)

AdaBoost adalah algoritma ensemble yang bekerja secara iteratif:
1. Melatih *weak learner* (Decision Tree) pada data
2. Memberikan bobot lebih besar pada data yang salah diklasifikasi
3. Menggabungkan semua weak learner menjadi satu *strong classifier*

```
AdaBoostClassifier
│
├── Base Estimator: DecisionTreeClassifier
│   └── max_depth: 2 (hasil GridSearchCV)
│
├── n_estimators: 50 (jumlah weak learner)
├── learning_rate: 0.1
└── algorithm: SAMME (default sklearn)
```

### Penanganan Imbalance: SMOTE
SMOTE (Synthetic Minority Oversampling Technique) digunakan sebagai eksperimen tambahan:
- Mensintesis data baru pada kelas minoritas secara interpolasi
- Menyeimbangkan distribusi kelas sebelum training

---

## 9. 🔧 Konfigurasi Training

### GridSearchCV — Ruang Pencarian Hyperparameter

| Parameter | Nilai yang Dicoba | Terpilih |
|-----------|-------------------|----------|
| `n_estimators` | 50, 100, 200 | **50** |
| `learning_rate` | 0.05, 0.1, 0.3, 0.8 | **0.1** |
| `estimator__max_depth` | 1, 2, 3 | **2** |

### Konfigurasi GridSearchCV

```python
GridSearchCV(
    estimator  = AdaBoostClassifier(...),
    param_grid = param_grid,
    cv         = 5,          # 5-fold cross validation
    scoring    = 'f1',       # optimasi berdasarkan F1-Score
    n_jobs     = -1          # gunakan semua core CPU
)
```

### Konfigurasi SMOTE (Eksperimen)

```python
SMOTE(random_state=42)
AdaBoostClassifier(
    estimator    = DecisionTreeClassifier(max_depth=2),
    n_estimators = 100,
    learning_rate = 0.05
)
```

---

## 10. 📈 Evaluasi

### Hasil Model Utama (AdaBoost + GridSearchCV + Feature Engineering)

| Metrik | Nilai |
|--------|-------|
| **Accuracy** | 0.6250 |
| **Balanced Accuracy** | 0.6196 |
| **Precision** | 0.6119 |
| **Recall** | 0.7593 |
| **F1-Score** | 0.6777 |
| **ROC-AUC** | 0.6013 |

### Perbandingan Model

| Model | Accuracy | F1-Score | ROC-AUC |
|-------|----------|----------|---------|
| AdaBoost + GridSearchCV | **0.6250** | **0.6777** | 0.6013 |
| AdaBoost + SMOTE | 0.5481 | 0.5524 | **0.6109** |

### Feature Importance (Top 5)

| Peringkat | Fitur | Importance |
|-----------|-------|------------|
| 1 | `RH` (Kelembapan Relatif) | 0.2900 |
| 2 | `temp` (Suhu) | 0.1950 |
| 3 | `wind_rain_ratio` | 0.1740 |
| 4 | `wind` (Kecepatan Angin) | 0.1343 |
| 5 | `DMC` (Duff Moisture Code) | 0.0825 |

### Analisis Penyebab Akurasi Terbatas

| Faktor | Kondisi | Dampak |
|--------|---------|--------|
| Imbalance data | Ringan (1.09) | Bukan penyebab utama |
| Ukuran dataset | Kecil (517 data) | Generalisasi terbatas |
| Batas keputusan | Kabur | Kebakaran kecil vs tidak ada sangat mirip |
| Label biner | Ambang `area = 0` | Sensitif terhadap satu titik batas |

---

## 11. ▶️ Cara Menjalankan

### Prasyarat

Pastikan Python ≥ 3.8 sudah terinstal, lalu install library yang dibutuhkan:

```bash
pip install pandas numpy matplotlib scikit-learn imbalanced-learn
```

### Langkah Menjalankan

1. **Clone / unduh** file proyek ini ke komputer lokal

2. **Pastikan struktur folder** sudah benar (lihat bagian Struktur Folder)

3. **Buka Jupyter Notebook**
   ```bash
   jupyter notebook
   ```
   atau menggunakan JupyterLab:
   ```bash
   jupyter lab
   ```

4. **Buka file notebook**
   ```
   Prediksi_Kebakaran_Hutan_AdaBoost.ipynb
   ```

5. **Jalankan semua cell** secara berurutan:
   - Klik menu **Kernel → Restart & Run All**, atau
   - Jalankan satu per satu dengan **Shift + Enter**

> ⚠️ **Penting:** File `forestfires.csv` harus berada di folder yang **sama** dengan file `.ipynb` agar perintah `pd.read_csv('forestfires.csv')` berhasil dijalankan.

---

## 12. 📁 Struktur Folder

```
project/
│
├── Prediksi_Kebakaran_Hutan_AdaBoost.ipynb   # Notebook utama
├── forestfires.csv                            # Dataset
└── README.md                                  # Dokumentasi proyek ini
```

---

## 13. ✅ Kesimpulan

1. **Model berhasil dibangun** — AdaBoost dengan GridSearchCV mampu mengklasifikasikan kondisi terjadinya kebakaran hutan berdasarkan 8 fitur cuaca dan indeks FWI, ditambah 3 fitur turunan hasil feature engineering.

2. **Judul selaras dengan program** — Fitur input mencakup faktor cuaca (`temp`, `RH`, `wind`, `rain`) dan Indeks Cuaca Kebakaran / Fire Weather Index (`FFMC`, `DMC`, `DC`, `ISI`), dengan metode AdaBoost sebagai classifier utama.

3. **Imbalance bukan penyebab utama** — Distribusi kelas relatif seimbang (47.8% vs 52.2%), sehingga rendahnya akurasi lebih disebabkan oleh ukuran dataset yang kecil (517 data) dan batas keputusan yang kabur antar kelas.

4. **Model terbaik adalah AdaBoost + GridSearchCV** dengan parameter `n_estimators=50`, `learning_rate=0.1`, `max_depth=2`, menghasilkan akurasi **62.5%** dan F1-Score **0.6777**.

5. **Fitur paling berpengaruh** adalah `RH` (kelembapan relatif) dan `temp` (suhu), diikuti fitur turunan `wind_rain_ratio` — menunjukkan bahwa kondisi kelembapan dan suhu udara adalah faktor dominan dalam prediksi kebakaran hutan.

6. **SMOTE tidak meningkatkan akurasi** secara signifikan karena data memang sudah relatif seimbang; justru menurunkan accuracy menjadi 54.8%, meskipun ROC-AUC sedikit meningkat (0.6109).

---

## 14. 💡 Saran Pengembangan

1. **Perbanyak data** — Dataset hanya 517 sampel. Menambah data dari sumber lain atau tahun yang berbeda dapat meningkatkan kemampuan generalisasi model secara signifikan.

2. **Coba algoritma lain** — Bandingkan AdaBoost dengan Random Forest, Gradient Boosting, atau XGBoost untuk melihat apakah ada peningkatan performa yang lebih signifikan.

3. **Optimasi threshold klasifikasi** — Alih-alih menggunakan threshold default 0.5, coba cari threshold optimal berdasarkan kurva ROC untuk menyeimbangkan precision dan recall sesuai kebutuhan.

4. **Penyesuaian definisi label** — Label biner `area > 0` sangat sensitif. Pertimbangkan threshold lain (misal `area > 1` ha) agar batas keputusan lebih representatif antara kebakaran signifikan dan tidak.

5. **Feature selection** — Gunakan metode seleksi fitur (seperti Recursive Feature Elimination) untuk membuang fitur yang tidak relevan dan mengurangi noise.

6. **Cross-validation lebih dalam** — Gunakan Stratified K-Fold secara eksplisit untuk mendapatkan estimasi performa yang lebih stabil mengingat ukuran data yang kecil.

7. **Hyperparameter tuning lebih luas** — Perluas ruang pencarian GridSearchCV atau gunakan RandomizedSearchCV / Bayesian Optimization untuk eksplorasi yang lebih efisien.

---

> **Dataset Reference:** Cortez, P., & Morais, A. (2007). *A Data Mining Approach to Predict Forest Fires using Meteorological Data*. UCI Machine Learning Repository.
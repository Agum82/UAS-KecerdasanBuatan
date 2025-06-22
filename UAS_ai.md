# Klasifikasi Dampak COVID-19 Global Menggunakan Artificial Neural Network (ANN)
Nama Kelompok:

Agum Aidil Saepul Rohman

# Business Understanding
# Permasalahan Dunia Nyata

Pandemi COVID-19 telah memberikan dampak besar terhadap berbagai negara di dunia, namun tingkat dampaknya berbeda-beda. Mengklasifikasikan tingkat dampak pandemi dapat membantu organisasi internasional dan pemerintah untuk memprioritaskan dukungan dan intervensi.

# Tujuan Proyek

Membangun model kecerdasan buatan untuk mengklasifikasikan negara-negara berdasarkan tingkat dampak COVID-19 (tinggi atau rendah) menggunakan metode Artificial Neural Network (ANN).

# Pengguna Sistem

Organisasi kesehatan dunia (WHO)

Pemerintah negara

Peneliti dan analis data kesehatan

# Manfaat Implementasi AI

Memberikan analisis cepat dan efisien dari dampak COVID-19

Menyediakan alat bantu pengambilan keputusan

Mendeteksi pola dan anomali dalam penyebaran pandemi
# Data Understanding

Sumber Data

Dataset diambil dari Kaggle: https://www.kaggle.com/datasets/imdevskp/corona-virus-report

Deskripsi Fitur
| Fitur                  | Deskripsi                                     |
|------------------------|-----------------------------------------------|
| Country/Region         | Nama negara                                   | 
| Confirmed              | Total kasus terkonfirmasi                     | 
| Deaths                 | Total kematian                                | 
| Recovered              | Total sembuh                                  | 
| Active                 | Kasus aktif                                   | 
| New cases              | Kasus baru terakhir                           |
| New deaths             | Kematian baru terakhir                        |
| New recovered          | Sembuh baru terakhir                          |
| Deaths / 100 Cases     | Persentase kematian per 100 kasus             |
| Recovered / 100 Cases  | Persentase sembuh per 100 kasus               |
| Deaths / 100 Recovered | Rasio kematian dibanding sembuh               |
| Confirmed last week    | Kasus minggu sebelumnya                       |
| 1 week change          | Selisih penambahan kasus minggu ini           |
| 1 week % increase      | Persentase peningkatan minggu ini             |
| WHO Region             | Wilayah WHO tempat negara berada              |

Ukuran dan Format Data

Format: CSV

Jumlah baris: 187 negara

Tipe data: Numerik dan kategorikal

Target Klasifikasi

Kelas High: negara dengan kematian > 10.000

Kelas Low: lainnya

# Exploratory Data Analysis (EDA)

Visualisasi Distribusi

Histogram dan bar chart menunjukkan distribusi jumlah kasus dan kematian


BAR CHART – 10 Negara dengan Kasus Tertinggi

 Pie chart proporsi WHO Region


Korelasi antar fitur

Heatmap menunjukkan korelasi tinggi antara jumlah kasus dan kematian

Beberapa fitur seperti Active dan Confirmed saling berkorelasi kuat


Deteksi Kelas Tidak Seimbang

Negara dengan kematian > 10.000 berjumlah sekitar 15% dari total data (kelas High lebih sedikit)


Insight Awal

Negara seperti Amerika Serikat, India, dan Brasil memiliki tingkat kematian tinggi

Beberapa negara memiliki rasio kesembuhan sangat tinggi

# Data Preparation

Pembersihan Data

Menghapus kolom non-numerik (seperti nama negara)

Mengganti nilai NaN dan Inf dengan 0

Encoding Kategorikal

Label target Impact: encoded menjadi 0 (Low) dan 1 (High)

Normalisasi

Semua fitur numerik dinormalisasi menggunakan MinMaxScaler

Split Data

80% data untuk training, 20% untuk testing menggunakan train_test_split

# Modeling

Algoritma: Artificial Neural Network (ANN)

Alasan Pemilihan Model

ANN mampu menangkap hubungan non-linear antar fitur

Cocok untuk klasifikasi biner

Fleksibel dalam arsitektur dan tuning

Arsitektur Model

Input layer: sesuai jumlah fitur

Hidden layer 1: 32 neuron, ReLU

Hidden layer 2: 16 neuron, ReLU

Output layer: 1 neuron, Sigmoid

Kode Implementasi Lengkap

IMPORT LIBRARY
import pandas as pd

import numpy as np

import matplotlib.pyplot as plt

import seaborn as sns

from sklearn.model_selection import train_test_split

from sklearn.preprocessing import LabelEncoder, MinMaxScaler

from sklearn.metrics import confusion_matrix, classification_report

import tensorflow as tf

from tensorflow.keras.models import Sequential

from tensorflow.keras.layers import Dense, Dropout

 LOAD DATA
data = pd.read_csv('/content/country_wise_latest.csv')

CREATE LABEL
data['Impact'] = data['Deaths'].apply(lambda x: 'High' if x > 10000 else 'Low')

PREPROCESSING
X = data.drop(columns=['Country/Region', 'WHO Region', 'Impact'])
X = X.replace([np.inf, -np.inf], np.nan).fillna(0)
scaler = MinMaxScaler()
X_scaled = scaler.fit_transform(X)

label_encoder = LabelEncoder()
y = label_encoder.fit_transform(data['Impact'])

X_train, X_test, y_train, y_test = train_test_split(X_scaled, y, test_size=0.2, random_state=42)

MODEL
model = Sequential([
    Dense(32, activation='relu', input_shape=(X_train.shape[1],)),
    Dropout(0.2),
    Dense(16, activation='relu'),
    Dense(1, activation='sigmoid')
])
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

history = model.fit(X_train, y_train, epochs=50, batch_size=8, validation_split=0.2, verbose=1)

EVALUASI
loss, acc = model.evaluate(X_test, y_test)
y_pred_prob = model.predict(X_test)
y_pred = (y_pred_prob > 0.5).astype('int32')

print(confusion_matrix(y_test, y_pred))
print(classification_report(y_test, y_pred, target_names=label_encoder.classes_))

VISUALISASI AKURASI
plt.figure(figsize=(10, 4))
plt.plot(history.history['accuracy'], label='Train Accuracy')
plt.plot(history.history['val_accuracy'], label='Validation Accuracy')
plt.title('Model Accuracy')
plt.xlabel('Epoch')
plt.ylabel('Accuracy')
plt.legend()
plt.grid(True)
plt.show()

# Evaluation

Confusion Matrix

Ditampilkan dengan fungsi confusion_matrix() dari sklearn

Metrik Evaluasi

| Metrik                 | Nilai                                         |
|------------------------|-----------------------------------------------|
| Accuracy               | 0.91                                          | 
| Precision              | 0.87                                          | 
| Recall                 | 0.89                                          | 
| F1-score               | 0.88                                          | 
          
Penjelasan Kinerja

Model ANN cukup akurat untuk klasifikasi ini

Recall tinggi menunjukkan model cukup sensitif dalam mendeteksi negara berdampak tinggi

# Kesimpulan dan Rekomendasi

Ringkasan

ANN berhasil mengklasifikasikan negara ke dalam dua kelas dampak COVID-19

Model memiliki akurasi > 90% pada data testing

Tujuan Tercapai?

Ya. Sistem berhasil mengklasifikasi tingkat dampak COVID-19 secara cukup akurat.

Kelebihan Model

Dapat menangkap hubungan non-linear

Akurasi tinggi

Keterbatasan

Dataset relatif kecil (187 negara)

Tidak mempertimbangkan data waktu (time series)

Rekomendasi

Tambahkan lebih banyak data historis (longitudinal)

Gunakan model lain untuk pembanding seperti Random Forest

Lakukan hyperparameter tuning dan cross-validation

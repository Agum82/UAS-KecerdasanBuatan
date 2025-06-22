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

Pie chart proporsi WHO Region

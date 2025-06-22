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
![image](https://github.com/user-attachments/assets/e2304cc8-c2de-453e-946c-ad0d9d13cb14)

BAR CHART – 10 Negara dengan Kasus Tertinggi
![image](https://github.com/user-attachments/assets/9ddad11e-394a-4cc5-aaf9-19504ff52a1e)
 Pie chart proporsi WHO Region

![image](https://github.com/user-attachments/assets/d3ad106e-f50a-44bf-9ad5-677324a6efd5)

Korelasi antar fitur

Heatmap menunjukkan korelasi tinggi antara jumlah kasus dan kematian

Beberapa fitur seperti Active dan Confirmed saling berkorelasi kuat
![image](https://github.com/user-attachments/assets/cde02e55-efd0-43b6-820d-01ef0aafefb7)

Deteksi Kelas Tidak Seimbang

Negara dengan kematian > 10.000 berjumlah sekitar 15% dari total data (kelas High lebih sedikit)

![image](https://github.com/user-attachments/assets/682f65d0-c4a2-4112-ae49-563fcaa8198e)
![image](https://github.com/user-attachments/assets/dd3e4ffe-7de3-40be-a396-71a95441e8f6)



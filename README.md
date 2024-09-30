# JCDSOL15-CAPSTONE3-RMGT
# Prediksi Pembatalan Reservasi Hotel

Proyek ini bertujuan untuk memprediksi pembatalan reservasi hotel menggunakan model pembelajaran mesin berdasarkan berbagai fitur pemesanan pelanggan. Dengan membangun model prediksi, diharapkan dapat membantu manajer hotel mengurangi potensi kerugian pendapatan akibat pembatalan mendadak dan mengoptimalkan pemanfaatan kamar.

## Daftar Isi
- [Ringkasan](#ringkasan)
- [Dataset](#dataset)
- [Alur Pembelajaran Mesin](#alur-pembelajaran-mesin)
- [Rekayasa Fitur](#rekayasa-fitur)
- [Evaluasi Model](#evaluasi-model)
- [Kesimpulan dan Rekomendasi](#kesimpulan-dan-rekomendasi)
- [Instalasi](#instalasi)
- [Penggunaan](#penggunaan)
- [Lisensi](#lisensi)

## Ringkasan
Proyek **Prediksi Pembatalan Reservasi Hotel** berfokus pada memprediksi pembatalan berdasarkan fitur-fitur seperti negara asal pelanggan, segmen pasar, jumlah pembatalan sebelumnya, jenis deposit, dan detail pemesanan lainnya. Model ini dapat membantu mengurangi risiko overbooking dan memaksimalkan pendapatan hotel.

### Pernyataan Masalah
Tingkat pembatalan reservasi yang tinggi di hotel sering menyebabkan kamar kosong dan pendapatan yang hilang. Memprediksi pembatalan dapat membantu manajemen hotel mengambil langkah-langkah pencegahan, seperti menawarkan kembali kamar atau menyesuaikan kebijakan untuk pelanggan berisiko tinggi.

## Dataset
Dataset yang digunakan untuk proyek ini berjudul **data_hotel_booking_demand.csv**. Dataset ini berisi informasi pemesanan seperti:
- `country`: Negara asal tamu.
- `market_segment`: Segmen pasar pemesanan (misalnya, Online TA, Direct, dll.).
- `previous_cancellations`: Jumlah pembatalan sebelumnya oleh pelanggan.
- `deposit_type`: Jenis deposit untuk pemesanan (misalnya, Non-Refundable).
- `is_canceled`: Variabel target (1 = pemesanan dibatalkan, 0 = pemesanan tidak dibatalkan).

Dataset ini terdiri dari 83.573 baris dan 11 fitur, termasuk data kategorikal dan numerik.

## Alur Pembelajaran Mesin

1. **Formulasi Masalah dan Pemahaman Data**  
   Langkah awal melibatkan pemahaman konteks pembatalan pemesanan hotel dan merumuskan masalah sebagai masalah klasifikasi.

2. **Analisis Data Eksploratif (EDA)**  
   Menganalisis dataset, termasuk distribusi fitur dan korelasi antara fitur dan variabel target (`is_canceled`).

3. **Rekayasa Fitur**  
   Penanganan nilai yang hilang, encoding variabel kategorikal, dan transformasi fitur untuk persiapan pelatihan model.

4. **Pelatihan Model**  
   Beberapa model diuji, termasuk:
   - Random Forest
   - AdaBoost
   - XGBoost

5. **Evaluasi dan Seleksi Model**  
   Kinerja model dievaluasi menggunakan metrik seperti:
   - F1-Score
   - Precision
   - Recall
   - ROC AUC

6. **Kesimpulan dan Rekomendasi**  
   Wawasan akhir dan saran untuk manajemen hotel berdasarkan hasil prediksi model.

## Rekayasa Fitur

Rekayasa fitur melibatkan imputasi nilai yang hilang, encoding variabel kategorikal (menggunakan One-Hot Encoding dan Binary Encoding), dan transformasi fitur untuk pelatihan model. Fitur kategorikal seperti `country` dan `market_segment` diencode, sedangkan fitur numerik seperti `previous_cancellations` digunakan secara langsung.

## Evaluasi Model

Setelah menguji beberapa algoritma pembelajaran mesin, **Random Forest Classifier** mencapai performa terbaik dengan metrik sebagai berikut:
- **F1-Score:** 0.73
- **Precision:** 0.64
- **Recall:** 0.85
- **ROC AUC:** 0.79

Model kemudian dituning lebih lanjut menggunakan **Optuna** untuk optimasi hyperparameter, menghasilkan peningkatan performa.

## Kesimpulan dan Rekomendasi

Model Random Forest secara efektif memprediksi pembatalan reservasi dengan nilai recall yang tinggi, yang berarti mampu mengidentifikasi sebagian besar pembatalan potensial. Kami merekomendasikan langkah-langkah berikut berdasarkan prediksi model:
1. **Perbaiki kebijakan deposit** untuk pelanggan berisiko tinggi guna mengurangi pembatalan.
2. **Kirim email konfirmasi** kepada tamu yang diprediksi akan membatalkan untuk mendorong mereka mempertahankan reservasi.
3. **Publikasikan ulang kamar kosong** lebih awal jika pembatalan diprediksi.

## Instalasi

Untuk menjalankan proyek ini secara lokal, ikuti langkah-langkah berikut:

1. Clone repository:
   ```bash
   git clone https://github.com/username-kamu/hotel-booking-cancellation.git
   cd hotel-booking-cancellation
2. Instal dependensi yang diperlukan:
   ```bash
   pip install -r requirements.txt
3. Jalankan notebook untuk analisis:
    ```bash
    jupyter notebook hotel_booking_cancellation_analysis.ipynb

# Pengembangan Sistem Deteksi Anomali pada Data Sensor IoT Menggunakan Arsitektur Hybrid CNN-LSTM

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)
![License](https://img.shields.io/badge/License-MIT-green)

**Tugas Akhir Mata Kuliah Deep Learning**
* **Nama:** M Hisbulah Endima T
* **NPM:** G1A022034
* **Program Studi:** Informatika, Universitas Bengkulu
## 🎥 Presentasi Video
Tonton Presentasi ini di YouTube:
[Klik di sini untuk menonton Video Demo](https://youtu.be/mkppKqAivRQ?si=zvLbERDRevkSTyaT))

---

## 📌 Latar Belakang
Dalam era Industri 4.0, sensor IoT menghasilkan data deret waktu (*time-series*) dalam volume masif. Kerusakan mesin seringkali diawali oleh pola anomali yang halus dan sulit dideteksi oleh metode pemantauan manual maupun statistik konvensional.

Proyek ini bertujuan membangun sistem **Deteksi Anomali Otomatis** menggunakan pendekatan **Deep Learning Hybrid** yang menggabungkan:
* **1D-CNN (Convolutional Neural Network):** Untuk mengekstrak fitur spasial dan mereduksi *noise* dari sinyal sensor.
* **LSTM (Long Short-Term Memory):** Untuk memodelkan ketergantungan waktu jangka panjang (*temporal dependencies*).

## 📂 Dataset
Dataset yang digunakan bersumber dari **Numenta Anomaly Benchmark (NAB)**, spesifiknya pada kasus **Temperature Sensor Data** dari mesin internal.
* **Sumber:** [Numenta GitHub Repository](https://github.com/numenta/NAB)
* **File:** (./data/machine_temperature_system_failure.csv)
* **Karakteristik:** Data *time-series* dengan label anomali akibat kegagalan sistem pendingin.

## 🛠️ Arsitektur Model
Model dibangun menggunakan **TensorFlow/Keras** dengan konfigurasi:
1.  **Input Layer:** Sliding Window (60 Time Steps).
2.  **Conv1D Layer:** 64 Filters, Kernel Size 3, ReLU.
3.  **Dropout Layer:** 0.2 (Mencegah Overfitting).
4.  **LSTM Layer:** 30 Units (Hasil Hyperparameter Tuning Terbaik).
5.  **Output Layer:** Dense Layer (Prediksi Nilai Suhu).

## 📊 Hasil Evaluasi
Model dilatih menggunakan mekanisme **Early Stopping** (berhenti di Epoch 13) untuk efisiensi. Berikut perbandingan performa model usulan dengan *baseline*:

| Model | F1-Score | Keterangan |
| :--- | :--- | :--- |
| **Hybrid CNN-LSTM (Usulan)** | **0.8571** | Akurasi tinggi, mampu mendeteksi anomali kritis secara robust. |
| One-Class SVM (Baseline) | 0.0122 | Gagal menangkap pola temporal data sensor. |

> **Kesimpulan:** Arsitektur Hybrid CNN-LSTM terbukti **84% lebih unggul** dibandingkan metode konvensional SVM pada dataset ini.

## 🚀 Fitur & Deployment
* **Preprocessing Otomatis:** Normalisasi MinMax & Sliding Window Sequence.
* **Hyperparameter Tuning:** Eksperimen jumlah unit LSTM (30 vs 60).
* **TFLite Support:** Model berhasil diekspor ke format `.tflite` (Lightweight) sehingga siap diimplementasikan pada perangkat *Edge IoT* (Raspberry Pi/ESP32).


## 📄 Dokumentasi Lengkap
* [Laporan Tugas Akhir (PDF)](./docs/Laporan_Tugas_Akhir.pdf)
* [Slide Presentasi (PDF)](./docs/Slide_Presentasi.pdf)

---
*Dibuat untuk memenuhi Tugas Akhir Deep Learning - 2025.*

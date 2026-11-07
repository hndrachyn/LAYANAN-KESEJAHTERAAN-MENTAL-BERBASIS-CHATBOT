# Layanan Kesejahteraan Mental Berbasis Chatbot

Aplikasi web (Flask) untuk layanan kesejahteraan mental yang menggabungkan survei, konsultasi, chatbot, dan model prediksi. Repositori ini adalah fork dari proyek kelompok [chaerudin91/HERADA-_Project](https://github.com/chaerudin91/HERADA-_Project).

## Fitur

- Registrasi dan login pengguna.
- **Survei kesejahteraan**: skor dikelompokkan ke dalam kategori kesejahteraan, hasilnya ditampilkan di halaman hasil.
- **Konsultasi**: daftar psikolog dan halaman konsultasi.
- **Chatbot**: menjawab dalam bahasa Indonesia dengan Google Generative AI (Gemini) setelah mendeteksi bahasa pesan. Tersedia juga fungsi integrasi Dialogflow.
- **Prediksi**: endpoint `POST /predict` menerima delapan fitur data tidur dan fisiologis (`snoring_rate`, `respiration_rate`, `body_temperature`, `limb_movement`, `blood_oxygen`, `eye_movement`, `sleeping_hours`, `heart_rate`) dan memprosesnya dengan model Keras.
- Halaman berita dan komunitas.

## Struktur proyek

| Lokasi | Isi |
|---|---|
| `run.py`, `config.py` | Titik masuk aplikasi dan konfigurasi |
| `app/routes.py` | Semua rute (halaman, survei, chat, prediksi) |
| `app/database.py` | Koneksi database MySQL |
| `app/templates/` | Halaman HTML |
| `models/` | Model terlatih (`Improved_Keras_model.h5`, `Model.pkl`) |
| `dataset/dataset.csv` | Data yang dipakai untuk model |
| `requirement.txt` | Daftar dependensi dasar |

## Teknologi

Python, Flask, MySQL, TensorFlow/Keras, scikit-learn, Google Generative AI, Dialogflow, langdetect.

## Cara menjalankan

1. Pasang dependensi: `pip install -r requirement.txt`. Paket lain yang dipakai di `app/routes.py` perlu dipasang juga (misalnya `flask-mysqldb`, `google-generativeai`, `google-cloud-dialogflow`, `langdetect`, `scikit-learn`).
2. Siapkan database MySQL lokal dan sesuaikan nama database serta kredensial di `config.py`.
3. Siapkan kunci API Gemini dan kredensial Google Dialogflow milik Anda sendiri. Kunci tidak boleh disimpan langsung di kode.
4. Jalankan: `python run.py` (aplikasi berjalan di port 8000).

## Catatan

Ganti semua nilai rahasia (kunci API dan `SECRET_KEY`) dengan variabel lingkungan sebelum aplikasi dipakai di luar lingkungan belajar.

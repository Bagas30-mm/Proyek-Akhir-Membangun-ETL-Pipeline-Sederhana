## 📦 Proyek Akhir: Implementasi Pipeline ETL Sederhana

Dalam proyek ini, peserta mengembangkan sebuah **pipeline ETL (Extract, Transform, Load)** untuk mengotomatisasi pengolahan data produk fashion. Proses dimulai dari pengambilan data dari situs [Fashion Studio Dicoding](https://fashion-studio.dicoding.dev/), dilanjutkan dengan transformasi data agar siap digunakan untuk analisis, dan berakhir dengan penyimpanan data ke tiga media berbeda:

- **CSV lokal** untuk penyimpanan file sederhana  
- **PostgreSQL** untuk penyimpanan data terstruktur  
- **Google Spreadsheet** untuk kemudahan kolaborasi berbasis cloud

Tujuan dari proyek ini adalah memberikan pemahaman praktis terkait implementasi ETL pada data dari situs web nyata.

---

### ✨ Fitur Utama

#### 🔍 Ekstraksi
Mengambil data HTML dari halaman web menggunakan pustaka `requests` dan `BeautifulSoup`.

#### 🔧 Transformasi
Proses transformasi meliputi:
- Konversi harga ke Rupiah (1 USD = Rp16.000)
- Pembersihan nilai rating seperti “Invalid Rating”
- Ekstraksi angka dari kolom warna (contoh: "3 Colors" → `3`)
- Normalisasi teks kolom ukuran dan gender
- Penambahan kolom `timestamp` saat scraping

#### 💾 Penyimpanan
Hasil data yang telah dibersihkan disimpan ke:
- File CSV
- Database PostgreSQL
- Google Sheets menggunakan API resmi

---

## 📁 Struktur Folder
```
├── screenshoot/
├── tests/
├── utils/
├── main.py
├── requirements.txt
├── submission.txt
├── fashion_data.csv
└── README.md
```

---

## ⚙ Teknologi dan Library
- Python 3.9
- BeautifulSoup, Pandas
- SQLAlchemy
- Google Sheets API
- PostgreSQL
- Pytest & Coverage

---

## 📤 Output Akhir
- **CSV:** `fashion_data.csv`  
- **Database:** PostgreSQL (`fashion_db.fashion_products`)  
- **Spreadsheet:** [Google Sheets](https://docs.google.com/spreadsheets/...)

---

## 🧪 Hasil Uji Coba Terminal
Log mencakup:
- Proses scraping 1000 produk
- Informasi struktur data sebelum dan sesudah transformasi
- Penyimpanan data ke tiga media berhasil
- Ringkasan jumlah data sebelum (1000) dan sesudah (867) pembersihan

---

## 🔍 Test Coverage
Cakupan pengujian mencapai **95%**, mencakup seluruh pipeline (extract, transform, load).

---

## 🚀 Cara Menjalankan Proyek

### Instalasi Awal
```bash
git clone https://github.com/maxwellmassie/submission-prada.git
python -m venv .env
.env\Scripts\activate  # Windows
pip install -r requirements.txt
```

### Konfigurasi PostgreSQL
Edit bagian konfigurasi di `utils/load.py` sesuai kredensial Anda.

### Menjalankan Proyek
```bash
python main.py
```

### Menjalankan Pengujian
```bash
pytest tests
pytest tests --cov --cov-report=html
```

---
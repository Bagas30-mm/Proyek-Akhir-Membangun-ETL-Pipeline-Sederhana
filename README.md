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

Memulai proses ekstraksi data...
Scraping halaman: https://fashion-studio.dicoding.dev/
.....
Scraping halaman: https://fashion-studio.dicoding.dev/page50
Ekstraksi selesai. Jumlah data: 1000

=======Informasi Data Sebelum Transformasi:=======
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 1000 entries, 0 to 999
Data columns (total 7 columns):
 #   Column     Non-Null Count  Dtype
---  ------     --------------  -----
 0   Title      1000 non-null   object
 1   Price      1000 non-null   object
 2   Rating     1000 non-null   object
 3   Colors     1000 non-null   object
 4   Size       1000 non-null   object
 5   Gender     1000 non-null   object
 6   Timestamp  1000 non-null   datetime64[ns]
dtypes: datetime64[ns](1), object(6)
memory usage: 54.8+ KB
None

=======Data Head Sebelum Transformasi:=======
             Title    Price          Rating Colors Size  Gender                  Timestamp
0  Unknown Product  $100.00  Invalid Rating      5    M     Men 2025-05-12 21:55:46.510667
1        T-shirt 2  $102.15           ⭐ 3.9      3    M   Women 2025-05-12 21:55:46.510667
2         Hoodie 3  $496.88           ⭐ 4.8      3    L  Unisex 2025-05-12 21:55:46.510667
3          Pants 4  $467.31           ⭐ 3.3      3   XL     Men 2025-05-12 21:55:46.510667
4      Outerwear 5  $321.59           ⭐ 3.5      3  XXL   Women 2025-05-12 21:55:46.510667

Memulai proses transformasi data...
Transformasi selesai. Jumlah data setelah dibersihkan: 867

=======Informasi Data Setelah Transformasi:=======
<class 'pandas.core.frame.DataFrame'>
Index: 867 entries, 1 to 999
Data columns (total 7 columns):
 #   Column     Non-Null Count  Dtype
---  ------     --------------  -----
 0   Title      867 non-null    object
 1   Price      867 non-null    float64
 2   Rating     867 non-null    float64
 3   Colors     867 non-null    int64
 4   Size       867 non-null    object
 5   Gender     867 non-null    object
 6   Timestamp  867 non-null    object
dtypes: float64(2), int64(1), object(4)
memory usage: 54.2+ KB
None

=======Data Head Setelah Transformasi:=======
         Title      Price  Rating  Colors Size  Gender                   Timestamp
1    T-shirt 2  1634400.0     3.9       3    M   Women  2025-05-12T21:55:46.510667
2     Hoodie 3  7950080.0     4.8       3    L  Unisex  2025-05-12T21:55:46.510667
3      Pants 4  7476960.0     3.3       3   XL     Men  2025-05-12T21:55:46.510667
4  Outerwear 5  5145440.0     3.5       3  XXL   Women  2025-05-12T21:55:46.510667
5     Jacket 6  2453920.0     3.3       3    S  Unisex  2025-05-12T21:55:46.511666

Memulai proses load data ke storage (CSV, PostgreSQL, Google Sheets)...
[Flatfile-.CSV] Data berhasil disimpan ke fashion_data.csv
[PostgreSQL] Data berhasil disimpan ke tabel fashion_products.
[Google Sheets] Data berhasil disimpan ke Spreadsheets(Pemrosesan Data Fashion).
Proses ETL selesai dengan sukses.
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
git clone https://github.com/Bagas30-mm/Proyek-Akhir-Membangun-ETL-Pipeline-Sederhana.git
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

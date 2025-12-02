## Petunjuk Singkat Pengujian Model (Untuk Dosen)

Ringkasan singkat untuk menjalankan pengujian model DenseNet121 (fine-tuned) menggunakan notebook `program_test.ipynb`.

Tujuan
- Menghitung metrik: akurasi, precision, recall, F1-score, dan menampilkan confusion matrix.
- Menghasilkan file prediksi akhir yang siap untuk pengecekan otomatis.

Model yang digunakan
- DenseNet121 (fine-tuned)
- Lokasi model: `models/densenet121_facecls.pth`

Prasyarat
- Python environment dengan dependensi yang diperlukan (lihat `requirements.txt`).
- Notebook `program_test.ipynb` berada di root project.

1) Struktur folder yang harus disiapkan
Pastikan struktur folder seperti berikut (jalankan dari direktori project):

```
.
├── program_test.ipynb      # Notebook yang dijalankan
├── models/
│     ├── densenet121_facecls.pth
│     └── label_mapping.json
├── Test/
│     ├── IMG_001.jpg
│     ├── IMG_002.jpg
         └── ...
└── test.csv                # CSV dengan kolom: filename,label
```

2) Format file `test.csv`
File `test.csv` harus berformat CSV sederhana dengan header `filename,label`. Contoh:

```
filename,label
IMG_001.jpg,NamaMahasiswa
IMG_002.jpg,NamaMahasiswa
IMG_003.jpg,NamaMahasiswaLain
```

3) Langkah menjalankan pengujian
- Buka `program_test.ipynb` di Jupyter / Kaggle / Colab
- Pastikan working directory mengarah ke direktori project
- Klik `Run All` (atau jalankan semua cell secara berurutan)

Notebook akan otomatis:
- Membaca `test.csv`
- Membaca semua gambar di folder `Test/` sesuai `filename` di CSV
- Melakukan face-cropping (jika ada) dan pra-pemrosesan yang diperlukan
- Menjalankan model DenseNet121 untuk inferensi
- Menghitung metrik performa (accuracy, precision, recall, F1)
- Menampilkan confusion matrix
- Menyimpan hasil prediksi

4) Output yang dihasilkan
Setelah notebook selesai, folder `test_outputs/` akan berisi file seperti:

```
test_outputs/
├── jawaban_densenet121_full.csv    # versi lengkap (untuk analisis)
└── jawaban_densenet121_submit.csv  # file final (format: filename,label)
```

- `jawaban_densenet121_submit.csv` dapat digunakan untuk pengecekan otomatis.

Catatan penting
- Pastikan file `models/label_mapping.json` ada — ini digunakan untuk memetakan kelas (label) ke nama mahasiswa.
- Jika menggunakan GPU, pastikan environment sudah mengarah ke perangkat GPU.
- Untuk dataset berukuran besar, pastikan kapasitas penyimpanan dan memori memadai.

Kontak
- Jika ada masalah saat menjalankan, silakan hubungi salah satu anggota tim:
    - Ikhsannudin Lathief — 122140137
    - Shintya Ayu Wardani — 122140138
    - Aldi Sanjaya — 122140150

---
Dokumentasi ini dirancang untuk memudahkan dosen melakukan pengujian cepat tanpa konfigurasi tambahan.


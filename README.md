# Tugas Besar Pembelajaran Mendalam - Face Classification

## Kelompok: NVTeam (Neural Vision Team)

### Anggota Kelompok - Pembelajaran Mendalam RA
1. **Ikhsannudin Lathief** - 122140137
2. **Shintya Ayu Wardani** - 122140138
3. **Aldi Sanjaya** - 122140150

## Model Terbaik:
**DenseNet121** (`densenet121_facecls.pth`)

## Tautan

### Aplikasi: [Hugging Face - Streamlit](https://huggingface.co/spaces/AldiSanjaya121/PengenalWajahMahasiswa)
### Video Presentasi: [Youtube](https://youtu.be/-RVCa59FNnM?si=QdQp6YWmByHC7S6B)
### Poster: [Gdrive](https://drive.google.com/file/d/1_02TFxsLvbL0b0U2wM1MP8ZhRawZgBBO/view?usp=drive_link)
### Notebook: [Kaggle](https://www.kaggle.com/code/lathief137/tugas-besar-deep-learning-ra)

## Deskripsi Project
Project ini merupakan implementasi klasifikasi wajah mahasiswa yang mengambil mata kuliah Pembelajaran Mendalam RA menggunakan deep learning dengan dua arsitektur model:
- **DenseNet121** (`densenet121_facecls.pth`)
- **Swin Transformer Tiny** (`swin_tiny_facecls.pth`)

Notebook dikembangkan dan dijalankan di platform **Kaggle** untuk memanfaatkan GPU gratis.

## Cara Menjalankan Notebook

### Opsi 1: Menjalankan di Kaggle (Recommended)
1. **Login ke Kaggle**
   - Buka [kaggle.com](https://www.kaggle.com) dan login ke akun Anda

2. **Upload Notebook**
   - Klik "Code" → "New Notebook"
   - Upload file `main.ipynb` dari repository ini
   - Atau copy-paste isi notebook ke Kaggle Notebook

3. **Upload Dataset**
   - Di sidebar kanan, klik "Add Data" → "Upload"
   - Upload folder dataset dengan struktur:
     ```
     Train/
     ├── Nama_Mahasiswa_1/
     │   ├── foto1.jpg
     │   ├── foto2.jpg
     │   └── ...
     ├── Nama_Mahasiswa_2/
     │   ├── foto1.jpg
     │   └── ...
     └── ...
     ```
   - Setiap folder berisi foto-foto wajah mahasiswa yang sama
   - Format gambar yang didukung: `.jpg`, `.jpeg`, `.png`, `.webp`, `.bmp`, `.jfif`, `.heic`, `.heif`
   - Atau gunakan Kaggle Dataset yang sudah tersedia

4. **Update Path Dataset**
   - Di cell kedua notebook, sesuaikan `DATA_DIR` dengan path dataset Anda
   - Contoh: `DATA_DIR = "/kaggle/input/nama-dataset/Train"`

5. **Upload Model Files (Opsional)**
   - Jika ingin menggunakan model yang sudah ditraining, upload:
     - `densenet121_facecls.pth`
     - `swin_tiny_facecls.pth`
   - Atau gunakan Kaggle Dataset untuk menyimpan model

6. **Aktifkan GPU**
   - Klik "Settings" di sidebar kanan
   - Pilih "Accelerator" → "GPU T4 x2" atau "GPU P100"
   - Klik "Save"

7. **Install Dependencies**
   - Jalankan cell pertama untuk install package yang diperlukan
   ```python
   !pip install -q timm mediapipe pillow-heif
   ```

8. **Run All Cells**
   - Klik "Run All" atau jalankan cell satu per satu

### Opsi 2: Menjalankan di Local
1. **Clone Repository**
   ```bash
   git clone https://github.com/lateeeppp/tugas-besar-pembelajaran-mendalam.git
   cd tugas-besar-pembelajaran-mendalam
   ```

2. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download Model Files**
   - File model (`.pth`) sudah tersimpan dengan Git LFS
   - Pastikan Git LFS sudah terinstall
   ```bash
   git lfs pull
   ```

4. **Siapkan Dataset**
   - Buat folder `dataset-dl/Train/` di direktori project
   - Atur struktur dataset sesuai format:
     ```
     dataset-dl/
     └── Train/
         ├── Nama_Mahasiswa_1/
         │   ├── foto1.jpg
         │   ├── foto2.jpg
         │   └── ...
         ├── Nama_Mahasiswa_2/
         │   ├── foto1.jpg
         │   └── ...
         └── ...
     ```
   - Setiap folder berisi foto-foto wajah mahasiswa yang sama
   
5. **Update Path Dataset**
   - Di cell kedua notebook, sesuaikan `DATA_DIR`:
   ```python
   DATA_DIR = "dataset-dl/Train"  # atau path absolut
   ```

6. **Run Jupyter Notebook**
   ```bash
   jupyter notebook main.ipynb
   ```

7. **Jalankan Cells**
   - Pastikan GPU tersedia (NVIDIA CUDA) untuk performa optimal
   - Atau gunakan CPU jika tidak ada GPU

## Dataset Structure
Dataset harus mengikuti struktur folder berikut:
```
dataset-dl/
└── Train/
    ├── Nama_Mahasiswa_1/
    │   ├── foto1.jpg
    │   ├── foto2.jpg
    │   ├── foto3.png
    │   └── ...
    ├── Nama_Mahasiswa_2/
    │   ├── foto1.jpg
    │   ├── foto2.jpeg
    │   └── ...
    ├── Nama_Mahasiswa_3/
    │   └── ...
    └── ...
```

**Ketentuan Dataset:**
- Setiap **folder** merepresentasikan satu **kelas/mahasiswa**
- Nama folder = nama mahasiswa (digunakan sebagai label)
- Setiap folder berisi minimal 1 foto wajah mahasiswa tersebut
- Format gambar yang didukung: `.jpg`, `.jpeg`, `.png`, `.webp`, `.bmp`, `.jfif`, `.heic`, `.heif`
- Total dataset yang digunakan: **70 kelas** dengan **284 gambar**

## Requirements
Lihat file `requirements.txt` untuk daftar lengkap dependencies:
- PyTorch
- torchvision
- timm (untuk Swin Transformer)
- NumPy
- Matplotlib
- OpenCV
- Dan library lainnya

## File Structure
```
.
├── main.ipynb                    # Notebook utama
├── densenet121_facecls.pth      # Model DenseNet121 (LFS)
├── swin_tiny_facecls.pth        # Model Swin Transformer (LFS)
├── requirements.txt             # Dependencies
└── README.md                    # Dokumentasi
```

## Catatan
- Model files (`.pth`) disimpan menggunakan Git LFS karena ukurannya > 100MB
- Untuk performa terbaik, gunakan GPU saat training/inference
- Notebook telah dioptimasi untuk environment Kaggle

## Learning Curve

### DenseNet121

[DenseNet121](learning_curve-densenet121.png)

### Swin-Tiny
[Swin-Tiny](learning_curve-swin.png)

## Metric Performance

### DenseNet121

[DenseNet121](metric-densenet121.png)

### Swin Tiny

[Swin-Tiny](metric-swin.png)

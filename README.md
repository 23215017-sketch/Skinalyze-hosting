# Sistem Klasifikasi Penyakit Kulit dengan Deep Learning

> **🚀 Quick Start:** Lihat [CARA_INSTALL.md](CARA_INSTALL.md) untuk panduan instalasi lengkap.

## 📋 Daftar Isi
1. [Tentang Proyek](#tentang-proyek)
2. [Dataset](#dataset)
3. [Teknologi](#teknologi)
4. [Cara Menjalankan](#cara-menjalankan)
5. [Fitur](#fitur)
6. [Hasil Model](#hasil-model)

---

## 🎯 Tentang Proyek

Sistem deteksi dini penyakit kulit menggunakan **Deep Learning** . Aplikasi web dapat mengklasifikasi 9 jenis penyakit kulit dari gambar dengan akurasi 94%.

**Tujuan:**
- Membantu deteksi awal penyakit kulit
- Menyediakan akses mudah melalui web
- Memberikan informasi edukasi tentang penyakit kulit

---

## 📊 Dataset

**9 Kelas Penyakit Kulit** (Total: 9.888 gambar):

| No | Penyakit | Jumlah |
|---|----------|--------|
| 1 | Actinic keratosis | 1.137 |
| 2 | Atopic Dermatitis | 1.136 |
| 3 | Benign keratosis | 1.143 |
| 4 | Dermatofibroma | 1.142 |
| 5 | Melanocytic nevus | 1.129 |
| 6 | Melanoma | 1.125 |
| 7 | Squamous cell carcinoma | 1.132 |
| 8 | Tinea Ringworm Candidiasis | 810 |
| 9 | Vascular lesion | 1.134 |

---

## 🧠 Teknologi

**Model Deep Learning:**
- **Arsitektur**: Transfer Learning dengan MobileNetV2
- **Framework**: TensorFlow/Keras 2.15.0
- **Akurasi Validasi**: 94.94%
- **Ukuran Model**: ~9 MB

**Web Application:**
- **Backend**: Flask 3.0.0
- **Frontend**: HTML5, CSS3, JavaScript
- **Image Processing**: Pillow 10.1.0

---

## 🚀 Cara Menjalankan

### 1. Install Dependencies
```bash
pip install -r requirements.txt
```

### 2. Jalankan Aplikasi
```bash
python app.py
```

### 3. Akses di Browser
```
http://localhost:5000
```

**Spesifikasi Minimal:**
- Python 3.8+
- RAM 1 GB
- Disk 500 MB

---

## ✨ Fitur

### 1. Prediksi Penyakit Kulit
- 📸 Upload gambar (drag & drop)
- ⚡ Prediksi cepat (< 1 detik)
- 📊 Hasil dengan confidence score
- 🎯 Probabilitas semua kelas (≥10%)

### 2. Artikel Edukasi
- 📚 Informasi 9 penyakit kulit
- 💊 Panduan pengobatan & perawatan
- 🖼️ Contoh gambar dari dataset

### 3. User Experience
- 🌙 Dark mode support
- 📱 Responsive design (mobile-friendly)
- ⚡ Loading indicators
- 🎨 Modern UI/UX

---

## 📈 Hasil Model

**Performance Metrics:**
- **Overall Accuracy**: 94.94%
- **Validation Loss**: 0.1568

**Kelas Terbaik:**
- Atopic Dermatitis: 97% precision, 99% recall
- Tinea Ringworm: 98% precision, 94% recall
- Vascular lesion: 96% precision, 95% recall

---

## 📖 Cara Penggunaan

### Untuk User:
1. Buka halaman "Prediksi"
2. Upload gambar lesi kulit (JPG/PNG, max 16MB)
3. Klik "Prediksi Sekarang"
4. Lihat hasil dan confidence score

### Untuk Developer:
- **Training Model**: Buka `skin_disease_classification.ipynb`
- **Modifikasi**: Edit `app.py` atau templates di `templates/`
- **Styling**: Edit `static/css/styles.css`

---

## 📁 Struktur Proyek

```
Skinalyze/
├── app.py                          # Flask application
├── models.py                       # Database models  
├── config.py                       # Configuration
├── skin_disease_mobilenetv2_stage1.h5  # Trained model
├── class_indices.json              # Class mapping
├── requirements.txt                # Dependencies
├── CARA_INSTALL.md                 # Installation guide
├── skin_disease_classification.ipynb  # Training notebook
├── instance/
│   └── database.db                 # SQLite database
├── templates/                      # HTML templates
├── static/                         # CSS, JS, images
└── uploads/                        # User uploads

```

---

## ⚠️ Disclaimer

**Sistem ini adalah alat bantu, BUKAN pengganti konsultasi medis profesional.**

Keterbatasan:
- Hanya mendeteksi 9 jenis penyakit kulit
- Hasil bergantung pada kualitas gambar
- Mungkin terjadi kesalahan klasifikasi

**Selalu konsultasikan dengan dokter spesialis kulit untuk diagnosis yang akurat.**

---

## 📄 License

Proyek ini dibuat untuk keperluan edukasi dan penelitian.

---

**Dibuat dengan ❤️ untuk kesehatan kulit**

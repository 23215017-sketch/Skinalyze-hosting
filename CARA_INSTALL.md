# 🚀 CARA INSTALL & MENJALANKAN APLIKASI

## 📋 Persyaratan Sistem
- Python 3.8 atau lebih baru
- pip (Python package installer)
- Browser (Chrome, Firefox, Edge, dll)

---

## 🔧 LANGKAH INSTALASI

### 1️⃣ Clone Repository
```bash
git clone https://github.com/23215017-sketch/Skinalyze.git
cd Skinalyze
```

### 2️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

**Catatan:** Proses install membutuhkan waktu beberapa menit karena TensorFlow cukup besar (~500MB).

### 3️⃣ Jalankan Aplikasi
```bash
python app.py
```

Anda akan melihat output seperti ini:
```
✅ Database & Tabel berhasil dibuat!
✅ Model loaded from skin_disease_mobilenetv2_stage1.h5
✅ Class indices loaded: 9 classes
✅ Database tables created/verified

🚀 Starting Flask application...
📝 Model status: ✅ Loaded
📝 Classes: 9 classes

🌐 Server running at http://127.0.0.1:5000
📊 Admin panel: http://127.0.0.1:5000/admin (login as admin first)
```

### 4️⃣ Buka Browser
```
http://127.0.0.1:5000
```

---

## 🔐 LOGIN SEBAGAI ADMIN (SUDAH ADA!)

Database sudah berisi akun admin yang bisa langsung digunakan:

**OPSI 1: Login Langsung dengan Admin yang Sudah Ada**

1. Buka: `http://127.0.0.1:5000/login`
2. Masukkan kredensial berikut:
   - **Username**: `admin`
   - **Password**: `123456`
3. Klik "Login"
4. Klik menu "Admin" di navbar untuk akses Admin Panel

> **⚠️ Catatan Keamanan:** Setelah login pertama kali, disarankan untuk mengganti password melalui menu Profile → Edit Profile.

---

## 🆕 MEMBUAT ADMIN BARU (Opsional)

Jika Anda ingin membuat akun admin baru dari awal:

### Cara 1: Menggunakan Script
```bash
python create_admin.py
```

Ikuti instruksi dan masukkan:
- Username
- Email
- Password
- Full Name (opsional)

### Cara 2: Register lalu Ubah Role Manual

1. **Register sebagai user biasa** di `http://127.0.0.1:5000/register`
2. **Stop aplikasi** (Ctrl+C)
3. **Jalankan Python console** dan eksekusi:
   ```python
   from app import app, db, User
   with app.app_context():
       user = User.query.filter_by(username='NAMA_USERNAME_ANDA').first()
       user.role = 'admin'
       db.session.commit()
       print("✅ User sekarang admin!")
   ```
4. **Jalankan aplikasi lagi**: `python app.py`
5. **Login** dengan akun yang baru dijadikan admin

### Cara 3: Reset Database Total

Jika ingin mulai dari awal (semua data hilang):

1. **Hapus database**: 
   - Windows: `del instance\database.db`
   - Linux/Mac: `rm instance/database.db`
2. **Jalankan aplikasi**: `python app.py` (database baru dibuat otomatis)
3. **Buat admin baru**: `python create_admin.py`

---

## 📱 FITUR APLIKASI

### Untuk User Biasa:
- ✅ Register & Login
- ✅ Upload gambar kulit untuk prediksi penyakit
- ✅ Lihat hasil prediksi dengan confidence score
- ✅ History prediksi
- ✅ Edit profil
- ✅ Baca artikel penyakit kulit

### Untuk Admin:
- ✅ Dashboard dengan statistik
- ✅ Manajemen user (lihat, edit role, hapus)
- ✅ Lihat semua prediksi dari semua user
- ✅ Lihat detail user & history prediksi per user
- ✅ Statistik top predicted classes

---

## 🧠 MODEL MACHINE LEARNING

**Model**: MobileNetV2 (Transfer Learning)
- **Input Size**: 224x224 pixels (RGB)
- **Output**: 9 kelas penyakit kulit
- **Validation Accuracy**: 87.09%

**9 Kelas Penyakit:**
1. Actinic keratosis
2. Atopic Dermatitis
3. Benign keratosis
4. Dermatofibroma
5. Melanocytic nevus
6. Melanoma
7. Squamous cell carcinoma
8. Tinea Ringworm Candidiasis
9. Vascular lesion

**File Training**: Lihat `skin_disease_classification.ipynb` untuk proses training lengkap.

---

## 📂 STRUKTUR PROYEK

```
Skinalyze/
├── app.py                    # Main Flask application
├── models.py                 # Database models (User, PredictionHistory)
├── config.py                 # Configuration
├── create_admin.py           # Script untuk membuat admin
├── requirements.txt          # Dependencies
├── README.md                 # Dokumentasi proyek
├── CARA_INSTALL.md          # Dokumentasi instalasi (file ini)
│
├── skin_disease_mobilenetv2_stage1.h5  # Model ML terlatih
├── class_indices.json        # Mapping kelas
├── skin_disease_classification.ipynb   # Notebook training
│
├── instance/
│   └── database.db          # SQLite database (sudah ada admin!)
│
├── templates/               # HTML templates
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── predict.html
│   ├── artikel.html
│   ├── profile.html
│   └── admin/              # Admin panel templates
│
└── static/                  # Static files
    ├── css/
    ├── js/
    └── dataset/            # Dataset images untuk contoh
```

---

## 🐛 TROUBLESHOOTING

### Error: "No module named 'tensorflow'"
```bash
pip install tensorflow==2.15.0
```

### Error: "No module named 'flask'"
```bash
pip install -r requirements.txt
```

### Error: Model tidak ditemukan
- Pastikan file `skin_disease_mobilenetv2_stage1.h5` ada di folder root
- Ukuran file ~9.5 MB

### Server tidak jalan pada port 5000
- Ubah port di `app.py` baris terakhir:
  ```python
  app.run(debug=True, host='0.0.0.0', port=8000)  # Ubah port
  ```

### Lupa password admin
- Gunakan Cara 3 di bagian "Membuat Admin Baru" (reset database)

---

## 💡 TIPS

1. **Gunakan Virtual Environment** (opsional tapi direkomendasikan):
   ```bash
   python -m venv venv
   
   # Windows
   venv\Scripts\activate
   
   # Linux/Mac
   source venv/bin/activate
   
   pip install -r requirements.txt
   ```

2. **Backup Database** sebelum reset:
   ```bash
   # Windows
   copy instance\database.db instance\database_backup.db
   
   # Linux/Mac
   cp instance/database.db instance/database_backup.db
   ```

3. **Lihat Log Error**: Jika ada error, lihat output di terminal untuk detail error.

---

## 📞 KONTAK

Jika ada pertanyaan atau masalah, hubungi developer proyek ini.

---

## 📄 LISENSI

Proyek ini dibuat untuk keperluan akademik.

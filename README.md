# MoneyMate: Capstone Project CC25-CF345

![MoneyMate Banner](https://via.placeholder.com/1200x300/2E7D32/FFFFFF?text=MoneyMate:%20AI-Powered%20Financial%20Guidance)

**Sistem Rekomendasi Finansial Berbasis Konten untuk Meningkatkan Literasi dan Kesehatan Keuangan Pengguna.**

---

## 📜 Daftar Isi
- [Latar Belakang](#-latar-belakang)
- [Fitur Utama](#-fitur-utama)
- [Arsitektur Sistem](#-arsitektur-sistem)
- [Tumpukan Teknologi](#-tumpukan-teknologi)
- [Arsitektur Model Machine Learning](#-arsitektur-model-machine-learning)
- [Hasil & Performa Model](#-hasil--performa-model)
- [Demo Aplikasi](#-demo-aplikasi)
- [Panduan Instalasi & Replikasi](#-panduan-instalasi--replikasi)
- [Tim Pengembang](#-tim-pengembang)
- [Lisensi](#-lisensi)

---

## 🌳 Latar Belakang

Di era digital, banyak individu, terutama dari kalangan mahasiswa hingga keluarga muda, menghadapi kesulitan dalam mengelola keuangan pribadi secara efektif. Kurangnya pemahaman tentang kebiasaan pengeluaran dan minimnya panduan finansial yang personal menjadi penghalang utama untuk mencapai kesehatan finansial. MoneyMate lahir dari kebutuhan ini, dengan tujuan untuk menyediakan sebuah platform cerdas yang tidak hanya melacak pengeluaran, tetapi juga memberikan wawasan dan rekomendasi yang dapat ditindaklanjuti, yang disesuaikan secara unik untuk setiap pengguna. Proyek ini bertujuan untuk menjembatani kesenjangan tersebut dengan memanfaatkan kekuatan *machine learning* untuk memberikan panduan finansial yang proaktif dan mudah diakses.

---

## ✨ Fitur Utama

- **Analisis Pola Pengeluaran:** Sistem secara otomatis mengidentifikasi kebiasaan belanja pengguna.
- **Klasifikasi Transaksi Cerdas:** Mengkategorikan setiap transaksi secara otomatis menggunakan model ML.
- **Skor Kesehatan Finansial:** Memberikan skor dinamis (0-100) untuk mengukur kesehatan finansial pengguna.
- **Rekomendasi Personal:** Memberikan saran finansial yang relevan berdasarkan profil, kebiasaan, dan skor kesehatan finansial pengguna.
- **Pencarian Pengguna Serupa:** Menemukan pengguna dengan profil finansial yang "mirip" untuk potensi wawasan komparatif.

---

## 🏗️ Arsitektur Sistem

MoneyMate dibangun di atas arsitektur modern yang memisahkan antara antarmuka pengguna (Frontend) dan logika pemrosesan data (Backend), yang berkomunikasi melalui API.

`[Aplikasi Web Pengguna (Vite.js)]` ↔️ `API (JSON)` ↔️ `[Server & Model ML (FastAPI)]`

- **Frontend (Client-Side):** Bertanggung jawab untuk semua interaksi dan visualisasi yang dilihat oleh pengguna.
- **Backend (Server-Side):** Bertanggung jawab untuk memproses logika bisnis, menjalankan model ML, dan mengelola data.

---

## 💻 Tumpukan Teknologi

| Komponen | Teknologi yang Digunakan |
| :--- | :--- |
| **Frontend** | HTML, CSS, JavaScript (Pure), Vite.js (Build Tool) |
| **Backend** | Python, FastAPI (Web Framework), Uvicorn (ASGI Server) |
| **Machine Learning**| Pandas, NumPy, Scikit-learn |
| **Deployment** | GitHub Actions |

---

## 🧠 Arsitektur Model Machine Learning

Sistem rekomendasi kami bukanlah model tunggal, melainkan sebuah pipeline cerdas yang terdiri dari 3 komponen utama:

1.  **Model Profiling & Feature Engineering:**
    - **Tugas:** Mengubah data transaksi mentah menjadi profil pengguna yang terukur (vektor fitur).
    - **Proses:** Melakukan agregasi data untuk menghitung metrik seperti rata-rata transaksi, frekuensi belanja, konsistensi (`spending_cv`), hingga persentase pengeluaran per kategori.

2.  **Model User Similarity Engine:**
    - **Tugas:** Menemukan pengguna dengan perilaku finansial yang "mirip".
    - **Proses:** Menggunakan **PCA** untuk meringkas fitur (menangkap **92.1%** informasi) dan **Cosine Similarity** untuk mengukur kedekatan antar pengguna.

3.  **Model Recommendation Scoring Engine:**
    - **Tugas:** Memberi peringkat pada semua tips finansial dan memilih 5 terbaik.
    - **Proses:** Menggunakan sistem skor berbasis aturan (heuristik) yang mempertimbangkan kecocokan profil, relevansi kategori pengeluaran, dan skor kesehatan finansial pengguna.

---

## 📈 Hasil & Performa Model

Model kami telah divalidasi secara kuantitatif dan menunjukkan performa yang sangat baik, memastikan rekomendasi yang dihasilkan berkualitas tinggi.

- ✅ **Personalisasi Terukur & Konsisten**:
  - *Profile Alignment Score* mencapai **100%**, membuktikan setiap rekomendasi selaras dengan arketipe profil pengguna.
- ✅ **Keragaman & Cakupan yang Tinggi**:
  - *Simpson Diversity* **0.876** (dari maks 1.0), menunjukkan rekomendasi yang sangat beragam.
  - *Category Coverage* **91.7%**, membuktikan sistem mampu menyarankan hampir semua jenis topik finansial.

---

## 🎥 Demo Aplikasi

*[Sisipkan screenshot atau GIF dari aplikasi web Anda di sini untuk menunjukkan fitur-fitur utama seperti dasbor, halaman rekomendasi, dan skor kesehatan finansial.]*

---

## 🚀 Panduan Instalasi & Replikasi

Berikut adalah langkah-langkah untuk menjalankan proyek ini di lingkungan lokal.

### Prasyarat
- [Git](https://git-scm.com/)
- [Python](https://www.python.org/downloads/) (versi 3.9+)
- [Node.js](https://nodejs.org/) dan npm (versi 18+)

### 1. Kloning Repositori

git clone [https://github.com/MoneyMate-CC25-CF345/Capstone-Project.git](https://github.com/MoneyMate-CC25-CF345/Capstone-Project.git)
cd Capstone-Project
### 2. Setup & Menjalankan Backend (Model ML)

# Buat dan aktifkan virtual environment
python -m venv venv
# Windows:
.\venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Instal semua dependensi Python
pip install -r moneymate_assets/requirements.txt

# Jalankan server API dengan Uvicorn
uvicorn main:app --reload
✨ Backend API sekarang berjalan di http://127.0.0.1:8000.

### 3. Setup & Menjalankan Frontend
(Catatan: Pastikan Anda berada di direktori utama proyek, lalu masuk ke folder frontend)


# Masuk ke direktori frontend (sesuaikan nama folder jika berbeda)
cd path/to/your/frontend-folder

# Instal semua dependensi JavaScript
npm install

# Jalankan server pengembangan Vite
npm run dev
✨ Aplikasi web sekarang dapat diakses di http://localhost:5173 (atau alamat lain yang ditampilkan di terminal).

👥 Tim Pengembang
Proyek ini merupakan hasil kolaborasi dari tim CC25-CF345.

Peran	            Anggota	                      Universitas
Machine Learning	Sitti Saenab	            Politeknik Negeri Ujung Pandang
Machine Learning	Ade Nurchalisa	            Universitas Islam Negeri Alauddin Makassar
Machine Learning	Muhammad Fadel Hamka	    Universitas Islam Negeri Alauddin Makassar
FEBE	            Muh. Anwar Syafriawan	    Universitas Islam Negeri Alauddin Makassar
FEBE	            Ahmad Syahid	            Universitas Islam Negeri Alauddin Makassar
FEBE	            Firdania Sasmita Sari	    Politeknik Negeri Ujung Pandang

📄 Lisensi
Proyek ini dilisensikan di bawah Lisensi MIT.
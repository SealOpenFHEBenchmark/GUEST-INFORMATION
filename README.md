# Benchmark Kinerja FHE: OpenFHE vs. Microsoft SEAL pada Raspberry Pi 5

Organizations ini berisi hasil dan analisis dari studi perbandingan kinerja antara dua *library* Fully Homomorphic Encryption (FHE) terkemuka: **OpenFHE** dan **Microsoft SEAL**.

Seluruh *benchmark* dijalankan pada perangkat **Raspberry Pi 5** untuk mengevaluasi efisiensi dan skalabilitas kedua *library* pada perangkat *edge/IoT*.

## 📊 Tentang Proyek Ini

Tujuan utama dari proyek ini adalah untuk mengukur dan membandingkan kinerja *head-to-head* dari OpenFHE dan Microsoft SEAL dalam menjalankan protokol telemetri IoT yang spesifik.

Perbandingan ini berfokus pada tiga algoritma inti yang digunakan dalam protokol:

1.  **Algoritma 1: RoundInit (Inisialisasi & Enkripsi)**
    * Mengukur *overhead* pembuatan *mask* acak dan enkripsi awal.
2.  **Algoritma 2: NodeProcess (Operasi Homomorfik)**
    * Mengukur kinerja inti FHE, yaitu penambahan *ciphertext-plaintext* (`EvalAdd` vs `add_plain_inplace`) secara berulang. Ini adalah metrik skalabilitas utama.
3.  **Algoritma 3: RoundVerify (Dekripsi & Verifikasi)**
    * Mengukur *overhead* dekripsi, *unmasking*, dan verifikasi data.

Parameter kriptografi (BFV, N=8192, q=65537) dijaga tetap identik di kedua *library* untuk memastikan perbandingan yang adil.

## 🛠️ Teknologi yang Digunakan

* **Bahasa:** C++17
* **Library FHE:**
    * OpenFHE
    * Microsoft SEAL
* **Sistem Build:** CMake
* **Hardware:** Raspberry Pi 5 (ARM64)
* **OS:** Raspberry Pi OS (Debian 12 Bookworm)

## 📈 Hasil (Ringkasan)

Analisis data *benchmark* (dijalankan rata-rata 5 kali untuk jumlah node `n` dari 16 hingga 4096) menunjukkan temuan sebagai berikut:

* **Overhead (Alg 1 & 3):** OpenFHE secara konsisten menunjukkan kinerja yang lebih cepat untuk operasi non-homomorfik seperti enkripsi awal dan dekripsi/verifikasi.
* **Kinerja Homomorfik (Alg 2):** Microsoft SEAL secara signifikan lebih unggul dalam kinerja dan skalabilitas untuk operasi `NodeProcess`. Pada beban kerja 4096 node, SEAL terbukti **~2.5x lebih cepat** daripada OpenFHE.

---

## 🔒 Akses Kode Sumber

File kode sumber lengkap (`IoT_FHE.cpp`, `benchmark_seal.cpp`, dan `CMakeLists.txt`) untuk *benchmark* ini tidak tersedia secara publik.

Untuk mendapatkan akses ke kodingan lengkap untuk tujuan akademik, penelitian, atau kolaborasi, silakan hubungi kontak di bawah ini:

* **Nama:** Ardea Himawan Nugroho
* **No. Telepon/WA:** 085600009732
* **Email:** ardeahnugroho@gmail.com

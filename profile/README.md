# TakarSaku (Tata Kelola Anggaran & Uang Saku)

### Sistem Pengelolaan & Evaluasi Uang Saku Bulanan Berbasis Web

![PHP](https://img.shields.io/badge/PHP_8-777BB4?style=for-the-badge&logo=php&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

Selamat datang di organisasi repositori resmi **TakarSaku**, proyek aplikasi web pengelolaan keuangan mahasiswa yang dikembangkan untuk membantu pencatatan anggaran, pemantauan realisasi pengeluaran, dan simulasi dana darurat secara terstruktur setiap bulan.

---

## Ringkasan Project

Mahasiswa sering menghadapi kendala dalam mengendalikan pengeluaran bulanan lintas kebutuhan pokok, akademik, penunjang, hingga gaya hidup. Pencatatan manual yang tidak terukur membuat sisa anggaran sulit dipantau dan kerap memicu _overbudget_ sebelum akhir bulan.

**TakarSaku** hadir sebagai ruang kerja finansial berbasis web yang ringkas dan aman menggunakan PHP 8. Aplikasi ini memisahkan tampilan ringkasan eksekutif dari tabel rincian alokasi, melengkapi pengguna dengan simulasi tabungan darurat (`0%`–`20%`), evaluasi status pos otomatis (`Aman`, `Waspada`, `Overbudget`), serta mekanisme autentikasi sesi dan preferensi tema berbasis _cookie_.

---

## Anggota Tim

| Nama                                     | NPM        | Status |
| :--------------------------------------- | :--------- | :----- |
| **Gihan Dimas Ardiyan**                  | 2240501145 | Aktif  |
| **Alin Rahma Herdiyanti**                | 232050109  | Aktif  |
| **Rizky Aulia Zahra**                    | 2330501103 | Aktif  |
| **Muhammad Hatta Mabarun Khalifatullah** | 2340501139 | Aktif  |

---

## Fitur Utama & Solusi Teknologi

1. **Autentikasi & Manajemen Sesi Aman**
   Menggunakan `password_hash()` dan `password_verify()` untuk verifikasi kredensial, pembaruan ID sesi via `session_regenerate_id(true)` saat login, proteksi halaman dengan `requireLogin()`, serta konfigurasi _cookie_ sesi `HttpOnly` dan `SameSite=Lax`.
2. **Keamanan Formulir & Keluaran (CSRF & XSS)**
   Seluruh aksi `POST` (login, logout, tambah pos, dan ubah tema) dilindungi token CSRF yang diverifikasi dengan `hash_equals()`, sedangkan seluruh data pengguna disanitasi menggunakan `htmlspecialchars()` sebelum dirender ke HTML.
3. **Evaluasi Anggaran & Simulasi Dana Darurat**
   Terintegrasi langsung dengan modul logika `pertemuan10/function.php` (`olahRincianPos()`) untuk menghitung persentase serapan, potongan dana cadangan (`0%`–`20%`), sisa efektif, serta klasifikasi status anggaran secara otomatis.
4. **Validasi Sisi Server, Input Array & Pola PRG**
   Formulir penambahan pos memproses _input array_ `metode_bayar[]`, menjalankan validasi sisi server dengan galat spesifik per _field_ dan _sticky form_, serta menerapkan pola _Post-Redirect-Get_ (PRG) lengkap dengan _flash message_ satu kali tampil.
5. **Preferensi Tema Cookie & Antarmuka Editorial Forest**
   Menyimpan pilihan _Light Mode_ dan _Dark Mode_ dalam _cookie_ `takarsaku_theme` (masa berlaku 30 hari dengan validasi _whitelist_) di atas tata letak responsif yang dikalibrasi khusus untuk layar laptop maupun perangkat seluler.

---

## Tech Stack & Penyelesaian Proyek

Pengembangan tahap **Pertemuan 10–11** telah selesai **100%** mencakup fondasi logika perhitungan anggaran hingga integrasi autentikasi, keamanan, dan antarmuka penuh.

### Daftar Capaian Fitur

- **Autentikasi & Sesi:** Halaman login _split-screen_, proteksi akses halaman, regenerasi ID sesi, dan logout aman via `POST`.
- **Keamanan Web:** Perlindungan XSS pada seluruh keluaran serta verifikasi token CSRF pada setiap pengiriman formulir.
- **Pengolahan Data (`GET` & `POST`):** Filter pencarian dan kategori via `GET`, penambahan pos via `POST`, pengolahan _array_ `metode_bayar[]`, validasi _server-side_, _sticky form_, dan PRG + _flash message_.
- **Cookie & Personalisasi:** Penyimpanan preferensi tema terang/gelap yang persisten antar-muat ulang halaman.
- **UI/UX & Responsivitas:** Sistem desain _Editorial Forest_ , pemisahan tab `Ringkasan` dan `Rincian Alokasi`, serta pratinjau status langsung (_live preview_) pada form tambah pos.

---

## Tautan Repository

Silakan akses komponen repositori proyek kami melalui tautan berikut:

- **[Repositori Utama Proyek](https://github.com/TakarSaku)**
- **[Repositori Pertemuan 10](https://github.com/TakarSaku/project-akhir-pemwe/tree/main/pertemuan10)**
- **[Repositori Pertemuan 11](https://github.com/TakarSaku/project-akhir-pemwe/tree/main/pertemuan%2011)**

---

## Antarmuka Aplikasi

### Halaman Masuk (_Login_)

_Tata letak split-screen berbingkai bezel dengan panel editorial di sisi kiri serta formulir masuk terpusat lengkap dengan tombol tampilkan/sembunyikan kata sandi dan umpan balik validasi._

### Dashboard — Tab Ringkasan (_Overview_)

_Menampilkan saldo aktual, kontrol cepat simulasi dana darurat (`0%`–`20%`), kartu sisa efektif, grafik proporsi serapan kategori, progres realisasi per kategori, serta daftar pos yang perlu perhatian._

### Dashboard — Tab Rincian Alokasi

_Ruang kerja tabel lengkap dengan bilah filter `GET` terintegrasi (pencarian kode/nama pos, filter kategori, dan simulasi cadangan), tag metode pembayaran, bar progres, serta baris rekapitulasi total._

### Formulir Tambah Pos Pengeluaran

_Antarmuka dua kolom dengan pilihan tile metode pembayaran interaktif, validasi sisi server, kartu pratinjau status otomatis saat mengetik, dan ringkasan kondisi sesi aktif._

---

## Keunggulan & Rencana Pengembangan

- **Keunggulan Saat Ini:** Ringan tanpa ketergantungan _framework_ eksternal, aman di level dasar aplikasi web (CSRF, XSS, _session regeneration_), terstruktur modular, dan tampilan rapi lintas ukuran layar.
- **Keterbatasan Saat Ini:** Penyimpanan data pos pengeluaran masih berbasis `$_SESSION` PHP sehingga data baru kembali ke _dataset_ awal saat sesi berakhir.
- **Rencana Pengembangan:** Migrasi penyimpanan ke basis data relasional (MySQL/PDO), penambahan fitur ubah dan hapus pos (_CRUD_ penuh), autentikasi registrasi pengguna, serta ekspor laporan bulanan ke PDF/CSV.

---

<p align="center">
  <b>TakarSaku © 2026 — Sistem Pengelolaan Uang Saku Bulanan</b><br>
  Dikembangkan bersama oleh Tim Pengembang TakarSaku
</p>

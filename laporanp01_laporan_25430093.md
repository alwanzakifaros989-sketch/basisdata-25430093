# Laporan Praktikum Basis Data - Pertemuan 1

* **Nama:** Alwan Zaki Faros
* **NIM:** 25430093
* **Kelas:** S1 Ilmu Komputer
* **Tema Proyek:** Akademik (`akad_093`)

---

## 1. Berkas Wajib Pertemuan 1

Saya telah menyiapkan dan mengunggah tiga berkas utama ke repositori GitHub `basisdata-25430093`:
* `p01_lingkungan_25430093.sql`: Berkas skrip SQL untuk membuat basis data proyek `akad_093` serta mengatur hak akses pengguna MariaDB.
* `README.md`: Berkas penjelasan profil proyek sistem informasi akademik dan batasan layanannya.
* `.gitignore`: Berkas konfigurasikan untuk mengabaikan berkas sensitif seperti `*.env` dan daftar kredensial agar tidak terunggah ke repositori publik.

---

## 2. Analisis Wajib

### A. Titik Analisis 1–4
1. **Titik Analisis 1 (Prinsip Hak Akses Terendah):**  
   Penggunaan akun khusus `mhs_093` dan `dev_093` menggantikan `root` bertujuan untuk membatasi wewenang pengguna sesuai kebutuhan saja. Hal ini mencegah kerusakan struktur basis data akibat kesalahan eksekusi perintah yang tidak disengaja.

2. **Titik Analisis 2 (Pengaturan SQL Mode Ketat):**  
   Penerapan `sql_mode` secara ketat berfungsi menjaga validitas data. Sistem MariaDB akan membatalkan transaksi dan menampilkan galat secara langsung jika data yang dimasukkan tidak sesuai tipe atau melebihi batas kolom.

3. **Titik Analisis 3 (Pemisahan Akun Mahasiswa dan Pengembang):**  
   Akun `mhs_093` difokuskan untuk manipulasi data operasional (DML), sedangkan `dev_093` memegang izin pengubahan struktur tabel (DDL) pada proyek `akad_093`. Pemisahan ini menjaga skema basis data utama tetap stabil.

4. **Titik Analisis 4 (Keamanan phpMyAdmin Mode Cookie):**  
   Autentikasi mode `cookie` mewajibkan pengguna memasukkan nama pengguna dan kata sandi pada formulir setiap kali sesi dimulai. Cara ini mencegah akses asing yang sering terjadi pada mode `config` akibat kata sandi tersimpan langsung di file konfigurasi.

---

### B. Perbedaan Kode Galat MySQL (1044, 1045, 1142)
* **Error 1045 (`Access Denied - Authentication`):**  
  Terjadi saat proses masuk (*login*) awal gagal karena nama pengguna, kata sandi, atau lokasi *host* yang dimasukkan salah.
* **Error 1044 (`Access Denied - Database`):**  
  Terjadi ketika pengguna berhasil masuk, tetapi tidak memiliki izin untuk memilih atau membuka suatu basis data (misalnya saat `mhs_093` menjalankan `USE mysql;`).
* **Error 1142 (`Command Denied - Table`):**  
  Terjadi saat pengguna bisa membuka suatu basis data, namun dilarang menjalankan perintah tertentu (seperti instruksi `CREATE` atau `DROP`).

---

## 3. Bukti Tangkapan Layar

### A. Pemeriksaan Versi MariaDB dan User
![Pemeriksaan Versi dan Pengguna](p01_versi_user_sqlmode.png)

### B. Tampilan `SHOW DATABASES` pada Akun `mhs_093` dan `dev_093`
![SHOW DATABASES mhs_093 dan dev_093](p01_show_databases.png)

### C. Pengujian Galat 1044 dan 1142
![Bukti Galat 1044 dan 1142](p01_galat_1044_1142.png)

### D. Halaman Masuk phpMyAdmin Mode Cookie
![phpMyAdmin Mode Cookie](p01_phpmyadmin_cookie.png)

### E. Bukti Inisialisasi Git Push Pertama
![Git Push Pertama](p01_git_push_pertama.png)
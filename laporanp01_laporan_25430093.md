# Laporan Praktikum Basis Data - Pertemuan 1

* **Nama:** Alwan Zaki Faros
* **NIM:** 25430093
* **Kelas:** S1 Ilmu Komputer
* **Tema Proyek:** Akademik (`akad_093`)

---

## 1. Berkas Wajib Pertemuan 1
Seluruh berkas utama pendukung praktikum telah dikonfigurasi dan berhasil di-push ke repositori GitHub `basisdata-25430093`:
1. `p01_lingkungan_25430093.sql` (Skrip SQL untukpembuatan basis data `akad_093` dan pengaturan pengguna MariaDB)
2. `README.md` (Berisi identitas proyek akademik `akad_093` beserta lingkup layanannya)
3. `.gitignore` (Pengecualian berkas kredensial seperti `*.env` dan `kredensial*.txt`)

---

## 2. Analisis Wajib

### A. Titik Analisis 1–4
1. **Titik Analisis 1 (Prinsip Hak Akses Terendah / Least Privilege):**
   Penggunaan akun khusus seperti `mhs_093` dan `dev_093` dibuat untuk menghindari penggunaan akun `root` secara terus-menerus. Hal ini bertujuan membatasi hak akses sesuai kebutuhan agar pengguna tidak bisa mengubah atau menghapus basis data yang bukan kewenangannya.

2. **Titik Analisis 2 (Pentingnya Mode Ketat SQL Mode):**
   Pengaturan `sql_mode` secara ketat memastikan integritas data terjamin. Jika ada data yang dimasukkan tidak sesuai tipe atau melebihi kapasitas kolom, sistem MariaDB akan menolak perintah tersebut dengan galat alih-alih memotong data secara otomatis.

3. **Titik Analisis 3 (Pemisahan Hak Akses Mahasiswa dan Pengembang):**
   Akun `mhs_093` hanya diberikan akses operasional pada basis data latihan/praktikum, sedangkan akun `dev_093` diberi wewenang khusus mengelola basis data proyek `akad_093`. Pemisahan ini mencegah terjadinya konflik instruksi dan menjaga kerahasiaan data proyek.

4. **Titik Analisis 4 (Keamanan Autentikasi phpMyAdmin Mode Cookie):**
   Penggunaan mode `cookie` wewajibkan pengguna memasukkan *username* dan *password* setiap kali sesi dimulai. Mode ini mencegah akses tanpa izin yang rawan terjadi jika menggunakan mode `config` (kata sandi tersimpan langsung di file konfigurasi).

---

### B. Perbedaan Kode Galat (Error) MySQL: 1044, 1045, dan 1142
* **Error 1045 (`Access denied for user`):**  
  Galat terjadi saat proses **login/autentikasi awal**, biasanya karena nama pengguna, kata sandi, atau host yang dimasukkan salah.
* **Error 1044 (`Access denied for user to database`):**  
  Galat terjadi saat pengguna yang sudah berhasil masuk mencoba **mengakses basis data** yang tidak terdaftar dalam daftar hak aksinya (misal: `USE mysql;` atau `USE kopma_093;`).
* **Error 1142 (`Command denied to user for table`):**  
  Galat terjadi saat pengguna memiliki akses ke suatu basis data, tetapi **dilarang menjalankan perintah/instruksi tertentu** (seperti perintah `CREATE`, `DROP`, atau `DELETE`).

---

## 3. Bukti Tangkapan Layar (Bukti Eksekusi Terminal)

### A. Pemeriksaan Versi MariaDB dan Informasi Pengguna
![Pemeriksaan Versi dan Pengguna](p01_versi_user_sqlmode.png)

### B. Hasil Pembuatan Basis Data dan Hak Akses `mhs_093` / `dev_093`
![SHOW DATABASES dan Hak Akses User](p01_show_databases.png)

### C. Pengujian Galat Akses (Error 1044 & 1142)
![Bukti Galat Akses](p01_galat_1044_1142.png)

### D. Tampilan Antarmuka phpMyAdmin Mode Cookie
![phpMyAdmin Mode Cookie](p01_phpmyadmin_cookie.png)

### E. Inisialisasi dan Inisial Push ke Repositori GitHub
![Git Push Pertama](p01_git_push_pertama.png)
# Laporan Pertemuan 6 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Praktikum 6.1 — Mengenali Bash dan Menyiapkan Workspace
1. Lihat shell login dan shell aktif saat ini:

   <img src="Screenshot 2026-04-14 195422.png" width="70%"> 

2. Lihat proses shell yang sedang berjalan:

   <img src="Screenshot 2026-04-14 195503.png" width="70%"> 

3. Buat workspace praktikum:

   <img src="Screenshot 2026-04-14 200341.png" width="70%"> 

4. Buat beberapa file contoh yang akan dipakai pada praktikum berikutnya:

   <img src="Screenshot 2026-04-14 201449.png" width="70%"> 

## Praktikum 6.2 — Membuat Ringkasan Sesi Terminal
1. Masuk ke workspace praktikum:

   cd ~/ praktikum - os / week07 - bash

2. Simpan informasi sesi terminal ke file laporan:

   <img src="Screenshot 2026-04-14 202303.png" width="70%"> 

3. Verifikasi isi file laporan:

   <img src="Screenshot 2026-04-14 202346.png" width="70%"> 

## Praktikum 6.3 — Menambahkan Konfigurasi Aman pada .bashrc
1. Lihat file konfigurasi Bash pada home directory:

   <img src="Screenshot 2026-04-14 202505.png" width="70%"> 

2. Buat backup .bashrc:

   <img src="Screenshot 2026-04-14 202543.png" width="70%"> 

3. Tambahkan blok konfigurasi praktikum:

   <img src="Screenshot 2026-04-14 202852.png" width="70%"> 

4. Terapkan konfigurasi tanpa logout:

   <img src="Screenshot 2026-04-14 203323.png" width="70%"> 

## Praktikum 6.4 — Menyiapkan .bash_profile untuk Shell Login
1. Backup .bash_profile jika sudah ada:

   <img src="Screenshot 2026-04-14 203643.png" width="70%"> 

2. Tambahkan konfigurasi login shell:

   <img src="Screenshot 2026-04-14 203832.png" width="70%"> 

3. Uji dengan membuka login shell baru:

   <img src="Screenshot 2026-04-14 203940.png" width="70%"> 

## Praktikum 6.5 — Membedakan Variabel Shell dan Environment Variable
1. Buat variabel lokal:

   <img src="Screenshot 2026-04-14 204041.png" width="70%"> 

2. Buka subshell dan cek apakah variabel masih ada:

   <img src="Screenshot 2026-04-14 204121.png" width="70%"> 

3. Sekarang ubah menjadi environment variable:

   <img src="Screenshot 2026-04-14 204235.png" width="70%"> 

4. Lihat isi PATH dan lokasi beberapa perintah:

   <img src="Screenshot 2026-04-14 204323.png" width="70%"> 

## Praktikum 6.6 — Menambahkan Direktori Script Pribadi ke PATH
1. Pastikan direktori bin praktikum tersedia:

   <img src="Screenshot 2026-04-14 205750.png" width="70%"> 

2. Tambahkan direktori tersebut ke PATH melalui .bashrc:

   <img src="Screenshot 2026-04-14 205817.png" width="70%"> 

3. Buat script ringkasan sistem:

   <img src="Screenshot 2026-04-14 210217.png" width="70%"> 

4. Jalankan script dari direktori yang berbeda:

   <img src="Screenshot 2026-04-14 210253.png" width="70%"> 

## Praktikum 6.7 — Membuat Alias Produktivitas Dasar
1. Tambahkan alias ke .bashrc:

   <img src="Screenshot 2026-04-14 210506.png" width="70%">

2. Uji alias:

   <img src="Screenshot 2026-04-14 210613.png" width="70%">

## Praktikum 6.8 — Membuat Fungsi Backup Konfigurasi
1. Siapkan file konfigurasi contoh:

   <img src="Screenshot 2026-04-14 210806.png" width="70%">

2. Tambahkan fungsi ke .bashrc:

   <img src="Screenshot 2026-04-14 214531.png" width="70%">

3. Uji fungsi:

   <img src="Screenshot 2026-04-14 214754.png" width="70%">

## Praktikum 6.9 — Menggunakan Completion Dasar dan Melihat History
1. Pastikan file contoh tersedia:

   <img src="Screenshot 2026-04-14 214917.png" width="70%">

2. Uji completion file:
   - Ketik cat lap lalu tekan Tab dua kali.
   - Amati daftar file yang memiliki prefix lap.
   - Ketik lebih spesifik, misalnya cat laporan-h lalu tekan Tab

   <img src="Screenshot 2026-04-14 215413.png" width="70%">

3. Jalankan beberapa perintah sederhana:

   <img src="Screenshot 2026-04-14 215500.png" width="70%">

## Praktikum 6.10 — Menelusuri Perintah Diagnostik dengan History
1. Jalankan beberapa perintah diagnostik:

   <img src="Screenshot 2026-04-14 215546.png" width="70%">

2. Cari ulang perintah diagnostik dari history:

   <img src="Screenshot 2026-04-14 215629.png" width="70%">

3. Jalankan ulang salah satu perintah berdasarkan nomor history:

   <img src="Screenshot 2026-04-14 215801.png" width="70%">

4. Simpan potongan history ke file dokumentasi:

   <img src="Screenshot 2026-04-14 220120.png" width="70%">

## Praktikum 6.11 — Mencoba Wildcard Dasar
1. Masuk ke direktori sampel:

   <img src="Screenshot 2026-04-14 221020.png" width="70%">

2. Coba beberapa pola wildcard:

   <img src="Screenshot 2026-04-14 221206.png" width="70%">

3. Coba beberapa ekspansi lain:

   <img src="Screenshot 2026-04-14 221347.png" width="70%">

## Praktikum 6.12 — Mengarsipkan Banyak Log Sekaligus
1. Siapkan file log tambahan:

   <img src="Screenshot 2026-04-14 221455.png" width="70%">

2. Preview file yang akan diproses:

   <img src="Screenshot 2026-04-14 221526.png" width="70%">

3. Pindahkan semua file log ke folder arsip:

   <img src="Screenshot 2026-04-14 221617.png" width="70%">

4. Kompres folder arsip:

   <img src="Screenshot 2026-04-14 221724.png" width="70%">

## Praktikum 6.13 — Membedakan Single Quote, Double Quote, dan Escape
1. Uji single quote dan double quote:

   <img src="Screenshot 2026-04-14 221828.png" width="70%">

2. Uji escape karakter spasi:

   <img src="Screenshot 2026-04-14 222121.png" width="70%">

3. Uji akses file yang sama dengan double quote:

   <img src="Screenshot 2026-04-14 222150.png" width="70%">

## Praktikum 6.14 — Menangani File dengan Nama Sulit Secara Aman
1. Pastikan file target tersedia:

   <img src="Screenshot 2026-04-14 222252.png" width="70%">

2. Salin file dengan nama kompleks ke folder backup:

   <img src="Screenshot 2026-04-14 223400.png" width="70%">

3. Gunakan variabel untuk memproses path dengan aman:

   <img src="Screenshot 2026-04-14 222825.png" width="70%">

4. Tampilkan daftar file hasil backup:

   <img src="Screenshot 2026-04-14 222957.png" width="70%">

## Tugas Praktikum
### Tugas Praktikum 1 — Toolkit Bash Administrator Pribadi
1. Tambahkan konfigurasi pada .bashrc untuk:
   • menambahkan direktori bin pribadi ke PATH,
   • membuat minimal 2 alias yang membantu kerja harian,
   • membuat minimal 1 fungsi shell yang berguna untuk administrasi.
2. Pastikan konfigurasi tersebut aktif kembali saat membuka shell login.
3. Buat satu script sederhana di direktori bin pribadi, misalnya script untuk menampilkan ringkasan sistem.
4. Uji dari direktori yang berbeda untuk memastikan script dapat dipanggil tanpa menuliskan path lengkap.
5. Simpan bukti pengujian ke file toolkit-bash-report.txt.

   <img src="Screenshot 2026-04-14 230850.png" width="70%">
   <img src="Screenshot 2026-04-14 231551.png" width="70%">
   <img src="Screenshot 2026-04-14 232111.png" width="70%">

### Tugas Praktikum 2 — Audit File Konfigurasi dan Logging Aman
1. Buat file laporan bernama audit-konfigurasi-$(date +%F).txt.
2. Cari file *.conf di dalam /etc dan simpan hasilnya ke file laporan.
3. Catat jumlah total file konfigurasi yang ditemukan.
4. Jika ada pesan error, simpan ke file terpisah, misalnya audit-error.log.
5. Tampilkan isi laporan ke terminal dan sekaligus simpan menggunakan tee.
6. Tambahkan ringkasan singkat 3–5 baris yang menjelaskan mengapa pemisahan stdout dan stderr penting dalam audit sistem.

   <img src="Screenshot 2026-04-14 233229.png" width="70%">
   <img src="Screenshot 2026-04-14 233844.png" width="70%">
   <img src="Screenshot 2026-04-14 234255.png" width="70%">

### Tugas Praktikum 3 — Mini Health Check Harian Server
1. Buat script Bash bernama daily-healthcheck pada direktori bin pribadi.
2. Script minimal harus menampilkan:
   • tanggal dan waktu,
   • hostname,
   • user aktif,
   • shell aktif,
   • uptime,
   • penggunaan memori,
   • penggunaan filesystem root,
   • 10 baris terakhir history command yang relevan dengan pengecekan.
3. Simpan hasil ke file log harian, misalnya healthcheck-$(date +%F).log.
4. Tampilkan hasil ke terminal dan ke file secara bersamaan.
5. Jika Anda menggunakan pipeline dengan tee, cek juga status exit command utama.

   <img src="Screenshot 2026-04-14 235310.png" width="70%">
   <img src="Screenshot 2026-04-14 235212.png" width="70%">

### Tugas Praktikum 4 — Penanganan File dengan Nama Kompleks dan Arsip Aman
1. Buat minimal 4 file contoh dengan nama yang bervariasi, termasuk:
   • nama file yang mengandung spasi,
   • nama file yang mengandung tanda kurung siku atau karakter khusus,
   • file dengan pola nama serupa untuk diuji dengan wildcard.
2. Tunjukkan perbedaan hasil jika file diakses tanpa quoting dan dengan quoting yang benar.
3. Lakukan preview wildcard dengan echo sebelum dipakai untuk operasi nyata.
4. Salin file-file tersebut ke direktori backup dengan nama yang aman.
5. Buat arsip tar.gz dari hasil backup.
6. Simpan riwayat perintah yang Anda gunakan ke file riwayat-arsip.txt

   <img src="Screenshot 2026-04-15 000624.png" width="70%">
   <img src="Screenshot 2026-04-15 000725.png" width="70%">
   <img src="Screenshot 2026-04-15 000749.png" width="70%">
   <img src="Screenshot 2026-04-15 001025.png" width="70%">

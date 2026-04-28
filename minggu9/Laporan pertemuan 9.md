# Laporan Pertemuan 9 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Praktikum 7.1 Script Pertama: Laporan Sistem
1. Buat workspace praktikum:

   <img src="Screenshot 2026-04-22 111200.png" width="70%"> 

2. Buat script dengan nano:

   <img src="Screenshot 2026-04-22 111241.png" width="70%"> 

3. Ketik isi berikut, simpan ( Ctrl+O Enter ), lalu keluar ( Ctrl+X ):

   <img src="Screenshot 2026-04-22 112204.png" width="70%"> 

4. Beri izin dan jalankan:

   <img src="Screenshot 2026-04-22 113356.png" width="70%"> 

### Latihan Latihan 9.1
Modifikasi laporan-sistem.sh agar menyimpan output ke file laporan-YYYY-MM-DD.txt sekaligus menampilkannya di terminal. Petunjuk: gunakan tee yang sudah dipelajari di bab sebelumnya.

<img src="Screenshot 2026-04-22 114901.png" width="70%"> 

## Praktikum 7.2 Script Info Sistem dengan Argumen
1. Buat script:

   <img src="Screenshot 2026-04-22 123836.png" width="70%"> 

2. Ketik isi berikut:

   <img src="Screenshot 2026-04-22 130041.png" width="70%"> 

3. Simpan, beri izin, uji dengan berbagai kombinasi argumen:

   <img src="Screenshot 2026-04-22 130807.png" width="70%"> 

### Latihan Latihan 9.2
Buat script kalkulator.sh yang menerima tiga argumen: <angka1> <operator> <angka2> dengan operator +, -, *, atau /. Contoh: ./kalkulator.sh 20 + 5 menghasilkan 25. Gunakan case untuk memilih operasi, dan validasi jika argumen tidak lengkap

<img src="Screenshot 2026-04-22 133617.png" width="70%"> 
<img src="Screenshot 2026-04-22 134526.png" width="70%"> 

khusus * harus menggunakan "", karena jika tidak ada * akan dianggap wildcard (file), bukan operator

## Praktikum 7.3 Script Grading dan Menu Interaktif
1. Buat script grading (menggunakan if dan for):

   <img src="Screenshot 2026-04-22 144013.png" width="70%"> 

2. Ketik isi berikut:

   <img src="Screenshot 2026-04-22 143706.png" width="70%"> 

3. Simpan, beri izin, dan jalankan:

   <img src="Screenshot 2026-04-22 142808.png" width="70%"> 

4. Buat script menu interaktif (while + case):

   <img src="Screenshot 2026-04-22 143926.png" width="70%"> 

5. Ketik isi berikut:

   <img src="Screenshot 2026-04-22 145018.png" width="70%"> 

6. Beri izin dan jalankan, coba setiap opsi:

   <img src="Screenshot 2026-04-22 145126.png" width="70%"> 

### Latihan Latihan 9.3
Tambahkan ke script grading-batch.sh sebuah ringkasan di bagian bawah yang menampilkan: jumlah mahasiswa per grade (A, B, C, D, E) menggunakan perulangan for kedua yang mengiterasi array MAHASISWA.

<img src="Screenshot 2026-04-22 151207.png" width="70%"> 
<img src="Screenshot 2026-04-22 151253.png" width="70%"> 

## Praktikum 7.4 Library Fungsi Validasi
1. Buat file library:

   <img src="Screenshot 2026-04-27 180707.png" width="70%"> 

2. Ketik isi berikut:

   <img src="Screenshot 2026-04-27 180737.png" width="70%"> 

3. Buat script yang menggunakan library:

   <img src="Screenshot 2026-04-27 180755.png" width="70%"> 

4. Ketik isi berikut:

   <img src="Screenshot 2026-04-27 185706.png" width="70%"> 

5. Beri izin dan uji semua skenario:

   <img src="Screenshot 2026-04-27 185635.png" width="70%"> 

### Latihan Latihan 9.4
Tambahkan fungsi konfirmasi() ke lib-validasi.sh. Fungsi ini menampilkan pertanyaan, membaca input Y/N dari user, mengembalikan 0 jika Y dan 1 jika N. Buat script demo yang memanggil fungsi ini sebelum menghapus sebuah file.

<img src="Screenshot 2026-04-27 192355.png" width="70%"> 
<img src="Screenshot 2026-04-27 193121.png" width="70%"> 
<img src="Screenshot 2026-04-27 193056.png" width="70%"> 

## Praktikum 7.5 Script Backup dengan Opsi
1. Buat script:

   <img src="Screenshot 2026-04-27 193458.png" width="70%">

2. Ketik isi berikut:

   <img src="Screenshot 2026-04-27 195217.png" width="70%">

3. Beri izin dan uji:

   <img src="Screenshot 2026-04-27 195532.png" width="70%">

## Praktikum 7.6 Debugging Script
1. Buat script untuk dianalisis:

   <img src="Screenshot 2026-04-27 200038.png" width="70%">

2. Ketik isi berikut:

   <img src="Screenshot 2026-04-27 200608.png" width="70%">

3. Cek sintaks, lalu jalankan dengan tracing:

   <img src="Screenshot 2026-04-27 200755.png" width="70%">
   <img src="Screenshot 2026-04-27 200925.png" width="70%">

### Latihan Latihan 9.5
Script debug-latihan.sh tidak menangani direktori yang tidak ada. Perbaiki
dengan menambahkan:
- set -e di baris kedua
- Pengecekan -d "$DIREKTORI" sebelum memanggil du
- Pesan error yang informatif jika direktori tidak ditemukan

Uji dengan direktori yang tidak ada.

<img src="Screenshot 2026-04-27 201836.png" width="70%">
<img src="Screenshot 2026-04-27 201919.png" width="70%">

## Tugas Praktikum
### Tugas 1 Script Absensi Kelas
<img src="Screenshot 2026-04-28 194339.png" width="70%">
<img src="Screenshot 2026-04-28 194404.png" width="70%">
<img src="Screenshot 2026-04-28 195418.png" width="70%">

### Tugas 2 Script Health Check Sistem
<img src="Screenshot 2026-04-28 202353.png" width="70%">
<img src="Screenshot 2026-04-28 202502.png" width="70%">
<img src="Screenshot 2026-04-28 202252.png" width="70%">
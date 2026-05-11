# Laporan Pertemuan 11 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Praktikum 9.1 — Permissions
Langkah 1: Buat direktori kerja dan dua file uji.

<img src="Screenshot 2026-05-06 085055.png" width="70%"> 

Langkah 2: Jadikan secret.txt privat hanya untuk owner.

<img src="Screenshot 2026-05-06 085349.png" width="70%"> 

Langkah 3: Jadikan myscript.sh dapat dijalankan.

<img src="Screenshot 2026-05-06 085453.png" width="70%"> 

Langkah 4: Buat direktori bersama dan amati efek SGID sederhana

<img src="Screenshot 2026-05-06 085551.png" width="70%"> 

Langkah 5: Uji efek umask pada file baru.

<img src="Screenshot 2026-05-06 085636.png" width="70%"> 

### Analisis
1. Mengapa secret.txt tidak dapat dibaca oleh group dan others setelah chmod 600?
2. Apa perbedaan arti 600 dan 755 terhadap file yang diuji?
3. Setelah umask 027, permission apa yang dihasilkan untuk file baru, dan mengapa bukan 777?
#### Jawaban Analisis
1. Setelah chmod 600, file secret.txt berubah menjadi -rw-------. Angka "0" pada posisi group dan others berarti seluruh hak akses dicabut secara total, sehingga hanya pemilik yang dapat membaca atau mengubah isinya.
2. perbedaan arti 600 dan 755
   - **600 (-rw-------)**: Fokus pada privasi. Digunakan untuk file dokumen yang hanya boleh diakses oleh pemilik.
   - **755 (-rwxr-xr-x)**: Fokus pada fungsionalitas eksekusi. Digunakan pada myscript.sh agar file tersebut bisa dijalankan sebagai program oleh siapa saja, meski hanya pemilik yang boleh mengubah isinya.
3. Berdasarkan hasil ls -l testfile-027, izin yang terbentuk adalah 640 (-rw-r-----).

   Hasilnya bukan 777 karena dua alasan teknis utama:
   - **Basis Default**: Di Linux, file baru secara otomatis menggunakan basis izin 666 (tanpa izin eksekusi), sedangkan basis 777 hanya diperuntukkan bagi folder.
   - **Efek Penyaringan (Masking)**: Perintah umask 027 berfungsi sebagai penyaring yang membuang izin tulis bagi grup dan membuang seluruh izin bagi pengguna lain dari basis default tersebut.
### Tantangan
Ubah owner atau group salah satu file uji ke akun atau group lain yang tersedia di sistem, kemudian jelaskan perubahan output ls -l sebelum dan sesudahnya.

<img src="Screenshot 2026-05-06 124920.png" width="70%"> 

Perubahan owner/group pada output ls -l secara visual mengubah teks di kolom keempat. Secara fungsional, hal ini mengalihkan kontrol hak akses (permission) dari individu/grup lama ke subjek baru yang ditentukan dalam sistem.

## Praktikum 9.2 — ACL
Langkah 1: Siapkan file dan lihat permission standar tanpa ACL tambahan.

<img src="Screenshot 2026-05-06 144120.png" width="70%"> 

Langkah 2: Beri akses baca ke satu user tertentu tanpa mengubah owner atau group.

<img src="Screenshot 2026-05-06 144900.png" width="70%"> 

Langkah 3: Buat direktori bersama yang mewariskan ACL ke file baru.

<img src="Screenshot 2026-05-06 145221.png" width="70%"> 

### Analisis
1. Mengapa getfacl confidential.txt awalnya tidak menampilkan user tertentu?
2. Setelah setfacl -m u:userA:r confidential.txt, apa perbedaan output ls -l dan getfacl?
3. Mengapa file inherited.txt mewarisi ACL dari direktori shared?
#### Jawaban Analisis
1. Awalnya, getfacl hanya menampilkan entri dasar (owner, group, others) karena file tersebut hanya menggunakan permission Unix standar. Belum ada aturan tambahan (ACL) yang didefinisikan secara khusus untuk pengguna lain pada tahap tersebut.
2. Setelah perintah setfacl -m u:userA:r dijalankan, terjadi dua perubahan utama:
   - **ls -l**, muncul tanda plus (+) di akhir string permission (contoh: -rw-r-----+), menandakan aktifnya ACL.
   - **getfacl**, muncul baris baru user:userA:r-- serta entri mask yang membatasi izin efektif bagi pengguna tambahan.
3. File inherited.txt mewarisi ACL secara otomatis karena direktori induknya (shared) memiliki Default ACL (opsi -d pada setfacl). Fitur ini memastikan setiap file baru di dalam direktori tersebut mengadopsi aturan akses yang sama tanpa perlu diatur ulang secara manual.

### Tantangan
Tambahkan satu ACL lagi agar group readonly-group hanya dapat membaca confidential.txt. Setelah itu, hapus ACL untuk userA dan verifikasi hasil akhirnya dengan getfacl.

<img src="Screenshot 2026-05-06 150353.png" width="70%"> 

## Praktikum 9.3A — Membuat dan Mengelola User
<img src="Screenshot 2026-05-09 084017.png" width="70%"> 

### Pertanyaan
1. Apa perbedaan output id userA sebelum dan sesudah menambah group?
2. Bagaimana status passwd -S userB berubah saat akun di-lock?
#### Jawaban Pertanyaan
1. perbedaan output id userA sebelum dan sesudah menambah group
   - Sebelum: Output hanya menampilkan grup primer
   - Sesudah: Daftar pada bagian groups= bertambah dengan nama grup baru
2. status passwd -S userB
   - Sebelum di-Lock: Kolom kedua berisi kode P (Password usable), artinya akun aktif dan userB bisa login dengan password.
   - Sesudah di-Lock: Kolom kedua berubah menjadi L (Locked). Hal ini menandakan password telah dinonaktifkan oleh sistem, sehingga userB tidak bisa login ke sistem.


## Praktikum 9.3B — Group Management
<img src="Screenshot 2026-05-09 085303.png" width="70%"> 

### Pertanyaan
1. Apa yang ditampilkan id userA vs groups userA?
2. Mengapa -a pada usermod -aG penting?
#### Jawaban Pertanyaan
1. id userA vs groups userA
   - id userA: Menampilkan detail teknis lengkap, yaitu UID (nomor user), GID (nomor grup utama), dan daftar semua grup tambahan dalam bentuk angka dan nama.
   - groups userA: Hanya menampilkan nama-nama grup saja secara sederhana, tanpa identitas angka (UID/GID).
2. -a pada usermod -aG penting karena untuk menambah grup baru tanpa menghapus grup lama.

## Praktikum 9.3C — Password Aging Policy
<img src="Screenshot 2026-05-09 085800.png" width="70%"> 

### Pertanyaan
1. Apa arti nilai yang ditampilkan chage -l userA?
2. Bagaimana cara membuktikan userB terkunci dari output passwd -S?
3. Kapan sebaiknya menggunakan chage -d 0 vs passwd -e?
#### Jawaban Pertanyaan
1. Perintah ini menampilkan kebijakan masa berlaku password. Nilai-nilai utamanya adalah:
   - **Last password change**: Tanggal terakhir user mengganti password.
   - **Password expires**: Tanggal password akan kedaluwarsa.
   - **Password inactive**: Masa tenggang setelah kedaluwarsa sebelum akun terkunci total.
   - **Minimum/Maximum number of days**: Jarak hari minimal dan maksimal antar pergantian password.
2. cukup melihat kode pada kolom kedua output tersebut, jika kolom kedua adalah L (Locked), maka akun resmi terkunci.
3. Kapan menggunakan chage -d 0 vs passwd -e:
   - **chage -d 0 user**:Mengatur tanggal terakhir ganti password menjadi 0 sehingga password langsung dianggap expired. Cocok untuk administrasi kebijakan umur password secara detail.
   - **passwd -e user**:Memaksa user mengganti password saat login berikutnya dengan cara cepat dan sederhana.

### Tantangan
Buat user bernama intern yang:
- memiliki shell /bin/bash;
- menjadi anggota labgroup;
- dipaksa ganti password pada login pertama;
- password expired setelah 45 hari dengan warning 7 hari sebelumnya.

<img src="Screenshot 2026-05-09 090811.png" width="70%"> 

## Praktikum 9.4 — Konfigurasi sudo
Langkah 1: Buat file konfigurasi sudo khusus untuk userA.

<img src="Screenshot 2026-05-09 091313.png" width="70%"> 

Langkah 2: Verifikasi aturan yang aktif dan uji hasilnya.

<img src="Screenshot 2026-05-09 091553.png" width="70%"> 

### Analisis
1. Mengapa aturan disimpan di /etc/sudoers.d//, bukan langsung di /etc/sudoers?
2. Mana perintah yang bisa dijalankan tanpa password, dan mana yang masih perlu autentikasi?
3. Informasi apa saja yang dicatat di log sudo?
#### Jawaban Analisis
1. Aturan sudo disimpan di /etc/sudoers.d/ agar konfigurasi lebih rapi, aman, dan mudah dikelola tanpa mengubah file utama /etc/sudoers.
2. Perintah apt update dan apt upgrade dapat dijalankan tanpa password karena menggunakan NOPASSWD. Perintah systemctl status * masih memerlukan autentikasi password sudo.
3. Log sudo mencatat waktu penggunaan sudo, nama user, terminal yang dipakai, direktori aktif, target user, dan perintah yang dijalankan.

### Tantangan
Tambahkan satu aturan baru agar userA boleh menjalankan /bin/systemctl restart ssh tetapi tidak boleh menjalankan reboot

<img src="Screenshot 2026-05-09 091938.png" width="70%">
<img src="Screenshot 2026-05-09 092518.png" width="70%">

## Praktikum 9.5 — Disk Quota
Langkah 1: Buat image filesystem kecil dan mount dengan opsi quota.

<img src="Screenshot 2026-05-09 095017.png" width="70%"> 

Langkah 2: Buat database quota dan aktifkan enforcement.

<img src="Screenshot 2026-05-09 095157.png" width="70%"> 

Langkah 3: Tetapkan quota untuk user uji dan amati hasilnya.

<img src="Screenshot 2026-05-09 095620.png" width="70%">
<img src="Screenshot 2026-05-09 101128.png" width="70%"> 

Langkah 4: Bersihkan lingkungan uji setelah selesai.

<img src="Screenshot 2026-05-09 095818.png" width="70%"> 

### Analisis
1. Apa perbedaan soft limit dan hard limit saat quota mulai terlampaui?
2. Mengapa praktikum ini memakai loopback filesystem, bukan langsung /home/?
3. Dari output repquota, informasi apa yang menunjukkan quota sudah aktif?
#### Jawaban Analisis
1. Perbedaan soft limit dan hard limit saat quota mulai terlampaui:
   - Soft Limit: Batas peringatan. User masih bisa menambah file, tapi muncul peringatan dan masa tenggang (grace period) dimulai.
   - Hard Limit: Batas mati. User langsung dilarang menambah file apa pun. Muncul pesan error "Disk quota exceeded".
2. Memakai loopback filesystem, karena aman (tidak berisiko merusak partisi sistem utama (/home) jika salah konfigurasi), praktis (tidak perlu restart sistem untuk mengaktifkan kuota), efisien (cukup menggunakan file kecil (simulasi) untuk menguji limit disk).
3. Tanda Quota Sudah Aktif (repquota):
   - Muncul baris Block grace time: 7days.
   - Kolom soft dan hard pada baris user berisi angka (bukan 0)
   - Kolom used menampilkan jumlah blok data yang sudah digunakan user secara real-time.

### Tantangan
Coba atur quota baru untuk userA dengan batas inode yang sangat kecil, kemudian jelaskan kapan pembatasan inode lebih penting daripada pembatasan block.

<img src="Screenshot 2026-05-11 191205.png" width="70%"> 

Pembatasan inode menjadi krusial dalam kondisi berikut:
- **Sistem dengan Banyak File Kecil**: Kapasitas disk mungkin masih tersisa 50 GB (block masih luas), tetapi jika user membuat jutaan file kecil berukuran 1 KB (seperti cache aplikasi atau session files), maka inode akan habis lebih dulu. Jika inode habis, disk dianggap "penuh" dan tidak ada user yang bisa membuat file baru meskipun kapasitas gigabyte-nya masih kosong.
- **Keamanan (Pencegahan Serangan DoS)**: Mencegah user nakal atau skrip yang error melakukan looping pembuatan file kosong tanpa henti yang bertujuan untuk menghabiskan indeks file sistem (inode exhaustion).
- **Server Email atau Web**: Server yang menampung ribuan email kecil atau file gambar thumbnail sering kali kehabisan inode sebelum kehabisan ruang penyimpanan.

## Latihan
### Latihan Latihan 9.A — Audit dan Kolaborasi
1. Temukan file SUID aktif dengan find / -perm -4000 -type f 2>/dev/null, lalu jelaskan tiga file yang Anda kenali beserta alasannya.
2. Cari direktori world-writable dan tentukan mana yang valid dan mana yang berisiko.
3. Rancang konfigurasi permission standar dan ACL untuk direktori proyek /srv/webapp/ agar group webapp-team dapat menulis, user deploy hanya membaca, dan file baru selalu mewarisi group proyek.
### Jawaban

1. <img src="Screenshot 2026-05-11 191718.png" width="70%">

   Tiga file yang dikenali:
   - **/usr/bin/passwd**: Digunakan user untuk mengganti password sendiri. File ini butuh SUID karena ia harus memodifikasi file /etc/shadow yang hanya bisa diakses oleh root.
   - **/usr/bin/sudo**: Digunakan untuk menjalankan perintah sebagai superuser. Ia butuh SUID agar bisa memverifikasi kredensial user dan berpindah identitas menjadi root.
   - **/usr/bin/chfn**: Digunakan untuk mengubah informasi finger (nama lengkap, nomor telepon, dll). Ia butuh SUID untuk menulis perubahan tersebut ke dalam database sistem /etc/passwd.

2. <img src="Screenshot 2026-05-11 191950.png" width="70%">
   
   Valid (Aman/Diperlukan):
   - **/tmp dan /var/tmp**: Direktori ini memang harus bisa ditulisi oleh siapa saja karena aplikasi sering menyimpan file sementara di sini. 
   - **/var/spool/mail**: Valid untuk proses pengiriman pesan sistem.

   Berisiko (Ancaman Keamanan):
   - Direktori konfigurasi aplikasi atau home user yang bersifat world-writable sangat berbahaya. Penyerang bisa menyisipkan skrip berbahaya (malware) atau mengganti file konfigurasi untuk mengambil alih sistem.

3. <img src="Screenshot 2026-05-11 192750.png" width="70%">

### Latihan Latihan 9.B — Kebijakan Akun dan Quota
Tuliskan langkah untuk membuat user intern, menambahkannya ke group labgroup, memaksa pergantian password tiap 45 hari (warning 7 hari), memberi izin sudo hanya untuk systemctl status, dan menetapkan quota ruang serta inode sederhana pada /home/.

<img src="Screenshot 2026-05-11 193703.png" width="70%">

<img src="Screenshot 2026-05-11 194220.png" width="70%">

<img src="Screenshot 2026-05-11 200058.png" width="70%">
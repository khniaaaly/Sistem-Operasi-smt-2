# Laporan Pertemuan 12 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Praktek 10.1: Amati Layanan Aktif Saat Boot
Langkah 1:  Lihat semua layanan yang sedang berjalan.

<img src="Screenshot 2026-05-16 082113.png" width="70%">

Langkah 2: Lihat semua unit service yang ada (aktif maupun tidak)

<img src="Screenshot 2026-05-16 082217.png" width="70%">

Langkah 3: Analisis waktu boot dan temukan layanan paling lambat.

<img src="Screenshot 2026-05-16 082348.png" width="70%">

### Tantangan
Identifikasi tiga layanan dengan waktu inisialisasi terlama menggunakan systemd-analyze blame. Gunakan pipeline dari Bab 3 (| sort -rh | head -3) untuk mempercepat pencariannya. Untuk setiap layanan, cari tahu fungsinya dengan systemctl cat nama-layanan. Tuliskan nama layanan, waktu inisialisasinya, dan penjelasan singkat fungsinya.

<img src="Screenshot 2026-05-16 083054.png" width="70%">
<img src="Screenshot 2026-05-16 083149.png" width="70%">

Nama Layanan: fwupd-refresh.service

Waktu Inisialisasi: 6.189 detik

Fungsi: Memperbarui data informasi update keamanan firmware (BIOS/perangkat keras) dari internet agar sistem tahu jika ada pembaruan hardware yang tersedia.

<img src="Screenshot 2026-05-16 083209.png" width="70%">

Nama Layanan: systemd-networkd-wait-online.service

Waktu Inisialisasi: 1.784 detik

Fungsi: Menunda proses booting sejenak untuk memastikan jaringan internet sudah benar-benar terhubung sebelum layanan lain yang butuh koneksi dijalankan.

<img src="Screenshot 2026-05-16 083252.png" width="70%">

Nama Layanan: snapd.seeded.service

Waktu Inisialisasi: 1.314 detik

Fungsi: Mengaktifkan dan menyiapkan aplikasi berformat Snap bawaan Ubuntu agar langsung siap digunakan setelah komputer menyala.

## Praktek 10.2: Kelola Layanan SSH
Langkah 1: Periksa status SSH secara menyeluruh.

<img src="Screenshot 2026-05-16 084216.png" width="70%">

Langkah 2: Lakukan restart dan pantau perubahannya

<img src="Screenshot 2026-05-16 084350.png" width="70%">

Langkah 3: Lihat dependensi SSH.

<img src="Screenshot 2026-05-16 084434.png" width="70%">

Langkah 4: Cek semua unit yang gagal di sistem.

<img src="Screenshot 2026-05-16 084637.png" width="70%">

### Tantangan
Buat skrip Bash (referensi Bab 7) bernama cek-layanan.sh yang memeriksa status daftar layanan dari sebuah berkas teks. Berkas teks daftar-layanan.txt berisi satu nama layanan per baris (isi minimal: ssh, cron, rsyslog). Skrip membaca setiap nama layanan, memeriksa statusnya dengan systemctl is-active, lalu menulis laporan ke berkas laporan-layanan.log dengan format: [TANGGAL] nama-layanan: ACTIVE/INACTIVE. Gunakan date untuk mendapatkan tanggal.

<img src="Screenshot 2026-05-16 104125.png" width="70%">
<img src="Screenshot 2026-05-16 104138.png" width="70%">
<img src="Screenshot 2026-05-16 104035.png" width="70%">

## Praktek 10.3: Buat Layanan Sederhana dari Skrip Bash
Langkah 1: Siapkan konten yang akan dilayani.

<img src="Screenshot 2026-05-16 112510.png" width="70%">

Langkah 2: Buat skrip wrapper untuk server HTTP

<img src="Screenshot 2026-05-16 110206.png" width="70%">

Langkah 3: Buat berkas unit systemd untuk layanan ini.

<img src="Screenshot 2026-05-16 110913.png" width="70%">

Langkah 4: Jalankan layanan dan verifikasi.

<img src="Screenshot 2026-05-16 111148.png" width="70%">

Langkah 5: Uji fitur restart otomatis.

<img src="Screenshot 2026-05-16 112054.png" width="70%">

Langkah 6: Bersihkan layanan uji setelah selesai.

<img src="Screenshot 2026-05-16 112218.png" width="70%">

### Tantangan
Modifikasi berkas unit demo-web.service sebelum menghapusnya: tambahkan RestartSec=10s agar sistemmenunggu 10 detik sebelum mencoba restart, dan tambahkan Environment="PORT=9091" lalu ubah ExecStart agar menggunakan variabel tersebut. Aktifkan layanan dengan enable dan WantedBy=multi-user.target, lalu uji apakah layanan aktif setelah systemctl daemon-reload. Dokumentasikan perbedaan perilaku dibanding versi sebelumnya.

<img src="Screenshot 2026-05-16 115941.png" width="70%">
<img src="Screenshot 2026-05-16 115917.png" width="70%">

Perbedaan: 
1. Perbaikan Sintaks Section Unit

   Pada versi lama, penulisan nama section menggunakan huruf kecil ([unit]). Karena systemd bersifat case-sensitive, hal ini memicu error “Unknown section 'unit'” dan membuat deskripsi layanan diabaikan.
   Setelah diperbaiki menjadi [Unit] dengan huruf kapital, systemd dapat membaca seluruh konfigurasi dengan normal tanpa warning.

2. Penggunaan Variabel Lingkungan dan Fleksibilitas Port

   Versi lama mengunci port secara statis langsung pada perintah utama (http.server 9090). 
   Pada versi baru, sistem menggunakan variabel lingkungan dinamis (Environment="PORT=9091") yang dipanggil via $PORT pada ExecStart. Hasil pengujian curl membuktikan server berhasil berpindah dan merespons dengan lancar di port 9091.

3. Mekanisme Jeda Waktu Pemulihan Layanan (RestartSec)

   Saat layanan dihentikan paksa (kill -9), konfigurasi lama (RestartSec=3s) membuat systemd langsung menghidupkan kembali server hanya dalam waktu 3 detik.
   Dengan mengubahnya menjadi RestartSec=10s, systemd kini menahan proses pemulihan dan menunggu selama 10 detik. Jeda ini berfungsi melindungi server dari beban berlebih akibat putaran error yang terlalu cepat (crash looping).

## Praktek 10.4: Filter dan Analisis Log Layanan
Langkah 1: Lihat log SSH dari satu jam terakhir.

<img src="Screenshot 2026-05-16 132517.png" width="70%">

Langkah 2: Filter log berprioritas error ke atas.

<img src="Screenshot 2026-05-16 132603.png" width="70%">

Langkah 3: Ikuti log secara real-time sambil memicu aktivitas.

<img src="Screenshot 2026-05-16 132646.png" width="70%">

Langkah 4: Ekstrak log ke berkas untuk analisis.

<img src="Screenshot 2026-05-16 135847.png" width="70%">

### Tantangan
Ekstrak semua log dengan prioritas error (-p err) dari 24 jam terakhir untuk layanan SSH, simpan ke berkas error-ssh-24jam.txt. Gunakan pipeline dari Bab 3 untuk menghitung total jumlah baris error dengan wc -l, lalu tampilkan 10 pesan error yang paling sering muncul menggunakan sort | uniq -c | sort -rn | head -10. Tuliskan perintah lengkap yang kamu gunakan.

<img src="Screenshot 2026-05-16 154508.png" width="70%">

## Praktek 10.5: Konfigurasi SSH Server
Langkah 1: Periksa konfigurasi SSH saat ini.

<img src="Screenshot 2026-05-16 154720.png" width="70%">

Langkah 2: Buat backup dan ubah port SSH.

<img src="Screenshot 2026-05-16 154919.png" width="70%">

Langkah 3: Validasi konfigurasi dan restart layanan.

<img src="Screenshot 2026-05-16 155053.png" width="70%">

Langkah 4: Verifikasi port baru dengan ss.

<img src="Screenshot 2026-05-16 155229.png" width="70%">

Langkah 5: Kembalikan port SSH ke 22 setelah praktek.

<img src="Screenshot 2026-05-16 155528.png" width="70%">

### Tantangan
Ubah konfigurasi SSH untuk menambahkan dua pengaturan keamanan: PermitRootLogin no (larang login root langsung) dan MaxAuthTries 3 (maksimal tiga kali percobaan). Lakukan dengan urutan yang aman: backup, edit, validasi dengan sshd -t, reload. Verifikasi perubahan dengan grep -E "PermitRoot|MaxAuth" /etc/ssh/sshd_config. Kemudian periksa log SSH untuk memastikan tidak ada error setelah perubahan dengan journalctl -u ssh -n 20. Referensi Bab 2 untuk penggunaan ss dan Bab 9 untuk keamanan pengguna.

<img src="Screenshot 2026-05-16 160558.png" width="70%">
<img src="Screenshot 2026-05-16 161117.png" width="70%">

## Latihan
### Latihan 10.1 Audit Layanan dan Analisis Boot
1. Jalankan systemctl list-units –type=service –state=running dan catat semua layanan aktif. Pilih tiga layanan yang kamu kenal, periksa status masing-masing dengan systemctl status, dan jelaskan fungsinya.
2. Jalankan systemd-analyze blame dan identifikasi lima layanan dengan waktu inisialisasi terlama. Tampilkan hasilnya menggunakan pipeline: systemd-analyze blame | head -5.
3. Jalankan systemctl –failed dan dokumentasikan hasilnya. Jika ada layanan yang gagal, cari tahu penyebabnya dengan journalctl -u nama-layanan -n 30.

### Jawaban
1. <img src="Screenshot 2026-05-16 161517.png" width="70%">
   <img src="Screenshot 2026-05-16 161848.png" width="70%">

   Fungsi: Layanan SSH digunakan untuk mengakses server atau komputer lain dari jarak jauh secara aman.

   <img src="Screenshot 2026-05-16 161927.png" width="70%">

   Fungsi: Layanan cron digunakan untuk menjalankan tugas otomatis terjadwal, seperti backup atau update sistem.

   <img src="Screenshot 2026-05-16 161954.png" width="70%">

   Fungsi: Layanan rsyslog digunakan untuk mencatat log sistem dan aktivitas layanan pada Linux.

2. <img src="Screenshot 2026-05-16 162432.png" width="70%">
3. <img src="Screenshot 2026-05-16 162657.png" width="70%">

### Latihan 10.2 Layanan Kustom dengan Restart Otomatis
1. Buat skrip Bash (referensi Bab 7) bernama monitor-disk.sh yang setiap 30 detik menuliskan penggunaan disk ke berkas log. Gunakan df -h dan date.
2. Buat berkas unit /etc/systemd/system/monitor-disk.service untuk menjalankan skrip tersebut dengan konfigurasi: Restart=always, RestartSec=5s, dan berjalan sebagai pengguna kamu sendiri.
3. Aktifkan dan jalankan layanan. Verifikasi dengan systemctl status dan pastikan log masuk ke journal.
4. Simulasikan crash dengan membunuh proses secara paksa (kill -9), tunggu 10 detik, dan verifikasi bahwa layanan hidup kembali secara otomatis.
5. Bersihkan: nonaktifkan layanan dan hapus berkas unit setelah selesai.

### Jawaban
1. <img src="Screenshot 2026-05-16 163104.png" width="70%">
2. <img src="Screenshot 2026-05-16 163353.png" width="70%">
3. <img src="Screenshot 2026-05-16 163923.png" width="70%">
4. <img src="Screenshot 2026-05-16 164136.png" width="70%">
5. <img src="Screenshot 2026-05-16 164556.png" width="70%">

### Latihan 10.3 Investigasi Log dan Keamanan SSH
1. Gunakan journalctl -b -p err untuk menemukan semua error sejak boot terakhir. Simpan hasilnya ke berkas dan hitung jumlah baris dengan wc -l.
2. Lakukan tiga perubahan keamanan pada /etc/ssh/sshd_config: tambahkan PermitRootLogin no, MaxAuthTries 3, dan LoginGraceTime 30. Ikuti alur aman: backup, edit, validasi sshd -t, reload.
3. Setelah reload, verifikasi tiga hal: layanan masih berjalan (systemctl status ssh), port masih mendengarkan (ss -tlnp | grep ssh), dan konfigurasi baru terbaca (grep -E "PermitRoot|MaxAuth|GraceTime" /etc/ssh/sshd_config).
4. Kembalikan konfigurasi SSH ke kondisi semula menggunakan berkas backup.

### Jawaban
1. <img src="Screenshot 2026-05-16 164910.png" width="70%">
2. <img src="Screenshot 2026-05-16 165107.png" width="70%">
   <img src="Screenshot 2026-05-16 165230.png" width="70%">
3. <img src="Screenshot 2026-05-16 165628.png" width="70%">
4. <img src="Screenshot 2026-05-16 165754.png" width="70%">
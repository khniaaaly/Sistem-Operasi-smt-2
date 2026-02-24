# Laporan Pertemuan 2 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Praktikum 2.1 - Identifikasi CPU dan Memori
Tampilkan informasi CPU:

<img src="Screenshot 2026-02-24 125047.png" width="70%"> 

Tampilkan ringkasan memori:

<img src="Screenshot 2026-02-24 125144.png" width="70%">

(opsional) cek informasi hardware dari DMI/BIOS (butuh sudo):

<img src="Screenshot 2026-02-24 125245.png" width="70%"> 

### Latihan Praktikum 2.1
1. Jumlah CPU(s), core/thread
2. Total RAM
3. Total Swap. Jelaskan perbedaan 

### Jawaban Praktikum 2.1
1. CPU(s) = 1 -> Core(s) = 1/Thread(s) = 1
2. RAM = 1.9 GiB
3. Swap = 2.0 GiB

perbedaan RAM dan Swap:
- RAM adalah memori utama yang digunakan untuk menyimpan data dan program yang sedang berjalan. RAM bekerja sangat cepat karena langsung terhubung ke prosesor, tetapi bersifat sementara (data hilang saat komputer dimatikan).
- Swap adalah memori cadangan yang berada di hard disk atau SSD dan digunakan ketika RAM penuh. Swap membantu sistem tetap berjalan, tetapi kecepatannya lebih lambat dibandingkan RAM karena menggunakan media penyimpanan.

## Praktikum 2.2 - Identifikasi Perangkat PCI/USB dan Driver
Lihat daftar perangkat PCI:

<img src="Screenshot 2026-02-24 125757.png" width="70%">

Lihat perangkat PCI beserta driver kertel yang digunakan:

<img src="Screenshot 2026-02-24 125850.png" width="70%">

Fokus pada NIC (Ethernet) untuk mencari modul driver:

<img src="Screenshot 2026-02-24 130023.png" width="70%">

Lihat perangkat USB:

<img src="Screenshot 2026-02-24 130058.png" width="70%">

Lihat topologi USB (tree):

<img src="Screenshot 2026-02-24 130134.png" width="70%">

### Latihan Praktikum 2.2

Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya

### Jawaban Praktikum 2.2

Perangkat PCI: Ethernet controller (NIC)

Vendor:Device ID (8086:100e)

Nama Driver: e1000, fungsinya Driver untuk kartu jaringan Intel Gigabit Ethernet. Mengatur komunikasi jaringan kabel (LAN).

## Praktikum 2.3 - Identifikasi Storage dan Filesystem
Lihat daftar disk/partisi:

<img src="Screenshot 2026-02-24 133742.png" width="70%">

Tampilkan UUID dan tipe filesystem:

<img src="Screenshot 2026-02-24 133822.png" width="70%">

Lihat mount point untuk root filesystem:

<img src="Screenshot 2026-02-24 133853.png" width="70%">

## Praktikum 2.4 - Melihat Modul Aktif dan Informainya
Cek versi kernel:

<img src="Screenshot 2026-02-24 151845.png" width="70%">

Tampilkan daftar modul aktif:

<img src="Screenshot 2026-02-24 152032.png" width="70%">

Pilih salah satu modul (contoh aman: loop) dan lihat detailnya:

<img src="Screenshot 2026-02-24 152118.png" width="70%">

(Opsional) lihat pesan kernel terbaru:

<img src="Screenshot 2026-02-24 152222.png" width="70%">

## Praktikum 2.5 - Konfigurasi Auto-load dan Blacklist
Buat file auto-load:

<img src="Screenshot 2026-02-24 153108.png" width="70%">

## Praktikum 2.6 - Mengenali Block vs Character Device
Lihat detail salah satu disk (sesuaikan dengan perangkat Anda, misal sda):

<img src="Screenshot 2026-02-24 153725.png" width="70%">

Lihat detail device terminal:

<img src="Screenshot 2026-02-24 153754.png" width="70%">

Lihat disk dan partisi untuk mengaitkan dengan /dev:

<img src="Screenshot 2026-02-24 153818.png" width="70%">

### Latihan Praktikum 2.6

Dari output ls -l, jelaskan perbedaan penanda file untuk block device dan character device. (Hint: karakter pertama pada permission string)

### Jawaban Praktikum 2.6

Perbedaan dari penanda file untuk block device dan character device yaitu terletak pada huruf pertama

- b (block device): Mengakses data dalam bentuk blok (block-oriented)
- c (character device): Mengakses data secara berurutan per karakter (stream)

## Praktikum 2.7 - Melihat Informasi udev
Cek atribut udev untuk disk:

<img src="Screenshot 2026-02-24 155253.png" width="70%">

(Opsional) monitor event udev (jalankan, lalu colok/lepas USB pada mesin fisik):

<img src="Screenshot 2026-02-24 155339.png" width="70%">

## Praktikum 2.8 - Membuat Workspace Praktikum
Buat direktori praktikum dan masuk ke dalamnya:

<img src="Screenshot 2026-02-24 161100.png" width="70%">

Buat beberapa file contoh:

<img src="Screenshot 2026-02-24 161128.png" width="70%">

Isi file log contoh (simulasi):

<img src="Screenshot 2026-02-24 161427.png" width="70%">

Baca file dengan less:

<img src="Screenshot 2026-02-24 161451.png" width="70%">

## Praktikum 2.9 - Pencarian Pola dengan grep
Cari baris yang mengandung ERROR pada data.log,
Cari tanpa memperhatikan huruf besar/kecil,
Tampilkan nomor baris,
Tampilkan baris yang tidak cocok (invert match):

<img src="Screenshot 2026-02-24 163509.png" width="70%">

### Latihan Praktikum 2.9 

Gunakan grep untuk menampilkan hanya baris yang mengandung INFO atau WARN dari data.log. (Hint: gunakan grep -E dengan pola alternatif)

### Jawaban Praktikum 2.9

<img src="Screenshot 2026-02-24 192807.png" width="70%">

## Praktikum 2.10 - Substitusi dengan sed (Aman di File Latihan)
Siapkan file konfigurasi latihan:

<img src="Screenshot 2026-02-24 164559.png" width="70%">

Ganti dev menjadi prod (tanpa mengubah file asli):

<img src="Screenshot 2026-02-24 164819.png" width="70%">

Terapkan perubahan langsung ke file (-i):

<img src="Screenshot 2026-02-24 165002.png" width="70%">

Ganti semua kemunculan kata (g untuk global), contoh ubah myserver menjadi node:

<img src="Screenshot 2026-02-24 165113.png" width="70%">

## Praktikum 2.11 - Ekstraksi Kolom dengan awk
Lihat output df -h:

<img src="Screenshot 2026-02-24 165504.png" width="70%">

Ambil kolom filesystem dan persentase pemakaian:

<img src="Screenshot 2026-02-24 165639.png" width="70%">

Filter hanya yang pemakaian disk di atas 80%:

<img src="Screenshot 2026-02-24 165746.png" width="70%">

## Praktikum 2.12 - Melihat Proses dengan ps
Tampilkan semua proses (format BSD):

<img src="Screenshot 2026-02-24 170756.png" width="70%">

Cari proses tertentu (misal sshd):

<img src="Screenshot 2026-02-24 170832.png" width="70%">

## Praktikum 2.13 - Monitoring Real-time dengan top
Jalankan top:

<img src="Screenshot (260).png" width="70%">

## Praktikum 2.14 - Menghentikan Proses dengan kill
Jalankan proses dummy di background:

<img src="Screenshot 2026-02-24 174502.png" width="70%">

Cari PID proses sleep:

<img src="Screenshot 2026-02-24 174537.png" width="70%">

Hentikan dengan SIGTERM:

<img src="Screenshot 2026-02-24 174557.png" width="70%">

Verifikasi proses berhenti:

<img src="Screenshot 2026-02-24 174616.png" width="70%">

(Opsional) Jika proses sulit untuk dihentikan dan Anda membutukan untuk menghentikan proses tersebut, gunakan SIGKILL:

<img src="Screenshot 2026-02-24 174633.png" width="70%">

## Praktikum 2.15 - Cek Disk, Load, dan Service
Cek penggunaan disk:

<img src="Screenshot 2026-02-24 174714.png" width="70%">

Cari direktori yang besar (contoh pada /var):

<img src="Screenshot 2026-02-24 174818.png" width="70%">

Cek load dan uptime:

<img src="Screenshot 2026-02-24 174844.png" width="70%">

Cek service yang gagal:

<img src="Screenshot 2026-02-24 174915.png" width="70%">

Ambil log error terbaru (jika ada indikasi masalah):

<img src="Screenshot 2026-02-24 175020.png" width="70%">

## Praktikum 2.16 - Monitoring Port dan Koneksi (Network Basics)
Lihat interface dan IP:

<img src="Screenshot 2026-02-24 175731.png" width="70%">

Lihat routing table:

<img src="Screenshot 2026-02-24 175755.png" width="70%">

Lihat port yang sedang listening:

<img src="Screenshot 2026-02-24 175820.png" width="70%">

### Latihan Praktikum 2.16

Pilih satu port yang listening dari output ss -tulpn(misal port 22), lalu tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut secara singkat.

### Jawaban Praktikum 2.16

- Port 53
- Service/proses: systemd-resolve
- Kegunaannya untuk menerjemahkan nama domain (misalnya google.com) menjadi alamat IP, dan digunakan saat sistem melakukan query DNS.

## 1.9 Latihan
### Latihan 2.A

Jalankan lspci -nnk. Pilih 1 perangkat PCI dan tuliskan: nama perangkat ID vendor:device, dan kernel driver in use.

- **Perangkat PCI:** Ethernet Controller

- **Nama Perangkat:** Intel Corporation 82540EM Gigabait Ethernet Controller

- **ID vendor:devive:** 8086:100e

- **Kernel driver in use:** e1000

### Latihan 2.B

Tentukan device root filesystem dengan findmnt /. Lalu cocokkan dengan lsblk -f dan tuliskan tipe filesystem serta UUID-nya.

- **Device root filesystem:** /dev/mapper/ubuntu--vg-ubuntu--lv

- **Tipe filesystem:** ext4

- **UUID:** 84dfdc9d-20d1-41c8-b024-17baca0cb5b7

### Latihan 2.C
Buat file server.log berisi minimal 10 baris dengan variasi kata: INFO WARN, ERROR. Gunakan grep untuk menampilkan hanya baris ERROR.

- <img src="Screenshot 2026-02-24 204551.png" width="70%">

### Latihan 2.D
Gunakan sed untuk mengganti semua kata server menjadi node pada file latihan. Tunjukkan sebelum dan sesudah.

- Sebelum: 

- <img src="Screenshot 2026-02-24 205021.png" width="70%">

- Sesudah: 

- <img src="Screenshot 2026-02-24 204815.png" width="70%">

### Latihan 2.E
Gunakan df -h lalu awk untuk menampilkan filesystem yang penggunaan disk di atas 70%

- <img src="Screenshot 2026-02-24 200511.png" width="70%">

### Latihan 2.F
Jalankan sleep 600 &. Temukan PID-nya dengan ps. Hentikan dengan SIGTERM. Jelaskan beda SIGTERM vs SIGKILL.

- <img src="Screenshot 2026-02-24 201247.png" width="70%">

Perbedaan SIGTERM dan SIGKILL
- SIGTERM (15): Menghentikan proses secara normal (graceful), memberi kesempatan menyimpan data.

- SIGKILL (9): Menghentikan proses secara paksa dan langsung, tidak bisa ditolak oleh proses.

### Latihan 2.G
Gunakan systemctl –failed. Jika tidak ada yang gagal, pilih satu service aktif (misal ssh) dan tampilkan status serta 30 baris log terakhirnya.

- <img src="Screenshot 2026-02-24 202632.png" width="70%">
- <img src="Screenshot 2026-02-24 202756.png" width="70%">
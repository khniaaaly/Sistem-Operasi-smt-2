# Laporan Pertemuan 1 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Latihan!

### Latihan Konseptual

#### Latihan 1.1 
Jelaskan 5 fungsi utama sistem operasi dengan contoh konkret dari minimal 2 OS berbeda (Windows, macOS, atau Linux).

#### Jawaban Latihan 1.1
5 fungsi utama sistem operasi yaitu:

**1. Process Management**
Process Management adalah fungsi sistem operasi untuk mengatur semua proses atau program yang sedang berjalan di dalam sistem, mulai dari menentukan proses mana yang mendapat CPU time, membuat dan mengakhiri proses, mengkoordinasi multiple processes, dan Memfasilitasi komunikasi antar proses. 

Contoh implementasi: Windows, Task Manager menampilkan proses yang berjalan dan penggunaan sumber daya, sedangkan di linux, perintah ps, top, dan htop untuk memantau proses.

**2. Memory Management**
Memory management adalah fungsi sistem operasi dalam mengelola penggunaan memori utama (RAM). Fungsi memory management yaitu memberikan memori ke proses yang membutuhkan, menggunakan disk sebagai extension dari RAM, mencegah satu proses mengakses memori proses lain, teknik untuk optimasi penggunaan memori. 

Contoh implementasi: Microsoft Windows terdapat pagefile sebagai virtual memory, sedangkan pada Linux digunakan swap space.

**3. File Management**
File management berfungsi untuk mengatur penyimpanan dan pengorganisasian data dalam bentuk file dan direktori. Sistem operasi menyediakan struktur hierarki (folder dan subfolder), serta operasi dasar seperti membuat, membaca, menulis, dan menghapus file.

Contoh implementasi: Windows menggunakan sistem file NTFS, sedangkan macOS menggunakan APFS

**4. I/O Management**
I/O management adalah fungsi sistem operasi dalam mengatur perangkat input dan output seperti keyboard, mouse, printer, dan disk. Sistem operasi menggunakan device driver untuk berkomunikasi dengan perangkat keras, serta mengatur buffering, interrupt handling, dan spooling.

Contoh implementasi: Pada Microsoft Windows, pengelolaan perangkat dapat dilihat melalui Device Manager. Sementara pada Ubuntu(linux), perangkat dapat dicek melalui perintah seperti lsusb atau lspci.

**5. Security dan Protection**
Security dan protection adalah fungsi sistem operasi untuk menjaga sistem dan data dari akses yang tidak sah. Hal ini mencakup authentication (verifikasi identitas pengguna), authorization (pengaturan hak akses), encryption (enkripsi data), dan auditing (pencatatan aktivitas sistem).

Contoh implementasi: Pada Microsoft Windows terdapat fitur BitLocker untuk enkripsi disk, sedangkan pada macOS terdapat FileVault. Pada Ubuntu, keamanan diterapkan melalui sistem permission (rwx) dan penggunaan perintah sudo.

#### Latihan 1.2
Kapan sebaiknya menggunakan Windows vs Linux vs macOS? Analisis berdasarkan use case: gaming, development, server, creative work, dan enterprise.

#### Jawaban Latihan 1.2
- Gaming

Sistem operasi yang paling direkomendasikan adalah Microsoft Windows. Windows memiliki dukungan game paling lengkap, kompatibilitas hardware terbaik (GPU, driver), serta mayoritas game dikembangkan dengan prioritas untuk Windows (DirectX support). Selain itu, hampir semua launcher populer dan game AAA tersedia secara native di Windows. Sementara itu, Ubuntu (Linux) mulai berkembang dengan adanya Steam Proton, tetapi masih belum sepenuhnya kompatibel untuk semua game. macOS kurang direkomendasikan untuk gaming karena pilihan game lebih terbatas dan tidak menjadi fokus utama Apple.

- Development

Pilihan terbaik biasanya adalah Linux atau macOS. Linux populer karena bersifat open source, fleksibel, dan banyak digunakan di lingkungan server sehingga memudahkan developer dalam menyesuaikan lingkungan development dengan lingkungan produksi. macOS juga unggul karena berbasis Unix (POSIX compliant), sehingga mendukung banyak tools development berbasis Unix sekaligus menyediakan antarmuka grafis yang stabil. Windows tetap relevan, terutama untuk pengembangan aplikasi berbasis .NET, enterprise software, dan game development, serta kini didukung fitur seperti WSL yang memungkinkan penggunaan lingkungan Linux di dalam Windows.

- Server

Linux merupakan sistem operasi yang paling dominan. Sebagian besar server, cloud computing, dan supercomputer menggunakan Linux karena stabil, aman, ringan, dan tidak memerlukan biaya lisensi. Windows juga memiliki Windows Server yang digunakan di lingkungan enterprise, khususnya pada perusahaan yang menggunakan ekosistem Microsoft seperti Active Directory. Sementara itu, macOS jarang digunakan sebagai sistem operasi server dalam skala besar.

- Creative work

Untuk pekerjaan kreatif seperti desain grafis, video editing, dan produksi audio, macOS sering menjadi pilihan utama. Hal ini karena integrasi hardware dan software yang sangat optimal serta kestabilan sistem yang tinggi. Banyak profesional kreatif memilih macOS untuk pekerjaan multimedia. Windows juga merupakan alternatif yang kuat karena mendukung berbagai software kreatif populer dan konfigurasi hardware yang fleksibel. Linux masih kurang dominan di industri kreatif karena dukungan software profesional belum selengkap Windows dan macOS.

- Enterprise

Windows banyak digunakan pada desktop karena memiliki integrasi yang kuat dengan sistem manajemen jaringan, kebijakan pengguna (Group Policy), serta software bisnis. Di sisi lain, Linux banyak digunakan pada server enterprise dan infrastruktur cloud karena stabilitas dan keamanannya. macOS biasanya digunakan di perusahaan kreatif atau startup teknologi yang membutuhkan ekosistem Apple.

### Latihan Praktikal

#### Latihan 1.3

Install Ubuntu Server 22.04 LTS di VirtualBox dengan langkah berikut:
1. Download Ubuntu Server ISO dari website resmi
2. Create VM baru di VirtualBox (RAM: 2GB, Disk: 25GB)
3. Install dengan automatic partitioning (guided)
4. Buat user account dengan password yang kuat
5. Reboot dan login ke sistem
6. Dokumentasikan proses instalasi dengan screenshot key steps

#### Jawaban Latihan 1.3

1. <img src="Screenshot 2026-02-24 211849.png" width="70%"> 
2. <img src="Screenshot 2026-02-24 211915.png" width="70%"> 

#### Latihan 1.4

Setelah instalasi Ubuntu Server, lakukan tasks berikut:
1. Update package list: sudo apt update
2. Upgrade packages: sudo apt upgrade
3. Install neofetch: sudo apt install neofetch
4. Jalankan neofetch dan screenshot hasilnya
5. Check disk usage dengan df -h
6. Check memory dengan free -h
7. Dokumentasikan output dari setiap command

#### Jawaban Latihan 1.4

1. <img src="Screenshot 2026-02-24 212728.png" width="70%"> 
2. <img src="Screenshot 2026-02-24 213350.png" width="70%"> 
3. <img src="Screenshot 2026-02-24 213804.png" width="70%"> 
4. <img src="Screenshot 2026-02-24 214453.png" width="70%"> 
5. <img src="Screenshot 2026-02-24 214524.png" width="70%"> 
6. <img src="Screenshot 2026-02-24 214727.png" width="70%"> 

#### Latihan 1.5

Eksplorasi sistem yang baru diinstall:
1. Tampilkan informasi OS: cat /etc/os-release
2. Tampilkan versi kernel: uname -r
3. List partisi: lsblk
4. Check network connectivity: ping -c 4 google.com
5. Install dan jalankan htop untuk melihat resource usage
6. Buat laporan singkat tentang konfigurasi sistem Anda

#### Jawaban Latihan 1.5

1. <img src="Screenshot 2026-02-24 214842.png" width="70%"> 
2. <img src="Screenshot 2026-02-24 214905.png" width="70%"> 
3. <img src="Screenshot 2026-02-24 214928.png" width="70%"> 
4. <img src="Screenshot 2026-02-24 215003.png" width="70%"> 
5. <img src="Screenshot 2026-02-24 215344.png" width="70%"> 
6. Sistem yang digunakan adalah Linux Ubuntu dengan arsitektur 64-bit. Kernel yang digunakan sesuai dengan hasil perintah uname -a. Prosesor memiliki beberapa core yang dapat dilihat melalui lscpu. Total RAM yang tersedia dapat dilihat menggunakan free -h, beserta penggunaan swap. Kapasitas penyimpanan dan penggunaan disk ditampilkan melalui df -h. Berdasarkan hasil monitoring menggunakan htop, sistem menunjukkan penggunaan CPU dan RAM dalam kondisi normal tanpa proses berat yang berjalan. Hal ini menandakan sistem berjalan stabil.

### Latihan Refleksi

#### Latihan 1.6

Ceritakan pengalaman Anda dengan sistem operasi:
1. Sistem operasi apa yang Anda gunakan sehari-hari? (Windows, macOS,
Linux, atau lainnya)
2. Berapa lama Anda menggunakan sistem operasi tersebut?
3. Apa yang Anda sukai dari sistem operasi tersebut?
4. Apa tantangan atau masalah yang pernah Anda hadapi?
5. Apakah Anda pernah menggunakan sistem operasi lain? Bandingkan
pengalaman Anda.
6. Setelah mempelajari bab ini, apakah ada sistem operasi lain yang ingin
Anda coba? Mengapa?
Tulis refleksi Anda dalam 300-500 kata disertai dengan dokumentasi.

#### Jawaban Latihan 1.6

Sistem operasi yang saya gunakan sehari-hari adalah Microsoft Windows. Saya telah menggunakan Windows sejak duduk di bangku sekolah dasar hingga sekarang di perkuliahan, sehingga kurang lebih sudah lebih dari 7 tahun. Windows menjadi sistem operasi yang paling familiar bagi saya karena hampir semua perangkat komputer di sekolah maupun di rumah menggunakan sistem operasi ini.

Hal yang saya sukai dari Windows adalah tampilannya yang mudah dipahami (user friendly) serta kompatibilitas software yang sangat luas. Hampir semua aplikasi perkantoran, aplikasi desain, hingga software pemrograman dapat berjalan dengan baik di Windows. Selain itu, Windows juga mendukung banyak perangkat keras sehingga jarang mengalami masalah kompatibilitas. Untuk kebutuhan sehari-hari seperti mengerjakan tugas, browsing, menonton video, hingga instalasi aplikasi kampus, Windows sangat memudahkan.

Namun, saya juga pernah menghadapi beberapa tantangan saat menggunakan Windows. Salah satunya adalah sistem yang terkadang menjadi lambat setelah pembaruan (update). Selain itu, Windows juga cukup rentan terhadap virus jika tidak menggunakan antivirus atau tidak berhati-hati saat menginstal aplikasi. Masalah lain yang pernah saya alami adalah penggunaan RAM yang cukup besar ketika banyak aplikasi dibuka secara bersamaan.

Saya juga pernah mencoba menggunakan Ubuntu dalam praktikum sistem operasi. Pengalaman menggunakan Linux cukup berbeda dibandingkan Windows. Linux terasa lebih ringan dan stabil, terutama saat digunakan di komputer dengan spesifikasi menengah ke bawah. Namun, bagi pemula, penggunaan terminal dan perintah command line terasa sedikit menantang. Dibandingkan Windows, Linux lebih fleksibel dan banyak digunakan pada server, tetapi dari sisi kemudahan penggunaan sehari-hari, Windows masih terasa lebih praktis bagi saya.

Setelah mempelajari bab tentang sistem operasi, saya menjadi tertarik untuk mencoba macOS. Saya ingin merasakan bagaimana integrasi antara hardware dan software yang sering disebut lebih stabil dan optimal, terutama untuk kebutuhan desain dan pengembangan aplikasi. Selain itu, saya juga ingin lebih mendalami Linux karena banyak digunakan dalam dunia server dan cloud computing, yang relevan dengan bidang teknologi informasi.

Secara keseluruhan, setiap sistem operasi memiliki kelebihan dan kekurangan masing-masing. Pengalaman ini membuat saya memahami bahwa pemilihan sistem operasi harus disesuaikan dengan kebutuhan pengguna.

<img src="Screenshot (261).png" width="70%"> 
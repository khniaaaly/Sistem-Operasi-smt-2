# Laporan Pertemuan 10 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Praktikum 10.1 - Melihat Penggunaan Memori
Langkah 1: Jalankan free -h untuk melihat ringkasan RAM dan swap.

<img src="Screenshot 2026-05-03 091302.png" width="70%"> 

Langkah 2: Lihat detail memori dari kernel melalui /proc/meminfo.

<img src="Screenshot 2026-05-03 091359.png" width="70%"> 

### Analisis
1. Hitung persentase memori tersedia: available / total × 100%. Jika hasilnya di bawah 10%, sistem mulai kekurangan memori.
2. Pada baris Swap, apakah kolom used bernilai 0? Jika lebih dari 0, kernel sudah pernah memindahkan data ke disk karena RAM tidak cukup.
3. Perhatikan field Cached dan Buffers di /proc/meminfo. Nilai ini sesuai dengan kolom buff/cache pada free -h.

### Jawaban Analisis
1. 1,6/1,9*100% = 84,2%, hasil > 10%
2. Ya, kolom used bernilai 0
3. Dari /proc/meminfo:
   - Buffers = 17764 kB (~17 MB)
   - Cached = 246944 kB (~241 MB)

   Total = 258 MB (setara dengan 274 Mi pada free -h)
   
   Dari free -h:
   - buff/cache = 274 Mi

   Nilai Buffers + Cached sesuai dengan buff/cache.

## Studi Kasus 10.1 Server Lambat karena Memori
Langkah 1: Periksa kondisi memori secara keseluruhan.

<img src="Screenshot 2026-05-03 091603.png" width="70%"> 

Langkah 2: Pantau proses secara real-time

<img src="Screenshot 2026-05-03 091627.png" width="70%"> 

### Analisis
1. Apakah nilai available sangat kecil (misalnya di bawah 200 MB pada server dengan RAM 2 GB)? Jika ya, server kemungkinan kekurangan memori.
2. Apakah kolom used pada baris Swap lebih dari 0? Jika ya, kernel sedang menggunakan swap, yang berarti performa menurun.
3. Di tampilan top, proses apa yang memiliki %MEM terbesar? Proses tersebut menjadi kandidat utama penyebab lambatnya server.

### Jawaban Analisis
1. Available = 1.6 GB, server dalam kondisi normal
2. Used = 0, performa masih optimal
3. Dari tampilan top:
   - systemd = 0.7% (terbesar)

   Tidak ada proses yang boros memori → sistem ringan.

## Praktikum 10.2 Mengamati Aktivitas Paging
Langkah 1: Jalankan vmstat dengan interval 1 detik, 5 sampel

<img src="Screenshot 2026-05-03 091748.png" width="70%"> 

### Analisis
1. Amati nilai si dan so pada kelima baris. Pada sistem normal dengan RAM cukup, kedua nilai ini selalu 0.
2. Jika nilai si atau so sesekali muncul lebih dari 0, artinya pernah ada aktivitas swap. Ini masih wajar jika tidak terus-menerus.
3. Jika si dan so terus-menerus lebih dari 0, sistem dalam kondisi memory pressure serius — performa turun drastis karena akses disk jauh lebih lambat dari RAM.
4. Perhatikan juga kolom free (RAM kosong) dan buff (buffer) untuk memahami kondisi keseluruhan RAM saat itu.

### Jawaban Analisis
1. Dari vmstat nilai si dan so sama-sama 0, yang artinya tidak ada aktivitas swap.
2. tidak ada nilai yang muncul lebih dari 0.
3. Hal tersebut tidak terjadi, jadi sistem sangat stabil.
4. Kondisi RAM (vmstat)
   - free ≈ 1.48 GB
   - buff ≈ 18 MB
   - cache ≈ 301 MB

   kondisi memori sangat sehat.

## Praktikum 10.3 Membuat dan Mengonfigurasi Swap File
Langkah 1: Buat file berukuran 512 MB sebagai calon swap.

<img src="Screenshot 2026-05-03 091926.png" width="70%"> 

Langkah 2: Atur permission file menjadi 600 — hanya root yang boleh membaca dan menulis.

<img src="Screenshot 2026-05-03 092013.png" width="70%"> 

Langkah 3: Format file sebagai area swap, lalu aktifkan

<img src="Screenshot 2026-05-03 092126.png" width="70%"> 

Langkah 4: Verifikasi swap aktif. Anda akan melihat entri /swapfile-week10 dengan ukuran 512M, dan nilai total pada baris Swap di free -h bertambah 512M.

<img src="Screenshot 2026-05-03 092353.png" width="70%"> 

Langkah 5: Periksa nilai swappiness, ubah sementara, dan verifikasi perubahan.

<img src="Screenshot 2026-05-03 092514.png" width="70%"> 

### Analisis
1. Berapa nilai swappiness default? Apa artinya bagi perilaku kernel dalam menggunakan swap?
2. Setelah diubah ke 10, konfirmasi nilai berubah pada output cat kedua. Apa dampak nilai 10 terhadap penggunaan swap dibanding nilai 60?
3. Apakah entri /swapfile-week10 muncul di swapon –show? Jika tidak, pastikan Langkah 2 (chmod 600) sudah dijalankan sebelum Langkah 3.

### Jawaban Analisis
1. Nilai swappiness default: 60, arti bagi kerner yaitu Nilai 60 berarti kernel cukup agresif dalam menukar data dari RAM ke swap untuk menjaga ketersediaan disk cache.
2. Konfirmasi output: 10, dampaknya, dengan nilai 10, kernel akan meminimalisir penggunaan swap dan lebih mengutamakan penggunaan RAM fisik selama mungkin. Ini meningkatkan performa jika RAM masih tersedia.
3. Ya, dengan ukuran 512 MB

   Karena file aktif, berarti langkah chmod 600 telah berhasil dijalankan sebelumnya.

## Praktikum 10.4 Monitoring Memory
Langkah 1: Ambil snapshot proses diurutkan dari penggunaan memori terbesar.

<img src="Screenshot 2026-05-03 092606.png" width="70%"> 

Langkah 2: Pantau secara real-time dengan top.

<img src="Screenshot 2026-05-03 092656.png" width="70%"> 

### Analisis
1. Proses apa yang berada di urutan pertama? Catat nilai %MEM dan RSS-nya.
2. Konversikan RSS dari KB ke MB (bagi 1024). Misalnya, RSS=524288 berarti proses menggunakan 512 MB RAM. Apakah wajar untuk jenis program tersebut?
3. Mengapa VSZ selalu lebih besar dari RSS pada proses yang sama?
4. Apakah urutan proses di ps konsisten dengan tampilan top saat diurutkan berdasarkan %MEM?

### Jawaban Analisis
1. proses di urutan pertama adalah: /sbin/multipathd -d -s
   - %MEM = 1.3
   - RSS = 27452 KB
2. 27452/1024 ≈ 26.8 MB, Untuk proses seperti multipathd, penggunaan 27 MB RAM masih wajar.
3. VSZ lebih besar karena mencakup seluruh memori virtual yang dialokasikan proses, termasuk yang belum digunakan, shared library, dan mapping file. RSS hanya menghitung memori yang benar-benar ada di RAM, sehingga nilainya lebih kecil.
4. Secara teori urutannya sama karena sama-sama berdasarkan %MEM. Namun bisa berbeda karena ps adalah snapshot sesaat, sedangkan top bersifat real-time dan terus diperbarui.

## Praktikum 10.5 Script Monitor Memor
Langkah 1: Masuk ke direktori kerja dan buat file script:

<img src="Screenshot 2026-05-04 182252.png" width="70%">
<img src="Screenshot 2026-05-04 182312.png" width="70%">  

Langkah 2: Ketik script berikut:

<img src="Screenshot 2026-05-04 182851.png" width="70%"> 
<img src="Screenshot 2026-05-04 182909.png" width="70%"> 

### Analisis
1. Variabel THRESHOLD=20 menetapkan batas persentase. Perintah free | awk ’/Mem/ {printf "%d", $7/$2*100}’ mengambil kolom ke-7 (available) dibagi kolom ke-2 (total) dari baris Mem, lalu dikalikan 100 untuk menghasilkan persentase bilangan bulat.
2. Kondisi if [ "$AVAIL" -lt "$THRESHOLD" ] bernilai benar jika persentase memori tersedia di bawah 20.
3. Ubah THRESHOLD menjadi 90 dan jalankan ulang. Apa yang berubah pada output? Mengapa demikian?

### Jawaban Analisis
1. THRESHOLD=20 adalah batas minimum memori. Perintah free | awk menghitung persentase memori tersedia dari available / total × 100.
2. Kondisi if akan benar jika AVAIL < THRESHOLD.
   - Jika benar → tampil peringatan
   - Jika salah → status normal
3. <img src="Screenshot 2026-05-05 163658.png" width="70%">
   
   Jika THRESHOLD diubah menjadi 90, maka output akan berubah menjadi peringatan. Semakin besar threshold, semakin mudah muncul peringatan.

## Studi Kasus 10.2 Gagal Akses File
Langkah 1: Buat direktori dan file konfigurasi contoh.

<img src="Screenshot 2026-05-04 183402.png" width="70%"> 

Langkah 2: Simulasikan permission bermasalah.

<img src="Screenshot 2026-05-04 183536.png" width="70%"> 

Langkah 3: Kembalikan permission dan verifikasi.

<img src="Screenshot 2026-05-04 183612.png" width="70%"> 

### Analisis
1. Mengapa cat menghasilkan Permission denied setelah chmod 000? System call apa yang gagal?
2. Apa perbedaan pesan error Permission denied vs No such file or directory? Coba rm app.conf lalu cat app.conf untuk melihat perbedaannya.
3. Permission 644 berarti apa untuk owner, group, dan others?

### Jawaban Analisis
1. Perintah chmod 000 mencabut semua hak akses, sehingga kernel menolak permintaan untuk membuka file. System Call yang gagal pada tahap open() karena tidak ada izin baca (read), sehingga proses tidak bisa berlanjut ke tahap read().
2. Perbedaan pesan error Permission denied vs No such file or directory
   - Permission denied: File ada, tetapi Anda dilarang mengaksesnya (contoh: setelah chmod 000).
   - No such file or directory: File tidak ada atau sudah dihapus (contoh: setelah rm app.conf).
3. Angka 644 membagi izin sebagai berikut:
   - Owner (6): Bisa membaca dan mengubah file (Read & Write).
   - Group (4): Hanya bisa membaca (Read Only).
   - Others (4): Hanya bisa membaca (Read Only).

## Praktikum 10.6 Mengamati System Call dengan strace
Langkah 1: Lihat 30 baris pertama system call dari perintah ls.

<img src="Screenshot 2026-05-04 183725.png" width="70%"> 

Langkah 2: Lihat ringkasan statistik dan bandingkan dua direktori berbeda.

<img src="Screenshot 2026-05-04 183846.png" width="70%"> 

### Analisis
1. Dari output Langkah 1, identifikasi minimal 4 system call berbeda. Jelaskan fungsi singkat masing-masing berdasarkan argumen yang terlihat.
2. Dari ringkasan strace -c, system call mana yang paling sering dipanggil? Mengapa?
3. Apakah ada system call dengan errors lebih dari 0? Apakah itu berarti program bermasalah, ataukah bagian normal dari logika program?
4. Apakah jumlah system call berbeda antara ls dan ls /etc? Faktor apa yang menyebabkan perbedaan tersebut?

### Jawaban Analisis
1. Berikut adalah 4 system call beserta fungsinya:
   - **execve**: Menjalankan program (dalam kasus ini /usr/bin/ls).
   - **brk**: Mengatur batas memori (heap) untuk alokasi data.
   - **mmap**: Memetakan file atau library ke memori.
   - **openat**: Membuka file untuk dibaca atau ditulis.
2. system call yang paling sering dipanggil adalah mmap dengan total 18 panggilan. Karena Perintah ls memerlukan banyak library sistem agar dapat berjalan (seperti libc, libselinux, dll). Setiap library ini perlu dipetakan ke dalam ruang alamat memori proses menggunakan mmap.
3. Ya, terdapat system call dengan jumlah error lebih dari 0, yaitu:
   - access: 2 errors.
   - statfs: 2 errors.

   Ini adalah bagian normal dari logika program. Sistem sering mencoba mengecek keberadaan file konfigurasi opsional (seperti ld.so.preload) yang mungkin tidak ada tanpa merusak jalannya program.
4. Terdapat perbedaan jumlah total system call antara kedua perintah tersebut:
   - strace -c ls: Memanggil total 75 system call.
   - strace -c ls /etc: Memanggil total 74 system call.

   Perbedaan disebabkan oleh jumlah file dan atribut di dalam direktori yang dibaca, yang mempengaruhi frekuensi system call untuk membaca konten direktori seperti getdents64 atau statx.

## Tugas Praktikum
### Tugas 10.1 Audit Penggunaan Memori Sistem

<img src="Screenshot 2026-05-04 185213.png" width="70%">

#### Analisis
1. Hitung persentase memori tersedia (available / total × 100%). Apakah sistem dalam kondisi normal?
2. Mengapa buff/cache tidak dihitung sebagai memori yang terpakai dari sudut pandang ketersediaan untuk aplikasi?
3. Dari /proc/meminfo, apakah SwapTotal lebih besar dari 0? Berapa nilai SwapFree?

#### Jawaban Analisis
1. 1,6/1,9 * 100% = 84,2%, sistem tersebut berada dalam kondisi normal, karena available jauh di atas 10%.
2. Karena buff/cache digunakan Linux untuk menyimpan cache file dan buffer I/O agar akses data lebih cepat. Memori ini bisa dibebaskan otomatis saat aplikasi membutuhkan RAM. Artinya walaupun terlihat “used”, buff/cache sebenarnya masih bisa dipakai kembali.
3. Ya, SwapTotal lebih besar dari 0, artinya sistem memiliki swap aktif.
Berdasarkan /proc/meminfo:
   - SwapTotal = 2621432 kB (≈ 2.5 GB)
   - SwapFree = 2621432 kB (≈ 2.5 GB)

### Tugas 10.2 Identifikasi Proses dengan Memori Tertinggi

<img src="Screenshot 2026-05-04 185526.png" width="70%"> 

#### Analisis
1. Proses apa di urutan pertama? Catat nilai %MEM dan RSS.
2. Konversikan RSS ke MB (bagi 1024). Apakah wajar?
3. Jumlahkan %MEM dari 5 proses teratas. Berapa persen RAM yang mereka gunakan bersama?

#### Jawaban Analisis
1. Proses pertama = /sbin/multipathd -d -s
   - %MEM = 1.3
   - RSS = 27452 KB
2. 27452/1024 = 26.8 MB, Nilai tersebut wajar, karena multipathd adalah service sistem linux untuk manajemen storage
3. 1.3 + 1.1 + 0.8 + 0.6 + 0.6 = 4.4% RAM yang digunakan.

### Tugas 10.3 Membuat dan Memverifikasi Swap File

<img src="Screenshot 2026-05-04 190535.png" width="70%"> 

#### Analisis
1. Identifikasi kolom NAME, TYPE, SIZE, dan USED pada output swapon –show.
2. Apakah nilai total pada baris Swap di free -h bertambah 256 MB?
3. Mengapa permission 600 penting? Apa risiko jika diatur ke 644?

#### Jawaban Analisis
1. - /swap.img - file - 2G - 0B
   - /swapfile-week10 - file - 512M - 0B
   - /swapfile-tugas-week10 - file - 256M - 0B
2. Ya, Swap bertambah 256 MB, sesuai ukuran file yang dibuat.
3. Permission 600 penting karena swap file dapat menyimpan data sementara dari RAM yang bersifat sensitif. Dengan pengaturan ini, hanya root yang bisa membaca dan menulis file tersebut sehingga lebih aman. Jika menggunakan 644, user lain bisa membaca isi swap file, yang berisiko menyebabkan kebocoran data dari sistem.

### Tugas 10.4 Analisis System Call dengan strace

<img src="Screenshot 2026-05-05 170027.png" width="70%"> 
<img src="Screenshot 2026-05-05 170043.png" width="70%"> 

#### Analisis
1. Sebutkan minimal 5 system call dari strace-summary.txt beserta fungsi singkatnya.
2. System call mana yang paling sering dipanggil? Mengapa?
3. Apakah ada errors lebih dari 0? Apakah program tetap berjalan normal meskipun ada kegagalan tersebut?

#### Jawaban Analisis
1. Berikut adalah 5 system call yang terdaftar dalam ringkasan tersebut beserta fungsi singkatnya:
   - **read**: Membaca data dari deskriptor file (seperti membaca isi file ke memori).
   - **write**: Menulis data ke deskriptor file (seperti menampilkan teks ke terminal).
   - **close**: Menutup deskriptor file yang sebelumnya dibuka agar sumber daya sistem dapat dilepaskan.
   - **mmap**: Memetakan file atau perangkat ke dalam ruang alamat memori proses (sering digunakan untuk memuat library).
   - **execve**: Mengeksekusi program atau skrip (dalam hal ini memulai perintah ls).
2. System call mmap, yaitu sebanyak 18 kali.

   Program ls perlu memuat berbagai shared libraries (perpustakaan sistem) agar bisa berjalan. Setiap library ini dipetakan ke memori menggunakan mmap. Selain itu, mmap juga digunakan untuk alokasi memori awal saat proses baru dimulai.
3. Ya, terdapat total 4 errors dalam ringkasan tersebut. Error terjadi pada system call access (2 error) dan statfs (2 error).

   Program tetap berjalan normal. Error tersebut bukanlah kegagalan fatal. Hal ini biasanya terjadi karena bagian dari logika program atau loader sistem mencoba mencari file konfigurasi di beberapa lokasi berbeda

### Tugas 10.5 Studi Kasus Diagnosa Server Lambat

<img src="Screenshot 2026-05-05 180939.png" width="70%"> 

#### Analisis
1. Jelaskan peran masing-masing fungsi: cek_memori, cek_swap, cek_proses, cek_paging, dan ringkasan. Mengapa diagnosa dipecah menjadi fungsi terpisah?
2. Berdasarkan bagian RINGKASAN, apakah kondisi sistem normal atau kritis? Jelaskan berdasarkan nilai threshold yang digunakan script.
3. Mengapa script menggunakan tee "$LAPORAN" bukan redirection biasa > "$LAPORAN"? Apa keuntungannya?
4. Dari output cek_paging, apakah ada aktivitas si atau so? Jika ada, apa implikasinya terhadap performa server?

#### Jawaban Analisis
1. Meskipun script dijalankan sebagai satu kesatuan, outputnya menunjukkan struktur fungsi berikut:
   - **cek_memori**: Menampilkan kondisi RAM (total, used, free, available) menggunakan perintah free -h.
   - **cek_swap**: Menunjukkan daftar file swap yang aktif beserta kapasitas dan penggunaannya melalui perintah swapon --show.
   - **cek_proses**: Mengidentifikasi 10 proses yang mengonsumsi memori (RSS) paling tinggi menggunakan ps aux.
   - **cek_paging**: Memantau aktivitas I/O memori (swap-in/swap-out) dan statistik CPU menggunakan vmstat.
   - **ringkasan**: Memberikan kesimpulan cepat mengenai status kesehatan sistem.

   Pemisahan ini menerapkan prinsip modularitas. Hal ini memudahkan pemeliharaan kode (debugging), memungkinkan penggunaan ulang fungsi tertentu di script lain, dan membuat laporan lebih terstruktur serta mudah dibaca oleh admin sistem.
2. Penjelasan berdasarkan Threshold:
   
   Memori (Normal): Nilai memori available (1,6Gi) jauh lebih besar dibandingkan memori used (318Mi). Berdasarkan logika script serupa sebelumnya, status normal diberikan jika memori tersedia di atas threshold (misalnya 20%).
3. Script menggunakan perintah | tee "$LAPORAN" karena memiliki keuntungan ganda:
   - Dual Output: Hasil diagnosa ditampilkan secara real-time di terminal (layar) sekaligus disimpan ke dalam file diagnosa-server-lambat.txt.
   - edirection biasa (>): Hanya akan mengirimkan output ke dalam file, sehingga layar terminal akan kosong selama proses berlangsung. Admin tidak bisa melihat progres diagnosa secara langsung.
4. Berdasarkan tabel Aktivitas Paging (5 Sampel):
   - Data si (swap-in): Menunjukkan nilai 0 pada semua sampel.
   - Data so (swap-out): Menunjukkan nilai 0 pada semua sampel.

   Implikasi terhadap Performa: Karena tidak ada aktivitas si (membaca dari swap ke RAM) maupun so (menulis dari RAM ke swap), performa server saat ini berada pada titik optimal. Tidak adanya aktivitas paging berarti server tidak mengalami memory pressure. Jika nilai ini tinggi, server akan melambat secara signifikan (thrashing) karena kecepatan baca-tulis disk jauh lebih lambat daripada RAM fisik.
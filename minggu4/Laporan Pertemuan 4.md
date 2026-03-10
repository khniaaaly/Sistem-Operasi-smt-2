# Laporan Pertemuan 4 (Sistem Operasi)

<h4>Nama : Khaniaa Puji Auliya<h4>
<h4>NIM : 254107020236<h4>
<h4>Kelas : TI-1G<h4>

## Tugas Pendahuluan
Jawablah pertanyaan-pertanyaan di bawah ini:
1. Apa yang dimaksud perintah-perintah direktory: pwd, cd, mkdir, rmdir.
2. Apa yang dimaksud preintah-perintah manipulasi file: cp, mv dan rm (sertakan format yang digunakan)
3. Jelaskan perbedaan *symbolic link* menggunakan *hard link (direct)* dan *soft link (indirect)*
4. Tuliskan maksud perintah-perintah: file, find, which, locate, dan grep.

Jawab:
1. Perintah-perintah direktori
   - **pwd (pirnt working directory):** Perintah untuk menampilkan direktori aktif saat ini atau lokasi folder tempat kita sedang berada
   - **cd (change directory):** Perintah untuk berpindah dari satu direktori ke direktori lain.
   - **mkdir (make directory):** Perintah untuk membuat direktori/folder baru.
   - **rmdir (remove directory):** Perintah untuk menghapus direktori yang kosong.

2. Perintah-perintah manipulasi file
   - **cp (copy):** Perintah untuk menyalin file atau direktori. Format: cp sumber tujuan
   - **mv (move):** Perintah untuk memindahkan atau mengganti nama file/direktori. Format: mv sumber tujuan
   - **rm (remove):** Perintah untuk menghapus file atau direktori. Format: rm nama_file

3. Perbedaan Hard Link dan Soft Link
   - **Hard Link (direct):** Merupakan salinan langsung dari inode file asli, Jika file asli dihapus, hard link masih bisa digunakan, Tidak bisa digunakan untuk direktori, Tidak bisa lintas partisi.

   - **Soft Link / Symbolic Link (indirect):** Merupakan file khusus yang berisi alamat/path file asli, Jika file asli dihapus, soft link menjadi rusak (broken link), Bisa digunakan untuk direktori, Bisa lintas partisi.

4. Maksud perintah-perintah
   - **file:** Untuk mengetahui tipe atau jenis suatu file.
   - **find:** Untuk mencari file atau direktori berdasarkan nama, tipe, atau kriteria tertentu di dalam direktori tertentu.
   - **which:** Untuk mengetahui lokasi file program/perintah yang akan dijalankan oleh sistem.
   - **locate:** Untuk mencari file dengan cepat berdasarkan database sistem.
   - **grep:** Untuk mencari teks atau pola tertentu di dalam file.

## Latihan:
1.	Cobalah urutan perintah berikut :
- $ cd
- $ pwd
- $ ls –al
- $ cd .
- $ pwd
- $ cd ..
- $ pwd
- $ ls -al
- $ cd ..
- $ pwd
- $ ls -al
- $ cd /etc
- $ ls –al | more
- $ cat passwd
- $ cd –
- $ pwd

<img src="Screenshot 2026-03-10 111221.png" width="70%"> 
<img src="Screenshot 2026-03-10 111409.png" width="70%"> 
<img src="Screenshot 2026-03-10 111510.png" width="70%"> 
<img src="Screenshot 2026-03-10 111725.png" width="70%">

2.	Lanjutkan penelusuran pohon pada sistem file menggunakan cd, ls, pwd dan cat. Telusuri direktory /bin, /usr/bin, /sbin, /tmp dan /boot.

<img src="Screenshot 2026-03-10 112830.png" width="70%">

cd / pwd ls

<img src="Screenshot 2026-03-10 112918.png" width="70%"> 

cd /bin ls

<img src="Screenshot 2026-03-10 113006.png" width="70%"> 

cd /usr/bin ls

<img src="Screenshot 2026-03-10 113036.png" width="70%"> 

cd /sbin ls

<img src="Screenshot 2026-03-10 113117.png" width="70%"> 

cd /tmp ls

<img src="Screenshot 2026-03-10 113146.png" width="70%"> 

cd /boot ls

3.	Telusuri direktory /dev. Identifikasi perangkat yang tersedia. Identifikasi tty (termninal) Anda (ketik who am i); siapa pemilih tty Anda (gunakan ls –l).

<img src="Screenshot 2026-03-10 115256.png" width="70%"> 

4.	Telusuri derectory /proc. Tampilkan isi file interrupts, devices, cpuinfo, meminfo dan uptime menggunakan perintah cat. Dapatkah Anda melihat mengapa directory /proc disebut pseudo -filesystem yang memungkinkan akses ke struktur data kernel ?

interrupts

<img src="Screenshot 2026-03-10 115414.png" width="70%"> 

devices

<img src="Screenshot 2026-03-10 115517.png" width="70%">

cpuinfo

<img src="Screenshot 2026-03-10 115544.png" width="70%">

meminfo

<img src="Screenshot 2026-03-10 115620.png" width="70%">

uptime

<img src="Screenshot 2026-03-10 115720.png" width="70%">

5.	Ubahlah direktory home ke user lain secara langsung menggunakan cd ~username.

<img src="Screenshot 2026-03-10 120443.png" width="70%"> 

6.	Ubah kembali ke direktory home Anda.

<img src="Screenshot 2026-03-10 120521.png" width="70%"> 

7.	Buat subdirektory work dan play.

<img src="Screenshot 2026-03-10 124035.png" width="70%"> 

8.	Hapus subdirektory work.

<img src="Screenshot 2026-03-10 124104.png" width="70%"> 

9.	Copy file /etc/passwd ke direktory home Anda.

<img src="Screenshot 2026-03-10 124154.png" width="70%"> 

10.	Pindahkan ke subirectory play.

<img src="Screenshot 2026-03-10 124331.png" width="70%"> 

11.	Ubahlah ke subdirektory play dan buat symbolic link dengan nama terminal yang menunjuk ke perangkat tty. Apa yang terjadi jika melakukan hard link ke perangkat tty ?

<img src="Screenshot 2026-03-10 125507.png" width="70%"> 

12.	Buatlah file bernama hello.txt yang berisi kata ”hello word”. Dapatkah Anda gunakan ”cp” menggunakan ”terminal” sebagai file asal untuk menghasilkan efek yang sama ?

<img src="Screenshot 2026-03-10 125849.png" width="70%"> 

13.	Copy hello.txt ke terminal. Apa yang terjadi ?

<img src="Screenshot 2026-03-10 125952.png" width="70%"> 

14.	Masih direktory home, copy keseluruhan direktory play ke direktory bernama work menggunakan symbolic link.

<img src="Screenshot 2026-03-10 130035.png" width="70%"> 

15.	Hapus direktory work dan isinya dengan satu perintah

<img src="Screenshot 2026-03-10 130116.png" width="70%"> 

## LAPORAN RESMI
1. Analisa hasil percobaan yang Anda lakukan

    a. Analisa setiap hasil tampilannya.

       Pada praktikum ini dilakukan beberapa percobaan yang berkaitan dengan pengelolaan file dan direktori pada sistem operasi (biasanya Linux). Perintah yang digunakan antara lain: 
       
       pwd (menampilkan direktori kerja saat ini)
       ls (menampilkan daftar file dan direktori yang ada pada direktori aktif)
       mkdir (membuat direktori baru)
       cd (berpindah direktori)
       touch (membuat file baru kosong)
       cp (menyalin file dari satu lokasi ke lokasi lain)
       mv (memindahkan atau mengganti nama file/direktori)
       rm (menghapus file)

    b. Pada Percobaan 1 point 3 buatlah pohon dari struktur file dan direktori.

       Direktori utama : Praktikum 3
       
       Di dalamnya terdapat dua file : file1.txt dan file2.txt

       Terdapat dua subdirektori : direktoriA dan direktoriB

       Masing-masing direktori memiliki file : direktoriA (fileA1.txt, dst.), direktoriB (fileB1.txt, dst.)

    c. Bila terdapat pesan error, jelaskan penyebabnya.

       No such file or directory : Terjadi karena file atau direktori yang dituju tidak ada atau salah penulisan nama.
    
       Permission denied : Terjadi karena pengguna tidak memiliki hak akses untuk membaca, menulis, atau menjalankan file/direktori tersebut.

       File exists : Terjadi ketika mencoba membuat file atau direktori dengan nama yang sudah ada sebelumnya.

       Is a directory : Terjadi ketika mencoba menghapus direktori menggunakan rm tanpa opsi -r

2. Kerjakan latihan diatas dan analisa hasil tampilannya.

   Latihan dilakukan dengan membuat beberapa direktori dan file menggunakan perintah Linux. Hasil tampilannya menunjukkan bahwa setiap perintah yang dijalankan memberikan output sesuai fungsi masing-masing.

3. Berikan kesimpulan dari praktikum ini.

   Berdasarkan praktikum yang telah dilakukan, dapat disimpulkan bahwa pengelolaan file dan direktori merupakan bagian penting dalam penggunaan sistem operasi. Melalui berbagai perintah yang digunakan pada terminal, seperti mkdir, cd, ls, touch, cp, mv, dan rm, pengguna dapat membuat, melihat, memindahkan, menyalin, serta menghapus file dan direktori dengan mudah. Selain itu, praktikum ini juga membantu memahami bagaimana struktur direktori tersusun secara hierarki sehingga memudahkan dalam mengorganisir dan menemukan file yang dibutuhkan. Dengan memahami penggunaan perintah-perintah tersebut, pengguna dapat mengelola sistem file dengan lebih efektif dan efisien.


# LAPORAN PROYEK AKHIR <br> KOMUNIKASI DATA DAN JARINGAN KOMPUTER <br> KELOMPOK 6 P3

## Anggota Kelompok
1. G6401211082	Syifa Adawiyah				
2. G6401211098	Daffa Nofiansyah				
3. G6401211051	Muhammad Ikhlash				
4. G6401211006	Muhammad Naufal Daffa Salim

## Deskripsi Web App "Flarum"
**[Flarum](https://flarum.org/)** merupakan sebuah aplikasi berbasis web untuk membuat forum diskusi. Seperti yang terdapat pada screenshot di bawah ini yang merupakan tampilan halaman utama dari web Flarum yang diambil dari web resminya
![image](https://github.com/ssyifaad/komdat-proyek/assets/56620851/be2e8535-19d3-456c-b5f8-c8509867e6a8)

## Fitur
1. Login/signup
2. Membuat forum diskusi baru
3. Memberi komentar pada forum diskusi lain
4. Menghapus forum diskusi
5. Memiliki notifikasi untuk balasan baru pada forum diskusi
6. Mengedit nama forum, tag, isi forum, dan komentar
7. Refresh dan mark all as read

#### Dokumentasi
Halaman utama web
<img width="960" alt="image" src="https://github.com/ssyifaad/komdat-proyek/assets/56620851/38aa12e4-1f7b-48bb-aefa-ebddbbc2b832">

Login/signup
<img width="960" alt="image" src="https://github.com/ssyifaad/komdat-proyek/assets/56620851/827d6067-0e45-40fd-a9f9-b4e2dcaf7ebf">

Forum diskusi
<img width="960" alt="image" src="https://github.com/ssyifaad/komdat-proyek/assets/56620851/34daab23-9e58-4c8d-a46d-8cc55670bc52">

## Requirements
- Apache (dengan mengaktifkan mod_rewrite) atau Nginx
- PHP 7.3+ dengan extensions: curl, dom, fileinfo, gd, json, mbstring, openssl, pdo_mysql, tokenizer, zip
- MySQL 5.6+/8.0.23+ atau MariaDB 10.0.5+
- Composer
- SSH (command-line) untuk menjalankan Composer
- XAMPP 8.1.0

## Local Server
1. Ubah direktori ke tempat yang digunakan untuk menyimpan project (pada contoh digunakan folder htdocs di xampp)
    ```
    cd xampp/htdocs
    ```
2. Jalankan perintah composer untuk menginstal flarum
    ```
    composer create-project flarum/flarum
    ```
3. Buat database MySQL baru untuk project flarum
    - Pastikan Apache dan MySQL pada XAMPP Control Panel sudah diaktifkan
    - Kunjungi URL http://localhost/phpmyadmin/
    - Buat new database dan beri nama yang sesuai

4. Setup Install Flarum dengan mengunjungi URL http://localhost/flarum/public/
![Screenshot 2023-10-03 104309](https://github.com/ssyifaad/komdat-proyek/assets/20938858/c26b3721-2332-47a8-8540-346c825d502e)
![image](https://github.com/ssyifaad/komdat-proyek/assets/20938858/ba6e80cb-871a-47e6-b5c6-8c0275021f77)

5. Masuk ke menu *administration*
![Screenshot 2023-10-03 111223](https://github.com/ssyifaad/komdat-proyek/assets/20938858/ed97eca7-fd3f-4c5b-83eb-347b3c43c4e4)

6. Setup email driver menggunakan *Simple mail transfer protocol* (SMTP)
![Screenshot 2023-10-03 112107](https://github.com/ssyifaad/komdat-proyek/assets/20938858/51cebdd4-9816-4c30-b3d0-516895197971)

7. Save changes


## Hosting


## Referensi
[Official web Flarum](https://flarum.org/) <br>
[Github Flarum](https://github.com/flarum/framework) <br>
[Flarum documentations](https://docs.flarum.org/install/) <br>
[Youtube tutorial instalasi](https://www.youtube.com/watch?v=hqbG_SGo4go) 

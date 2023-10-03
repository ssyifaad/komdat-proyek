# LAPORAN PROYEK AKHIR <br> KOMUNIKASI DATA DAN JARINGAN KOMPUTER <br> KELOMPOK 6 P3

## Anggota Kelompok
1. G6401211082	Syifa Adawiyah				
2. G6401211098	Daffa Nofiansyah				
3. G6401211051	Muhammad Ikhlash				
4. G6401211006	Muhammad Naufal Daffa Salim

## Aplikasi Web "Flarum"
![image](https://github.com/ssyifaad/komdat-proyek/assets/56620851/8e0bc07e-6aef-49fd-b9d9-27f53a6c3610)<br>

<br>**[Flarum](https://flarum.org/)** merupakan sebuah aplikasi berbasis web untuk membuat forum diskusi. Seperti yang terdapat pada screenshot di bawah ini yang merupakan tampilan halaman utama dari web Flarum yang diambil dari web resminya.
<br>

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


## Virtual Private Server

1. Setup VM menggunakan layanan VPS Digital Ocean
    - Sign up/Sign in dengan akun yang sesuai
    - Buat project baru dan beri nama sesuai atau gunakan *first-project* yang sudah otomatis dibuat ketika membuat akun
    ![Screenshot 2023-10-03 113107](https://github.com/ssyifaad/komdat-proyek/assets/20938858/82a2e6b9-8d97-4fa5-bda2-5f9acb0ea604)

    - Buat droplet (VM) baru dengan spesifikasi yang diinginkan (pada contoh menggunakan Ubuntu 22.04 LTS)
    ![Screenshot 2023-10-03 113245](https://github.com/ssyifaad/komdat-proyek/assets/20938858/434e3342-e3dd-4a1c-9591-8bb732142eea)

2. Buka terminal dan connect ke VPS dengan root menggunakan ```ssh``` IP Address yang disediakan VPS dan masukan password
    ```
    $ ssh root@IPaddress
    ```

3. Tambah user baru
    ```
    $ sudo adduser [username]
    ```

4. Berikan hak administratif kepada user kemudian logout
    ```
    $ sudo usermod -aG sudo [username]
    $ logout
    ```

5. Connect ssh dengan user dan masukan password user

    ```
    $ ssh user@IPAddrress
    ```

6. Jalankan system update untuk update package list
    ```
    $ sudo apt update && sudo apt upgrade
    ```

7. Install Apache dan MariaDB menggunakan APT package manager
    ```
    $ sudo apt-get install apache2 mariadb-server mariadb-client
    ```

8. Configure MariaDB
    ```
    $ sudo mysql_secure_installation
    > Enter current password: Tekan ENTER
    > Create new password: Y
    > Jawab Y untuk seluruh pertanyaan setelahnya
    ```

9. Buat Database baru
    ```
    $ mysql -u root -p
    > create database nama_db;
    ```

10. Buat VHost baru beserta directorynya
    ```
    $ sudo mkdir -p /var/www/flarum
    $ sudo chown -R root:root /var/www/flarum
    ```

11. Buat file conf
    ```
    $ sudo nano /etc/apache2/sites-available/flarum.conf
    ```
    lalu tambahkan baris berikut:
    ```
    <VirtualHost *:80>
    ServerAdmin example@email.com
    ServerName flarum
    ServerAlias flarum
    DocumentRoot /var/www/flarum
    <Directory "/var/www/flarum">
    AllowOverride All
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    </VirtualHost>
    ```

12. Install PHP 8.1 beserta extension yang dibutuhkan
    ```
    $ sudo add-apt-repository ppa:ondrej/php

    $ sudo apt install php8.1 libapache2-mod-php8.1 php8.1-common php8.1-mbstring php8.1-curl php8.1-xmlrpc php8.1-soap php8.1-gd php8.1-xml php8.1-intl php8.1-mysql php8.1-cli php8.1-mcrypt php8.1-zip php8.1-curl php8.1-dom composer openssl
    ```

13. Install composer
    ```
    sudo apt install composer
    ```

14. CD ke directory var/www/flarum dan run composer, pastikan isi directory kosong
    ```
    $ cd /var/www/flarum

    $ composer create-project flarum/flarum . --stability=beta
    ```

15. Enable VHost dan mod_rewrite
    ```
    $ sudo a2ensite flarum
    $ sudo a2enmod rewrite
    $ sudo a2dissite 000-default.conf
    $ sudo systemctl restart apache2
    ```

16. Fix permission
    ```
    $ sudo chmod -R 777 /var/www/flarum
    ```

17. Setup Install Flarum dengan mengunjungi URL http://IPAddress_VPS/public/
![Screenshot 2023-10-03 103452](https://github.com/ssyifaad/komdat-proyek/assets/20938858/a19bf745-b383-4b4d-b345-73117219ec92)
![image](https://github.com/ssyifaad/komdat-proyek/assets/20938858/ba6e80cb-871a-47e6-b5c6-8c0275021f77)

18. Masuk ke menu *administration*
![Screenshot 2023-10-03 111223](https://github.com/ssyifaad/komdat-proyek/assets/20938858/ed97eca7-fd3f-4c5b-83eb-347b3c43c4e4)

19. Setup email driver menggunakan *Simple mail transfer protocol* (SMTP)
![Screenshot 2023-10-03 112107](https://github.com/ssyifaad/komdat-proyek/assets/20938858/51cebdd4-9816-4c30-b3d0-516895197971)

20. Save changes

## Kelebihan dan Kekurangan
### Kelebihan
**1. Antarmuka yang Modern** <br>
Flarum memiliki antarmuka pengguna yang modern, bersih, dan intuitif.<br>
**2.Ringan dan Cepat**<br>
Flarum dirancang dengan fokus pada kinerja dan kecepatan. Ini membuatnya sangat responsif dan cocok untuk penggunaan pada berbagai perangkat<br>
**3. Notifikasi dan Aktivitas Terbaru**<br>
Pengguna dapat menerima notifikasi real-time tentang tanggapan, pesan pribadi, atau aktivitas lainnya di forum, membuat pengalaman berpartisipasi lebih interaktif.<br>
**4. Fleksibel dan dapat disesuaikan**<br>
Flarum memiliki sistem ekstensi yang kuat, sehingga pengguna dapat menyesuaikan platform sesuai dengan kebutuhan mereka<br>

### Kekurangan
**1. Keterbatasan ekstensi** <br>
Jumlah ekstensi yang tersedia masih terbatas dibandingkan dengan platform diskusi lainnya <br>
**2. Fitur-fitur yang masih terbatas** <br>
Flarum masih dalam pengembangan, sehingga fitur-fitur yang tersedia masih terbatas. Namun, tim pengembang Flarum terus menambahkan fitur-fitur baru ke dalam platform ini <br>
**3. Komunitas pengguna yang masih kecil** <br>
Komunitas pengguna Flarum masih kecil dibandingkan dengan platform forum web lainnya. Hal ini dapat menyebabkan kesulitan dalam menemukan informasi atau bantuan <br>

## Kesimpulan
Flarum adalah aplikasi web forum diskusi antarmuka yang mudah digunakan. Ia memiliki fitur dasar seperti login, pembuatan forum, dan notifikasi. Flarum memiliki kelebihan berupa fleksibilitas, ringan, dan cepat, tetapi flarum masih memiliki keterbatasan fitur dan komunitas pengguna yang relatif kecil. Secara keseluruhan, Flarum adalah solusi forum diskusi yang menjanjikan, terutama bagi pengguna yang mencari platform yang ringan dan mudah digunakan.

## Referensi
[Official web Flarum](https://flarum.org/) <br>
[Github Flarum](https://github.com/flarum/framework) <br>
[Flarum documentations](https://docs.flarum.org/install/) <br>
[Youtube tutorial instalasi](https://www.youtube.com/watch?v=hqbG_SGo4go) 

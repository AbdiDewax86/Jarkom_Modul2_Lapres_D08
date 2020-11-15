# Jarkom_Modul2_Lapres_D08
## DNS
### Soal 1
Untuk membuat sebuah website, dilakukan konfigurasi berikut ke /etc/bind/named.conf.local
Karena server MALANG digunakan sebagai Master, maka prosedur ini dilakukan di server MALANG

![alt text](images/1-1.png)

Lalu dibuatkan directory shift di /etc/bind/
File /etc/bind/db.local dicopy ke /etc/bind/shift/ dan direname menjadi semerud08.pw
Lalu dilakukan konfigurasi di file /etc/bind/shift/semerud08.pw sebagai berikut:

![alt text](images/1-2.png)

Agar site dikenali oleh client, maka dilakukan konfigurasi berikut di client di /etc/resolv.conf

![alt text](images/1-3.png)
### Soal 2
Untuk konfigurasi Alias website, ditambahkan line CNAME berikut dlm /etc/bind/shift/semerud08.pw

![alt text](images/2-1.png)

![alt text](images/2-2.png)
### Soal 3
Untuk konfigurasi subdomain website, ditambahkan line A berikut dlm /etc/bind/shift/semerud08.pw
IP diganti menjadi IP PROBOLINGGO

![alt text](images/3-1.png)
![alt text](images/3-2.png)
### Soal 4
Untuk menambah reverse DNS, ditambahkan konfigurasi berikut ke /etc/bind/named.conf.local

![alt text](images/4-1.png)

File /etc/bind/db.local dicopy ke /etc/bind/shift/ dan direname menjadi 79.151.10.in-addr.arpa, dan dilakukan konfigurasi sebagai berikut:

![alt text](images/4-2.png)
![alt text](images/4-3.png)
### Soal 5
Untuk mengatur server MALANG sebagai DNS master, ditambahkan line2 berikut dlm file /etc/bind/named.conf.local

![alt text](images/5-1.png)

Buka server MOJOKERTO, dan dilakukan konfigurasi juga di /etc/bind/named.conf.local agar MOJOKERTO dapat menjadi DNS slave

![alt text](images/5-2.png)

Dlm client, ditambahkan IP MOJOKERTO dlm /etc/resolv.conf

![alt text](images/5-3.png)
![alt text](images/5-4.png)
### Soal 6 & 7
Untuk membuat mendelegasikan subdomain dengan nama alamat http://gunung.semerud08.pw pertama kita harus mengkonsfigurasi pada server Malang di file bind yang kita buat dengan membuat ns1 dan di arahkan ke server Mojokerto
![alt text](images/6%207-1.png)
Kemudian di file named.local.conf kita buat allow transfer ke Mojokerto dan restart bind9 kita
![alt text](images/6%207-2.png)
Kemudian di server Mojokerto kofigurasi pada named.local.conf alamat http://gunung.semerud08.pw 
![alt text](images/6%207-3.png)
Kemudian di file gunung.semerud08.pw pada bind9 kita buat konfigurasi ke IP Probolinggo dan juga kita membuat subdomain di ke Probolinggo dengan nama naik
![alt text](images/6%207-4.png)
Coba ping pada pada client gunung.semerud08.pw dan naik.gunung.semerud08.pw
![alt text](images/6%207-5.png)

## Web Server
### Soal 8
Untuk mengatur webserver semerud08.pw, dibuat file semerud08.pw dari file default di /etc/apache2/sites-available dengan ServerName semerud08.pw , ServerAlias www.semerud08.pw, dan DocumentRoot /var/www/semerud08.pw
Isi folder semerud08.pw didapat dari zip semeruyyy.pw.zip yang telah disediakan oleh wget 10.151.36.202/semeruyyy.pw.zip
File zip di-unzip ke directory /var/www/ dan direname sesuai nama kelompok

![alt text](images/8-1.png)
![alt text](images/8-2.png)
### Soal 9
UNtuk membuat agar urlnya menjadi http://semeruyyy.pw/home. Kita dapat membuatnya dengan metode rewrite dan kita membuka .htaccess pada folder yang sama dengan dengan file semerud08.pw berada dan mengisinya seperti di bawah ini
![alt text](images/9-1.png)
Kemudian kita harus melakukan configurasi pada file semerud08.pw pada di sites-available di apache2 agar .htaccessnya dapat berjalan.
![alt text](images/9-2.png)
Hasilnya :
![alt text](images/9-3.png)
### Soal 10
Untuk mengatur webserver penanjakan.semerud08.pw, dilakukan langkah yang sama seperti semerud08.pw di no. 8
Isi folder penanjakan.semerud08.pw didapat dari zip penanjakan.semeruyyy.pw yang telah disediakan oleh wget 10.151.36.202/penanjakan.semeruyyy.pw.zip
File zip di-unzip ke directory /var/www/ dan direname sesuai nama kelompok

![alt text](images/10-1.png)
![alt text](images/10-2.png)
### Soal 11
Untuk mengatur Indexing maka diketikkan syntax sebagai berikut:

![alt text](images/11-1.png)

Public memiliki argumen +Indexes agar dapat diakses dan directory dibawahnya menggunakan -Indexing agar menolak akses.
Directory yang memiliki arg +Indexes dapat diakses seperti biasa, sedangkan yang memiliki arg -Indexes akan menunjukkan halaman 403 Forbidden

![alt text](images/11-2.png)
![alt text](images/11-3.png)
![alt text](images/11-4.png)
![alt text](images/11-5.png)
### Soal 12
Agar semua error 404 melakukan redirect ke error/404.html, maka ditambahkan line "ErrorDocument 404 /errors/404.html"

![alt text](images/12-1.png)
### Soal 13
Agar memudahkan mengakses /public/javascripts dengan hanya mengakses penanjakan.semerud08.pw/js, maka ditambahkan alias berikut:

![alt text](images/13-1.png)

Setelah diberikan alias, directory /js akan menampilkan halaman yang sama dengan dengan directory /public/javascripts

![alt text](images/13-2.png)
![alt text](images/13-3.png)
### Soal 14
Untuk mengatur web server naik.gunung.semerud08.pw, VirtualHost diganti dari 80 menjadi 8888, dan DocumentRoot diganti menjadi /var/www/naik.gunung.semerud08.pw

![alt text](images/14-1.png)
![alt text](images/14-2.png)
### Soal 15
Untuk membuat sistem authentation pada apache  pertama kita harus memiliki sebuat ultilitas yang disebut dengan htpasswd. Jika belum memilikinya kita harus mendownloadnya dengan cara mengetikkan perintah pada uml 
```c 
apt-get install apache2 apache2-utils
```
kemudian untuk membuat sebuah user kita dapat melakukannya dengan mengetikkan pada uml perintah 
```c
htpasswd -c /etc/apache2/.htpasswd semeru
```
beberapa saat kemudian akan ad perintah untuk membuat password dan kita harus mengisinya untuk membuat password yang kita inginkan. seletah itu kita melakukan configurasi pada naik.gunung.semerud08.pw dengan menambahkan syntax berikut
```c
ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined

    <Directory "/var/www/html">
        AuthType Basic
        AuthName "Restricted Content"
        AuthUserFile /etc/apache2/.htpasswd
        Require valid-user
    </Directory>
```
jika pada file naik.gunung.semerud08.pw sudah ad syntax di atas hanay perlu menambahkan syntax yang tidak ada saja dan jangan lupa untuk merestart apache. Kemudian lakukan konfigurasi pada apache2.conf dan temukan blok <Directory> untuk direktori /var/www yang menyimpan root dokumen. Aktifkan pemrosesan .htaccess dengan mengubah perintah AllowOverride dalam blok itu dari "None" menjadi "All" seperti contoh di bawah.
    ```c
        . . .

        <Directory /var/www/>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>

        . . .
        ```
![alt text](images/15-1.png)
Hasil :
![alt text](images/15-2.png)
### Soal 16
Untuk membuat setiap melakukan pencarian pada browser dengan IP Probolinggo langsung menuju ke file semerud08.pw kita harus melakukan rewrite dengan cara membuat configurasi pada file .htaccess di folder sites-available dengan syntax seperti dibawah ini
![alt text](images/16-1.png)
Setelah itu lakukan configurasi pada file semerud08.pw dan default dengan menemukan blok <Directory> untuk direktori / var / www yang menyimpan root dokumen. Aktifkan pemrosesan .htaccess dengan mengubah perintah AllowOverride dalam blok itu dari "None" menjadi "All" seperti contoh di bawah.
    ```c
         . . .

        <Directory /var/www/>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>

        . . .
    ```
    
![alt text](images/16-2.png)
![alt text](images/16-3.png)

### Soal 17

Untuk membuat setiap request gambar dengan substring semeru akan menuju ke semeru.jpg. Kita akan melakukan proses rewrite pada penajakan.semerud08.pw dengan melakukan configurasi pada file .htaccess dengan mengetikkan syntax berikut
![alt text](images/17-1.png)
Kemudian pada file penanjakan.semerud08.pw temukan blok <Directory /> dan biasanya ini berada di atas direktori / var / www yang menyimpan root dokumen. Aktifkan pemrosesan .htaccess dengan mengubah perintah AllowOverride dalam blok itu dari "None" menjadi "All" seperti contoh di bawah
```c
        . . .

        <Directory />
            Options Indexes FollowSymLinks
            AllowOverride All
        </Directory>

        . . .
  ```
![alt text](images/17-2.png)

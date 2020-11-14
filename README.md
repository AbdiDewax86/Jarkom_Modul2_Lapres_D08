# Jarkom_Modul2_Lapres_D08
## DNS
#### 1
Untuk membuat sebuah website, dilakukan konfigurasi berikut ke /etc/bind/named.conf.local
Karena server MALANG digunakan sebagai Master, maka prosedur ini dilakukan di server MALANG

![alt text](images/1-1.png)

Lalu dibuatkan directory shift di /etc/bind/
File /etc/bind/db.local dicopy ke /etc/bind/shift/ dan direname menjadi semerud08.pw
Lalu dilakukan konfigurasi di file /etc/bind/shift/semerud08.pw sebagai berikut:

![alt text](images/1-2.png)

Agar site dikenali oleh client, maka dilakukan konfigurasi berikut di client di /etc/resolv.conf

![alt text](images/1-3.png)
#### 2
Untuk konfigurasi Alias website, ditambahkan line CNAME berikut dlm /etc/bind/shift/semerud08.pw

![alt text](images/2-1.png)

![alt text](images/2-2.png)
#### 3
Untuk konfigurasi subdomain website, ditambahkan line A berikut dlm /etc/bind/shift/semerud08.pw
IP diganti menjadi IP PROBOLINGGO

![alt text](images/3-1.png)
![alt text](images/3-2.png)
#### 4
Untuk menambah reverse DNS, ditambahkan konfigurasi berikut ke /etc/bind/named.conf.local

![alt text](images/4-1.png)

File /etc/bind/db.local dicopy ke /etc/bind/shift/ dan direname menjadi 79.151.10.in-addr.arpa, dan dilakukan konfigurasi sebagai berikut:

![alt text](images/4-2.png)
![alt text](images/4-3.png)
#### 5
Untuk mengatur server MALANG sebagai DNS master, ditambahkan line2 berikut dlm file /etc/bind/named.conf.local

![alt text](images/5-1.png)

Buka server MOJOKERTO, dan dilakukan konfigurasi juga di /etc/bind/named.conf.local agar MOJOKERTO dapat menjadi DNS slave

![alt text](images/5-2.png)

Dlm client, ditambahkan IP MOJOKERTO dlm /etc/resolv.conf

![alt text](images/5-3.png)
![alt text](images/5-4.png)
#### 6 & 7
![alt text](images/6%207-1.png)
![alt text](images/6%207-2.png)
![alt text](images/6%207-3.png)
![alt text](images/6%207-4.png)
![alt text](images/6%207-5.png)

## Web Server
#### 8
Untuk mengatur webserver semerud08.pw, dibuat file semerud08.pw dari file default di /etc/apache2/sites-available dengan ServerName semerud08.pw , ServerAlias www.semerud08.pw, dan DocumentRoot /var/www/semerud08.pw
Isi folder semerud08.pw didapat dari zip semeruyyy.pw.zip yang telah disediakan oleh wget 10.151.36.202/semeruyyy.pw.zip
File zip di-unzip ke directory /var/www/ dan direname sesuai nama kelompok

![alt text](images/8-1.png)
![alt text](images/8-2.png)
#### 9
![alt text](images/9-1.png)
![alt text](images/9-2.png)
![alt text](images/9-3.png)
#### 10
Untuk mengatur webserver penanjakan.semerud08.pw, dilakukan langkah yang sama seperti semerud08.pw di no. 8
Isi folder penanjakan.semerud08.pw didapat dari zip penanjakan.semeruyyy.pw yang telah disediakan oleh wget 10.151.36.202/penanjakan.semeruyyy.pw.zip
File zip di-unzip ke directory /var/www/ dan direname sesuai nama kelompok

![alt text](images/10-1.png)
![alt text](images/10-2.png)
#### 11
Untuk mengatur Indexing maka diketikkan syntax sebagai berikut:

![alt text](images/11-1.png)

Public memiliki argumen +Indexes agar dapat diakses dan directory dibawahnya menggunakan -Indexing agar menolak akses.
Directory yang memiliki arg +Indexes dapat diakses seperti biasa, sedangkan yang memiliki arg -Indexes akan menunjukkan halaman 403 Forbidden

![alt text](images/11-2.png)
![alt text](images/11-3.png)
![alt text](images/11-4.png)
![alt text](images/11-5.png)
#### 12
Agar semua error 404 melakukan redirect ke error/404.html, maka ditambahkan line "ErrorDocument 404 /errors/404.html"

![alt text](images/12-1.png)
#### 13
Agar memudahkan mengakses /public/javascripts dengan hanya mengakses penanjakan.semerud08.pw/js, maka ditambahkan alias berikut:

![alt text](images/13-1.png)

Setelah diberikan alias, directory /js akan menampilkan halaman yang sama dengan dengan directory /public/javascripts

![alt text](images/13-2.png)
![alt text](images/13-3.png)
#### 14
Untuk mengatur web server naik.gunung.semerud08.pw, VirtualHost diganti dari 80 menjadi 8888, dan DocumentRoot diganti menjadi /var/www/naik.gunung.semerud08.pw

![alt text](images/14-1.png)
![alt text](images/14-2.png)
#### 15
Untuk menambahkan
![alt text](images/15-1.png)
![alt text](images/15-2.png)
#### 16
![alt text](images/16-1.png)
![alt text](images/16-2.png)
![alt text](images/16-3.png)
#### 17
![alt text](images/17-1.png)
![alt text](images/17-2.png)

 ![image](https://user-images.githubusercontent.com/13843450/32212055-cf3fbe52-be47-11e7-95a7-2ef08d213148.png)

# Sekilas Tentang
Searx merupakan salah satu metasearch engine internet gratis dan Open Source yang mengumpulkan hasil lebih dari 70 layanan pencarian. Pengguna tidak dilacak dan diprofilkan. Selain itu, searX dapat digunakan dengan Tor untuk online secara anonim.

# Instalasi
## Kebutuhan Sistem
•	Sistem operasi Linux, Ubuntu Server

• Apache web server

• Python

## Proses Instalasi
Sebelum melakukan instalasi pastikan kita mempunyai akses terhadap repository paket-paket yang kita butuhkan:
1.	Install paket-paket yang dibutuhkan oleh Searx dan pastikan paket tersebut up-to-date

`$ sudo apt-get install git build-essential libxslt-dev python-dev python-virtualenv python-pybabel zlib1g-dev libffi-dev libssl-dev`

2.	Install Searx search engine dengan kode di bawah ini
```
$ sudo git clone https://github.com/asciimoo/searx.git 
$ sudo useradd searx -d /usr/local/searx 
$ sudo chown searx:searx -R /usr/local/searx cd /usr/local
```
3.	Install kebutuhan search engine yang berupa python framework virtual env
```
$ sudo -u searx -i 
$ cd /usr/local/searx 
$ virtualenv searx-ve 
$ . ./searx-ve/bin/activate 
$ ./manage.sh update_packages
```
#Konfigurasi

`$ sed -i -e "s/ultrasecretkey/'openssl rand -hex 16'/g" searx/settings.yml`

note: Gunakan tanda kutip disebelah kiri angka 1 sebelum dan sesudah * *openssl rand -hex 16* *

# Web Server
Install Apache sebagai Web Server untuk searX yang akan digunakan nanti. Disini kami menginstall Apache sebagai web server di virtual box dengan sistem operasi linux agar searX juga bisa kami gunakan pada client di Notebook kami yang menggunakan sistem operasi Windows dengan menentukan location Web Server Apache pada konfigurasinya nanti.
1.	Tambahkan modul wsgi. Wsgi adalah salah satu modul milik Apache

``
sudo apt-get install libapache2-mod-uwsgi
sudo a2enmod uwsgi
``

2.	Tambahkan konfigurasi ini pada file /etc/apache2/apache2.conf:

```
<Location />
    Options FollowSymLinks Indexes
    SetHandler uwsgi-handler
    uWSGISocket /run/uwsgi/app/searx/socket
`</Location>`
```

Pada bagian `<Location />` kita harus memberikan alamat root yang akan kita gunakan saat ingin membukanya di client. Contohnya <Location /searx> atau juga bisa diisi dengan kata-kata lain <Location /student> 

3.	Restart Apache

`sudo /etc/init.d/apache2 restart`

# Perbandingan Fitur-fitur searX vs Google
1.	Tab Menu

![image](https://user-images.githubusercontent.com/13843450/32212289-d15502b4-be48-11e7-93e2-750335086c46.png)

Gambar. Tab menu searX

![image](https://user-images.githubusercontent.com/13843450/32212323-f07d2388-be48-11e7-9fcb-b4b4b9ca54bb.png) 

Gambar. Tab menu Google

Seperti yang terlihat pada gambar, searX dan Google mempunyai beberapa tab menu yang berbeda, pada searX terdapat tab menu music sedangkan Google tidak.

2.	Waktu dan Bahasa

![image](https://user-images.githubusercontent.com/13843450/32212341-fe84884a-be48-11e7-9f88-9b9a834c5d7c.png) 

Gambar. Waktu dan bahasa searX

![image](https://user-images.githubusercontent.com/13843450/32212354-093ac6dc-be49-11e7-8417-b653aaedeb91.png) 

Gambar. Waktu dan bahasa Google

Untuk pengaturan waktu dan bahasa pada searX berupa dropdown yang disediakan langsung pada antarmukanya. Sedangkan pada Google kita harus memilih menu setelan agar bahasa yang ingin kita pilih keluar dan menu alat agar pengaturan waktu keluar.

3.	Biografi

![image](https://user-images.githubusercontent.com/13843450/32212375-1546e30c-be49-11e7-9833-cb0ab4758ad6.png) 

Gambar. Biografi searX

![image](https://user-images.githubusercontent.com/13843450/32212386-200e8eb6-be49-11e7-9210-57cb539c32d5.png) 

Gambar. Biografi Google

Sama seperti Google, jika kata kunci yang kita masuk berupa entitas/objek maka searX juga akan menampilkan kolom biografi dari objek tersebut.

4.	Paging

![image](https://user-images.githubusercontent.com/13843450/32212395-2bded714-be49-11e7-876c-3ea90b0b7ecc.png) 

Gambar. Paging searX

![image](https://user-images.githubusercontent.com/13843450/32212413-36db3e46-be49-11e7-8e20-4162fe646b22.png) 

Gambar. Paging Google

Paging pada Google lebih lengkap dan mudah disbanding searX karena menyediakan nomer halamannya langsung yang ingin kita tuju. Sedangkan searX hanya berupa previos page dan next page yang berarti kita hanya bisa mengunjungi halamannya satu per satu.

5.	Sugestion dan beberapa tambahan

![image](https://user-images.githubusercontent.com/13843450/32212424-419cf22a-be49-11e7-9575-776f3cada41f.png) 

Gambar. Sugestion dan beberapa tambahan searX

![image](https://user-images.githubusercontent.com/13843450/32212438-4a93aac2-be49-11e7-96be-e5ca2c53ce34.png)

Gambar. Sugestion Google

Pada searX juga terdapat menu suggestion sama seperti Google. Namun bedanya searX menyediakan beberapa menu tambahan seperti donate. Donate berisi permintaan dari pihak searX kepada user bagi yang ingin mendukung searX dalam pengembangannya dan melakukan donasi berupa uang. SearX juga menyediakan fitur Search URL karena pada searX ketika memasukkan kata kunci, URL tersebut tidak berada pada bagian atas browser seperti biasanya namun berada di bagian fitur search URL. SearX juga menyediakan menu download result yang berupa csv, json, dan rss. Hasil download berupa kode program dengan format tersebut dari antarmuka yang tersedia.

# Cara Pemakaian

![image](https://user-images.githubusercontent.com/13843450/32212450-56444a02-be49-11e7-82c8-16dd489b1f94.png) 

1.	Cara memakai searX hampir sama seperti search engine yang lain, langkah pertama yaitu kita cukup memasukan kata kunci yang ingin kita cari di internet pada kolom search.

![image](https://user-images.githubusercontent.com/13843450/32212461-65dc0e3c-be49-11e7-8818-a36a3e0ad7a0.png) 

2.	Selanjutnya, searX akan menampilkan hasil pencarian yang berhubungan dengan kata kunci yang kita masukkan. Bedanya searX menampilkan beberapa pilihan menu yang berbeda dengan beberapa search engine yang lain.

![image](https://user-images.githubusercontent.com/13843450/32212477-721efa42-be49-11e7-94b5-1c4fefec69d1.png)

3.	Selanjutnya kita bisa menggunakan searX sesuai keinginan kita berdasarkan fitur-fitur dan filter-filter yang telah disediakan oleh searX.

# Pembahasan
**SearX** merupakan metasearch engine yang dibuat menggunakan  bahasa pemrograman Phyton, aplikasi search engine ini memiliki kelebihan, diantaranya:

o	Host sendiri

o	Tidak ada pelacakan pengguna

o	Tidak ada profil pengguna

o	Didukung 70 search engine

o	Mudah diintegrasi dengan mesin pencari

o	Cookie tidak digunakan secara default

o	Sambungan yang aman dan terenkripsi (HTTPS/SSL)

o	Host oleh organisasi seperti La Quadrature du Net yang mempromosikan hak digital.

**SearX** memiliki kelemahan antara lain:

o	Tidak dapat melakukan penelusuran secara mendetail

o	Relatif lebih lama dibandingkan menggunakan Search Engine biasa.

o	Tidak memiliki database sehingga informasi yang dihasilkan relatif terbatas

# Referensi

1.	About SearX (https://asciimoo.github.io/searx/) – SearX

2.	searX installation (https://asciimoo.github.io/searx/dev/install/installation.html)

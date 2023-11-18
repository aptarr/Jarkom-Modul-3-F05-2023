# Jarkom-Modul-3-F05-2023
Pratikum Jaringan Komputer 2023 Modul 3
# Kelompok  
Apta Rasendriya Wijaya - 5025211139  
Made Nanda Wija Vahindra - 5025211160  

## Topologi
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/aec6280c-d9eb-4c96-bdae-71a64eb891b2)
## Konfigurasi  
Aura:
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 10.54.1.5
    netmask 255.255.255.0

auto eth2
iface eth2 inet static
    address 10.54.2.5
    netmask 255.255.255.0

auto eth3
iface eth3 inet static
    address 10.54.3.5
    netmask 255.255.255.0

auto eth4
iface eth4 inet static
    address 10.54.4.5
    netmask 255.255.255.0
```
ETH1  
Himmel:
```
auto eth0
iface eth0 inet static
    address 10.54.1.1
    netmask 255.255.255.0
    gateway 10.54.1.5
```
Heiter:
```
auto eth0
iface eth0 inet static
    address 10.54.1.2
    netmask 255.255.255.0
    gateway 10.54.1.5
```
ETH2  
Denken:
```
auto eth0
iface eth0 inet static
    address 10.54.2.1
    netmask 255.255.255.0
    gateway 10.54.2.5
```
Eisen:
```
auto eth0
iface eth0 inet static
    address 10.54.2.2
    netmask 255.255.255.0
    gateway 10.54.2.5
```
ETH3  
Lugner:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether 96:f3:76:73:91:ff
```
Linie:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether 9a:99:2d:c8:99:f0
```
Lawine:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether a2:b2:4a:77:81:d9
```
Richter:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether 0a:fc:0a:da:bd:92
```
Revolte:
```
auto eth0
iface eth0 inet dhcp
```
ETH4  
Frieren:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether da:2a:01:b6:fd:6d
```
Flamme:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether 86:4b:9f:5c:22:63
```
Fern:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether 8a:24:71:1a:a5:5a
```
Stark:
```
auto eth0
iface eth0 inet dhcp
    hwaddress ether e6:35:e4:b4:21:f1
```
Sein:
```
auto eth0
iface eth0 inet dhcp
```

## Soal 1
Konfigurasi sesuai topologi kemudian register domain berupa riegel.canyon.yyy.com untuk worker Laravel dan granz.channel.yyy.com untuk worker PHP (0) mengarah pada worker yang memiliki IP [prefix IP].x.1.
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/5fe138b1-a0f6-40b7-a4b0-93575fda028f)  
Untuk php worker  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/bf540fae-d91b-43d5-a181-1dbe1f6bc675)  
Untuk Laravel Worker  
## Soal 2
Client yang melalui switch 3 mendapatkan range IP dari 10.54.3.16 - 10.54.3.32 dan 10.54.3.64 - 10.54.3.80, dikonfigurasi pada dhcp server  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/495c2a01-d9e9-47f3-9af5-8ac0855a3e81)  
## Soal 3  
Client yang melalui Switch4 mendapatkan range IP dari 10.54.4.12 - 10.54.4.20 dan 10.54.4.160 - 10.54.4.168
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/a891111a-2967-4a91-9c4b-331ee0108891)  
## Soal 4
Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut. Untuk dapat terhubung
ke internet, digunakan dns forwarder pada dns server ke ip nameserver dari router.
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/faf97c87-daf9-4658-a1a3-2eb6a4d7d533)  
## Soal 5
Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit di konfigurasi pada  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/7d5cad6b-f4ce-48ea-9e70-29ebf77b4c0e)  
lease time dan max lease time pada dhcp server menuju masing masing switch.  
## Soal 6
Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website berikut dengan menggunakan php 7.3.  
Untuk melakukan konfigurasi dilakukan installasi nginx, php, dan php-fpm. Juga dilakukan instalasi wget dan zip untuk mengunduh dan melakukan unzip dari file yang sudah disediakan. File yang ada di dalam zip dipindahkan ke direktori ```/var/www/jarkom/```. Untuk konfigurasi nginx pada file ```/etc/nginx/sites-available/jarkom``` seperti dibawah ini
```
server {

listen 80;

root /var/www/jarkom;

index index.php index.html index.htm;
server_name _;

location / {
        try_files \$uri \$uri/ /index.php?\$query_string;
}

# pass PHP scripts to FastCGI server
location ~ \.php\$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
}

location ~ /\.ht {
        deny all;
}

error_log /var/log/nginx/jarkom_error.log;
access_log /var/log/nginx/jarkom_access.log;
}
```
Jalankan perintah 
```
ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
service php7.3-fpm start
service php7.3-fpm restart
rm -rf /etc/nginx/sites-enabled/default
service nginx restart
```
untuk menlakukan symbolic link dan menjalankan service php-fpm serta menghapus site default dari nginx kemudian merestart service nginx untuk memuat konfigurasi.
## Soal 7
Kepala suku dari Bredt Region memberikan resource server sebagai berikut:  
    Lawine, 4GB, 2vCPU, dan 80 GB SSD.  
    Linie, 2GB, 2vCPU, dan 50 GB SSD.  
    Lugner 1GB, 1vCPU, dan 25 GB SSD.  
aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second.  
Untuk itu kita perlu melakukan konfigurasi pada eisen sebagai load balancer dan menambahkan  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/748de9f5-d3a2-49b4-9744-9b52db5372ec)  
kemudian untuk melakukan testing kita menggunakan perintah
```ab -n 1000 -c 100 -g out.data http://10.54.2.2/```  
## Soal 8
Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer.  
Disini digunakan 4 algoritma yang berbeda yaitu
- Round Robin
- Least Connection
- IP Hash
- Generic Hash
Berikut adalah grafik dari hasil request per second dari setiap algoritma yang digunakan  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/9723a9b1-5838-45d8-8113-11290cb44a31)
dari yang terlihat pada grafik, request per second dari algoritma IP Hash adalah yang paling tinggi namun juga memiliki kelemahan dimana jika tidak semua worker memiliki spesifikasi yang memadai mungkin akan terjadi penurunan peforma.
## Soal 9  
Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second.  
Kita set load balancer menggunakan Algoritma Round Robin kemudian melakukan test sesuai skenario pada soal. 
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/6f8124ee-4b98-4a0d-84da-2e2758d6b396)  
Grafik diatas merupakan hasil dari test tersebut, terlihat bahwa hasil test yang dilakukan tidak terdapat perubahan yang signifikan.  
## Soal 10
Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/
Konfigurasi dilakukan pada nginx load balancer ```/etc/nginx/sites-available/lb-jarkom``` dengan menambahkan authentikasi
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/1c817c1d-fb73-4856-a43b-cf129563d780)  
kemudian set username dan passwordnya dengan perintah
```
htpasswd -cb /etc/nginx/rahasisakita/.htpasswd netics ajkf05
```
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/facbe324-1c11-4226-929d-ab26aa2c8c59)  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/0659d9e7-0d97-4f1c-8019-05f7cdbb0c58)  
## Soal 11
Buat untuk setiap request yang mengandung /its akan di proxy passing menuju halaman https://www.its.ac.id.  
Untuk konfigurasinya kita menambahkan proxy_pass pada konfigurasi nginx di load balancer  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/2940795c-1535-40f3-8023-e9acf700ec21)   
untuk test saat melakukan ```lynx 10.54.2.2/its``` maka akan di passing menuju halaman https://www.its.ac.id.   
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/3e8836c7-a139-42c0-941b-f20b0f3ba8e1)  

## Soal 12
LB ini hanya boleh diakses oleh client dengan IP 10.54.3.69, 10.54.3.70, 10.54.4.167, dan 10.54.4.168.  
Untuk konfigurasinya bisa menambahkan allow untuk IP tersebut kemudian deny untuk yang lainnya  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/d9546327-501c-49a8-a5d8-c720438b45f9)  
Maka pada saat IP selain IP yang ditentukan mengakses web akan memunculkan 403 Forbidden.  
![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/114988957/cf961019-a019-445e-a81e-c75cb9eb54b4)  


 


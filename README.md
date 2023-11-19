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

## Soal 13
pada soal diminta agar semua data yang diperlukan, diatur pada Denken dan harus dapat diakses oleh Frieren, Flamme, dan Fern. maka pada database server kita perlu menambahkan user berdasarkan IP seprti berikut
```
    CREATE USER 'kelompokf05'@'10.54.2.1' IDENTIFIED BY 'passwordf05';
    CREATE USER 'kelompokf05'@'10.54.4.1' IDENTIFIED BY 'passwordf05';
    CREATE USER 'kelompokf05'@'10.54.4.2' IDENTIFIED BY 'passwordf05';
    CREATE USER 'kelompokf05'@'10.54.4.3' IDENTIFIED BY 'passwordf05';
    CREATE DATABASE dbkelompokf05;
    GRANT ALL PRIVILEGES ON *.* TO 'kelompokf05'@'10.54.2.1';
    GRANT ALL PRIVILEGES ON *.* TO 'kelompokf05'@'10.54.4.1';
    GRANT ALL PRIVILEGES ON *.* TO 'kelompokf05'@'10.54.4.2';
    GRANT ALL PRIVILEGES ON *.* TO 'kelompokf05'@'10.54.4.3';
    CREATE USER 'kelompokf05'@'localhost' IDENTIFIED BY 'passwordf05';
    GRANT ALL PRIVILEGES ON *.* TO 'kelompokf05'@'localhost';
    FLUSH PRIVILEGES;
```
jangan lupa menambahkan ini pada file ```/etc/mysql/my.cnf ``` pada database server agar dapat diakses oleh node client
```
[mysqld]
skip-networking=0
skip-bind-address
```
dan lakukan ```service mysql restart```. untuk mengecek apakah berhasil tercapai permintaan nomor 13 run command berikut ```mariadb --host=10.54.2.1 --port=3306 --user=kelompokf05 --password``` dan coba show database sehingga hasil seperti berikut

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/a1750d5f-3db3-4608-a33c-349ac08ed1ea)

## Soal 14
pada soal diminta untuk melakukan instalasi laravel sesuai dengan github maka hanya perlu menjalankan script berikut
```
apt-get update
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2

curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'

apt-get update
apt-get install php8.0-mbstring php8.0-xml php8.0-cli php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y

wget https://getcomposer.org/download/2.0.13/composer.phar
chmod +x composer.phar
mv composer.phar /usr/bin/composer

apt-get install git -y

cd /var/www/
git clone https://github.com/martuafernando/laravel-praktikum-jarkom.git
cd laravel-praktikum-jarkom
composer update

echo "APP_NAME=Laravel
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=10.54.2.1
DB_PORT=3306
DB_DATABASE=dbkelompokf05
DB_USERNAME=kelompokf05
DB_PASSWORD=passwordf05

BROADCAST_DRIVER=log
CACHE_DRIVER=file
FILESYSTEM_DISK=local
QUEUE_CONNECTION=sync
SESSION_DRIVER=file
SESSION_LIFETIME=120

MEMCACHED_HOST=127.0.0.1

REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS=\"hello@example.com\"
MAIL_FROM_NAME=\"\${APP_NAME}\"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=false

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_HOST=
PUSHER_PORT=443
PUSHER_SCHEME=https
PUSHER_APP_CLUSTER=mt1

VITE_PUSHER_APP_KEY=\"\${PUSHER_APP_KEY}\"
VITE_PUSHER_HOST=\"\${PUSHER_HOST}\"
VITE_PUSHER_PORT=\"\${PUSHER_PORT}\"
VITE_PUSHER_SCHEME=\"\${PUSHER_SCHEME}\"
VITE_PUSHER_APP_CLUSTER=\"\${PUSHER_APP_CLUSTER}\"
" > .env

php artisan migrate:fresh
php artisan db:seed --class=AiringsTableSeeder
php artisan key:generate
php artisan jwt:secret

echo "
server {

    listen 80;

    root /var/www/laravel-praktikum-jarkom/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files \$uri \$uri/ /index.php?\$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php\$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php8.0-fpm.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
}" > /etc/nginx/sites-available/implementasi

ln -s /etc/nginx/sites-available/implementasi /etc/nginx/sites-enabled/
rm -rf /etc/nginx/sites-enabled/default
chown -R www-data.www-data /var/www/laravel-praktikum-jarkom/storage
service php8.0-fpm start
service nginx restart
```

pada script tersebut sebelum melakukan instalasi git script tersebut melakukan instalasi PHP 8.0 kemudian dilanjutkan melakukan konfigurasi dengan file laravel, dimana untuk melakukan pengetesan hanya perlu jalankan command berikut ```lynx http://10.54.4.1``` tergantung worker mana yang diping atau ```lynx http://riegel.canyon.f05.com``` dimana karena worker ini sudah diset pada load balancer dengan nama DNS yang sudah ditentukan. berikut hasil jika berhasil melakukan konfigurasi laravel:

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/f83e3321-8e5a-4393-b38d-2846a750f02d)

hasil respon saat melakukan curl:

http://10.54.4.1/api/auth/register

command:
```curl -s -X POST -H "Content-Type: application/json" -d '{"username": "Camille", "password": "c4aa45b6-4327-43dd-aed9-301f396267b1"}' http://10.54.4.2/auth/register```

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/d6788786-3ff5-449d-b280-5b7a0b6ac80c)

http://10.54.4.1/api/auth/login 

command:
```curl -s -X POST -H "Content-Type: application/json" -d '{"username": "Camille", "password": "c4aa45b6-4327-43dd-aed9-301f396267b1"}' http://10.54.4.2/auth/login```

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/e1325910-95cc-40dc-842d-4a6014270d7e)

http://10.54.4.1/api/me

command:
```curl -X GET -H "Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJodHRwOi8vMTAuNTQuNC4yL2FwaS9hdXRoL2xvZ2luIiwiaWF0IjoxNzAwMzM3MTAxLCJleHAiOjE3MDAzNDA3MDEsIm5iZiI6MTcwMDMzNzEwMSwianRpIjoiTzI0TDhqSkpONWF1dEFXYyIsInN1YiI6IjEiLCJwcnYiOiIyM2JkNWM4OTQ5ZjYwMGFkYjM5ZTcwMWM0MDA4NzJkYjdhNTk3NmY3In0.8j5i00O7spfAwBB8EgejQkb0L_d0TaYdoUS_NL5KK7c" -H "Content-Type: application/json" http://10.54.4.2/api/me```

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/664269f6-c288-4007-854b-8dd66b38b55a)

## Soal 15
pada soal diminta untuk melakukan bench marck dimana hanya perlu menajalankan command ini (untuk file register_data.json sudah saya lampirkan diatas):

POST /auth/register

```
ab -n 100 -c 10 -p register_data.json -T "application/json" http://riegel.canyon.f05.com/auth/register
```

hasil:

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/9225cd3b-5a56-4430-b8d7-e91cafeda7d2)

## Soal 16
pada soal diminta untuk melakukan bench marck dimana hanya perlu menajalankan command ini:

POST /auth/login 

```
ab -n 100 -c 10 -p register_data.json -T "application/json" http://riegel.canyon.f05.com/auth/login
```

hasil:

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/7a9ee673-d1ad-4274-8437-26578bf148ad)

## Soal 17
pada soal diminta untuk melakukan bench marck dimana hanya perlu menajalankan command ini:

GET /me 

```
ab -n 100 -c 10 -p output_login.json -T "application/json" http://riegel.canyon.f05.com/api/me
```

untuk mendapatkan ```output_login.json``` kita perlu menjalankan script berikut, dimana untuk mengambil semua token user dan dimasukkan kedalam file

Pertama kita melakukan pendaftaran terlebih dauhulu dengan script berikut
```
#!/bin/bash
apt install jq -y

# Check if the file exists
file_path="register_data.json"

if [ ! -f "$file_path" ]; then
    echo "File not found: $file_path"
    exit 1
fi

# Read data from the file
json_data=$(cat "$file_path")

# Extract username and password values
usernames=($(echo "$json_data" | jq -r '.[].username'))
passwords=($(echo "$json_data" | jq -r '.[].password'))

# Declare an array to store the tokens
tokens_array=()

# Iterate through the arrays and print username and password
for ((i=0; i<${#usernames[@]}; i++)); do
    echo "Username: ${usernames[i]}"
    echo "Password: ${passwords[i]}"

    # Make curl request and save output to a variable
    curl_output=$(curl -X POST -H "Content-Type: application/json" -d "{\"username\": \"${usernames[i]}\", \"password\": \"${passwords[i]}\"}" http://riegel.canyon.f05.com/api/auth/register)

    # Check for curl errors
    if [ $? -ne 0 ]; then
        echo "Curl request failed for ${usernames[i]}"
        continue
    fi

    # Debug: Print curl output
    echo "Curl Output: $curl_output"

    # Extract the token from curl output and add it to the tokens array
    token=$(echo "$curl_output" | jq -r '.token')
    tokens_array+=("{\"token\":\"$token\"}")

done

# Convert the tokens array to a JSON array and save it to a file
echo "[" > output_register.json
for ((i=0; i<${#tokens_array[@]}; i++)); do
    if [ $i -eq $((${#tokens_array[@]}-1)) ]; then
        # If it's the last element, don't append a comma
        echo "${tokens_array[i]}" >> output_register.json
    else
        # For other elements, append a comma and newline
        echo "${tokens_array[i]}," >> output_register.json
    fi
done
echo "]" >> output_register.json
```

kemdian jalankan script berikut agar mendapatkan ```output_login.json``` 

```
#!/bin/bash
apt install jq -y

# Check if the file exists
file_path="register_data.json"

if [ ! -f "$file_path" ]; then
    echo "File not found: $file_path"
    exit 1
fi

# Read data from the file
json_data=$(cat "$file_path")

# Extract username and password values
usernames=($(echo "$json_data" | jq -r '.[].username'))
passwords=($(echo "$json_data" | jq -r '.[].password'))

# Declare an array to store the tokens
tokens_array=()

# Iterate through the arrays and print username and password
for ((i=0; i<${#usernames[@]}; i++)); do
    echo "Username: ${usernames[i]}"
    echo "Password: ${passwords[i]}"

    # Make curl request and save output to a variable
    curl_output=$(curl -X POST -H "Content-Type: application/json" -d "{\"username\": \"${usernames[i]}\", \"password\": \"${passwords[i]}\"}" http://riegel.canyon.f05.com/api/auth/login)

    # Check for curl errors
    if [ $? -ne 0 ]; then
        echo "Curl request failed for ${usernames[i]}"
        continue
    fi

    # Debug: Print curl output
    echo "Curl Output: $curl_output"

    # Extract the token from curl output and add it to the tokens array
    token=$(echo "$curl_output" | jq -r '.token')
    tokens_array+=("{\"token\":\"$token\"}")

done

# Convert the tokens array to a JSON array and save it to a file
echo "[" > output_login.json
for ((i=0; i<${#tokens_array[@]}; i++)); do
    if [ $i -eq $((${#tokens_array[@]}-1)) ]; then
        # If it's the last element, don't append a comma
        echo "${tokens_array[i]}" >> output_login.json
    else
        # For other elements, append a comma and newline
        echo "${tokens_array[i]}," >> output_login.json
    fi
done
echo "]" >> output_login.json
```

hasil:

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/8932b5bf-d788-4e1b-958e-aa0c378b667e)

## Soal 18
pada soal diminta untuk memastikan ketiganya bekerja sama secara adil untuk mengatur Riegel Channel maka implementasikan Proxy Bind pada Eisen untuk mengaitkan IP dari Frieren, Flamme, dan Fern sehingga hanya perlu menambahkan line berikut pada ```/etc/nginx/sites-available/lb-jarkom```

```
    location /frieren/ {
        # Proxy Bind configuration for frieren
        proxy_bind 10.54.2.2; # IP frieren
        proxy_pass http://10.54.4.1/index.php;
    }

    location /fiamme/ {
        # Proxy Bind configuration for Fiamme
        proxy_bind 10.54.2.2; # IP Fiamme
        proxy_pass http://10.54.4.2/index.php;
    }

    location /fern/ {
        # Proxy Bind configuration for Fern
        proxy_bind 10.54.2.2; # IP Fern
        proxy_pass http://10.54.4.3/index.php;
    }
```

hasil kurang lebih seperti berikut setelah menjalankan ```lynx http://riegel.canyon.f05.com/fiamme```:

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/0ef9c591-00c8-428c-8f31-2787e9a1e740)

## Soal 19
pada soal diminta untuk melakukan bench marck dimana hanya perlu menajalankan command ini sebanyak 3 kali:

```
    ab -n 100 -c 10 http://riegel.canyon.f05.com/
```

tetapi sebelum melakukan hal terserbut kita perlu set pada setiap worker dengan menjalankan script berikut:

freieren

```
echo '[www]
user = eisen_user
group = eisen_user
listen = /run/php/php8.0-fpm-einen.sock
listen.owner = www-data
listen.group = www-data
php_admin_value[disable_functions] = exec,passthru,shell_exec,system
php_admin_flag[allow_url_fopen] = off

; Choose how the process manager will control the number of child processes.

pm = dynamic
pm.max_children = 25
pm.start_servers = 5
pm.min_spare_servers = 10
pm.max_spare_servers = 10' > /etc/php/8.0/fpm/pool.d/eisen.conf

groupadd eisen_user
useradd -g eisen_user eisen_user

service php8.0-fpm restart

echo "
server {

    listen 80;

    root /var/www/laravel-praktikum-jarkom/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files \$uri \$uri/ /index.php?\$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php\$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php8.0-fpm-einen.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
}" > /etc/nginx/sites-available/implementasi

service nginx restart
```

flamme

```
echo '[www]
user = eisen_user
group = eisen_user
listen = /run/php/php8.0-fpm-einen.sock
listen.owner = www-data
listen.group = www-data
php_admin_value[disable_functions] = exec,passthru,shell_exec,system
php_admin_flag[allow_url_fopen] = off

; Choose how the process manager will control the number of child processes.

pm = dynamic
pm.max_children = 90
pm.start_servers = 5
pm.min_spare_servers = 10
pm.max_spare_servers = 20' > /etc/php/8.0/fpm/pool.d/eisen.conf

groupadd eisen_user
useradd -g eisen_user eisen_user

service php8.0-fpm restart

echo "
server {

    listen 80;

    root /var/www/laravel-praktikum-jarkom/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files \$uri \$uri/ /index.php?\$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php\$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/run/php/php8.0-fpm-einen.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
}" > /etc/nginx/sites-available/implementasi

service nginx restart
```

freieren

```
echo '[www]
user = eisen_user
group = eisen_user
listen = /run/php/php8.0-fpm-einen.sock
listen.owner = www-data
listen.group = www-data
php_admin_value[disable_functions] = exec,passthru,shell_exec,system
php_admin_flag[allow_url_fopen] = off

; Choose how the process manager will control the number of child processes.

pm = dynamic
pm.max_children = 10
pm.start_servers = 5
pm.min_spare_servers = 5
pm.max_spare_servers = 10' > /etc/php/8.0/fpm/pool.d/eisen.conf

groupadd eisen_user
useradd -g eisen_user eisen_user

service php8.0-fpm restart

echo "
server {

    listen 80;

    root /var/www/laravel-praktikum-jarkom/public;

    index index.php index.html index.htm;
    server_name _;

    location / {
            try_files \$uri \$uri/ /index.php?\$query_string;
    }

    # pass PHP scripts to FastCGI server
    location ~ \.php\$ {
    include snippets/fastcgi-php.conf;
    fastcgi_pass unix:/var/run/php/php8.0-fpm-einen.sock;
    }

location ~ /\.ht {
            deny all;
    }

    error_log /var/log/nginx/implementasi_error.log;
    access_log /var/log/nginx/implementasi_access.log;
}" > /etc/nginx/sites-available/implementasi

service nginx restart
```

HASIL:

Percobaan 1

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/894aca65-baae-4ed0-954d-c7b14bd51ba0)

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/c79d35b7-c3b2-46c0-9466-1ad8e037e70f)

Percobaan 2

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/cdef0099-cd6b-4769-8f6f-ce63e84e1b10)

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/81b7bcf0-ac6b-445d-afe9-2291f19470dc)

Percobaan 3

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/cddf67a3-c545-4c29-bc84-3b30b6f031f5)

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/0fa466a4-0ae0-4325-b778-0009a2743d5b)

## Soal 20
pada soal diminta untuk melakukan bench marck dimana hanya perlu menajalankan command ini:
```
ab -n 100 -c 10 http://riegel.canyon.f05.com/
```
tetapi sebelum melakukan hal terserbut kita perlu menambahkan line berikut pada file ```/etc/nginx/sites-available/lb-jarkom```:

```
upstream laravel_backend  {
    least_conn;
    server 10.54.4.1; #IP Frieren
    server 10.54.4.2; #IP Fiamme
    server 10.54.4.3; #IP Fern
}
```

HASIL:

![image](https://github.com/aptarr/Jarkom-Modul-3-F05-2023/assets/116022017/1a19ca39-e39b-420f-b60d-48b7b1e742a7)
 


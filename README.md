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




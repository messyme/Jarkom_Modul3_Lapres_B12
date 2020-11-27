# Jarkom_Modul3_Lapres_B12

1. 05111840000057 - Maisie Chiara Salsabila
2. 05111840000062 - Geizka Wahyu Fahriza


## Daftar Isi
### Dynamic Host Configuration Protocol (DHCP)
  1. [Nomor 1](#1)
  2. [Nomor 2](#2)
  3. [Nomor 3](#3)
  4. [Nomor 4](#4)
  5. [Nomor 5](#5)
  6. [Nomor 6](#6)

### Proxy
  7. [Nomor 7](#7)
  8. [Nomor 8](#8)
  9. [Nomor 9](#9)
  10. [Nomor 10](#10)
  11. [Nomor 11](#11)
  12. [Nomor 12](#12)
  </br></br></br>
  
<a name="1"></a>
## SOAL NO 1
### membuat topologi jaringan demi kelancaran TA-nya dengan kriteria sebagai berikut:
![testestes](/Screenshot/soal1.jpg)

- Buat topologi.sh yang berisi seperti gambar:
![testestes](/Screenshot/1-1.png)

- Mengatur interface untuk masing-masing UML pada router ```SURABAYA``` melakukan setting sysctl dengan perintah ```nano /etc/sysctl.conf```. 
- Uncommand pada ```net.ipv4.ip_forward=1``` atau hilangkan tanda pagar ```#```
- Aktifkan perubahan menggunakan perintah ```sysctl -p```
- Setting IP setiap UML dengan perintah ```nano /etc/network/interfaces```
<!--
SURABAYA (Sebagai Router / DHCP Relay)
```
```
MALANG (Sebagai DNS Server)
```
```
MOJOKERTO (Sebagai Proxy Server)
```
```
TUBAN (Sebagai DHCP Server)
```
```
GRESIK
```
```
SIDOARJO
```
```
BANYUWANGI
```
```
MADIUN
```
```
-->
- Restart network dengan perintah ```service networking restart```
- Lakukan export proxy pada setiap UML dengan perintah ```source proxy.sh```
<!--
```
export http_proxy=”http://DPTSI-apa-apa:passVPN@proxy.its.ac.id:8080”
export https_proxy=”http://DPTSI-apa-apa:passVPN@proxy.its.ac.id:8080”
export ftp_proxy=”http://DPTSI-apa-apa:passVPN@proxy.its.ac.id:8080”
```
-->
- Menggunakan perintah ```apt-get update``` untuk update setiap UML
</br></br></br>


<a name="2"></a>
## SOAL NO 2
### SURABAYA ditunjuk sebagai perantara (DHCP Relay) antara DHCP Server dan client
- Jalankan perintah ```apt-get install isc-dhcp-server``` pada UML **TUBAN**
- Buka file konfigurasi interface ```nano /etc/default/isc-dhcp-server``` untuk menentukan interface.
![testestes](/Screenshot/2-1.png)

- Jalankan perintah ```apt-get install isc-dhcp-relay``` pada UML **SURABAYA**
![testestes](/Screenshot/2-2.png)
![testestes](/Screenshot/2-3.png)

- Pada UML **TUBAN** buka file konfigurasi DHCP dengan perintah ```nano /etc/dhcp/dhcpd.conf```
- Tambahkan script seperti:</br>
![testestes](revisi-3.png)

- Restart service dengan perintah ```service isc-dhcp-server restart```
</br></br></br>


<a name="3"></a>
## SOAL NO 3
### Client pada subnet 1 mendapatkan range IP dari 192.168.0.10 sampai 192.168.0.100 dan 192.168.0.110 sampai 192.168.0.200.
- Pada UML **TUBAN** edit file ```nano /etc/default/isc-dhcp-server``` pada interface diisi ```eth0```
- Buka file konfigurasi DHCP dengan perintah ```nano /etc/dhcp/dhcpd.conf``` dan edit file menjedi seperti:
![testestes](/Screenshot/revisi-1.png)

- Pada UML **SIDOARJO** buka ```nano /etc/network/interfaces``` untuk mengonfigurasi interface SIDOARJO.
- Lalu tambahkan 
  ```
  auto eth0
  iface eth0 inet dhcp
  ```
  ![testestes](/Screenshot/3-2.png)

- Lakukan perintah ```service networking restart``` untuk merestart network
![testestes](/Screenshot/3-3.png)
</br></br></br>


<a name="4"></a>
## SOAL NO 4
### Client pada subnet 3 mendapatkan range IP dari 192.168.1.50 sampai 192.168.1.70.
- Pada UML **TUBAN** edit file ```nano /etc/default/isc-dhcp-server``` pada interface diisi ```eth0```
- Buka file konfigurasi DHCP dengan perintah ```nano /etc/dhcp/dhcpd.conf``` dan edit file menjedi seperti:
![testestes](/Screenshot/revisi-2.png)

- Pada UML **BANYUWANGI** buka ```nano /etc/network/interfaces``` untuk mengonfigurasi interface BANYUWANGI.
![testestes](/Screenshot/4-2.png)


- Lakukan perintah ```service networking restart``` untuk merestart network
![testestes](/Screenshot/4-3.png)
</br></br></br>


<a name="5"></a>
## SOAL NO 5
### Client mendapatkan DNS Malang dan DNS 202.46.129.2 dari DHCP
- Pada UML **TUBAN** edit file ```nano /etc/default/isc-dhcp-server``` pada interface diisi ```eth0```
- Buka file konfigurasi DHCP dengan perintah ```nano /etc/dhcp/dhcpd.conf``` dan edit file tambahkan ```option domain-name-servers 10.151.83.106, 202.46.129.2```</br>
  ![testestes](/Screenshot/revisi-2.png)

- Periksa pada UML **SIDOARJO** apakah DNS server sudah sesuai konfigurasi dengan menggunakan perintah ```cat /etc/resolv.conf```</br>
![testestes](/Screenshot/5-1.png)
</br></br></br>


<a name="6"></a>
## SOAL NO 6
### Client di subnet 1 mendapatkan peminjaman alamat IP selama 5 menit, sedangkan client pada subnet 3 mendapatkan peminjaman IP selama 10 menit.
- Pada UML **TUBAN** edit file ```nano /etc/default/isc-dhcp-server``` pada interface diisi ```eth0```
- Buka file konfigurasi DHCP dengan perintah ```nano /etc/dhcp/dhcpd.conf``` dan edit file dan tambahkan:
  - pada subnet 1
      ```
      default-lease-time 300;
      max-lease-time 300;
      ```
  - pada subnet 3
      ```
      default-lease-time 600;
      max-lease-time 600;
      ```
  ![testestes](/Screenshot/revisi-2.png)

- Pada UML **SIDOARJO** lakukan perintah ```service networking restart``` untuk merestart network
![testestes](/Screenshot/6-1.png)

- Pada UML **BANYUWANGI** lakukan perintah ```service networking restart``` untuk merestart network
![testestes](/Screenshot/6-2.png)
</br></br></br>


<a name="7"></a>
## SOAL NO 7
### Pertama, akses ke proxy hanya bisa dilakukan oleh Anri sendiri sebagai user TA. User autentikasi milik Anri memiliki format: User : userta_b12, Password : inipassw0rdta_b12
- Pada UML **MOJOKERTO** install squid dengan perintah ```apt-get install squid```
- Pada konfigurasi ```nano /etc/squid3/squid.conf``` tambahkan
  ```
  http_port 8080
  visible_hostname mojokerto
  ```
  ![testestes](/Screenshot/7-1.png)
- Lalukan restart squid3 dengan perintah ```service squid3 restart```
- Atur proxy browser pada device

- Pada UML **MOJOKERTO** install apache2-utils dengan perintah ```pt-get install apache2-utils```
- Dengan perintah ```htpasswd -c /etc/squid/passwd userta_b12``` membuat user dan password.
![testestes](/Screenshot/7-2.png)

- Buka file konfigurasi dengan perintah ```nano /etc/squid/squid.conf``` untuk menambahkan
  ```
  auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/passwd
  auth_param basic children 5
  auth_param basic realm Proxy
  auth_param basic credentialsttl 2 hours
  auth_param basic casesensitive on
  acl USERS proxy_auth REQUIRED
  http_access allow USERS
  ```

- Lakukan restart squid3 dengan perintah ```service squid3 restart```, maka saat diakses akan muncul autentikasi seperti:
![testestes](/Screenshot/7-3.png)
</br></br></br>


<a name="8"></a>
## SOAL NO 8
### Anri sudah menjadwal pengerjaan TA-nya, setiap hari Selasa-Rabu pukul 13.00-18.00. Bu Meguri membatasi penggunaan internet Anri hanya pada jadwal yang telah ditentukan itu saja. Maka diluar jam tersebut, Anri tidak dapat mengakses jaringan internet dengan proxy tersebut. Jadwal bimbingan dengan Bu Meguri adalah
<!--![testestes](/Screenshot/8-1.png)-->
- Pada UML **MOJOKERTO** buka file konfigurasi dengan perintah ```nano /etc/squid/squid.conf``` untuk menambahkan:
  ```
  acl WAKTU_TA time TW 13:00-18:00
  http_access allow WAKTU_TA
  ```
  ![testestes](/Screenshot/9-1.png)
 
- Lakukan restart squid3 dengan perintah ```service squid3 restart```
</br></br></br>


<a name="9"></a>
## SOAL NO 9
###  setiap hari Selasa-Kamis pukul 21.00 - 09.00 keesokan harinya (sampai Jumat jam 09.00). Agar Anri bisa fokus mengerjakan TA, 
<!--![testestes](/Screenshot/9-1.png)-->
- Pada UML **MOJOKERTO** buka file konfigurasi dengan perintah ```nano /etc/squid/squid.conf``` untuk menambahkan:
  ```
  acl WAKTU_TA time TW 13:00-18:00
  acl WAKTU_BIMBINGAN_1 time TWH 21:00-23:59
  acl WAKTU_BIMBINGAN_2 time WHF 00:00-09:00
  
  http_access allow USERS WAKTU_TA
  http_access allow USERS WAKTU_BIMBINGAN_1
  http_access allow USERS WAKTU_BIMBINGAN_2
  ```
  ![testestes](/Screenshot/9-0.jpg)
 
- Lakukan restart squid3 dengan perintah ```service squid3 restart```
</br></br></br>


<a name="10"></a>
## SOAL NO 10
###  setiap dia mengakses google.com, maka akan di redirect menuju monta.if.its.ac.id agar Anri selalu ingat untuk mengerjakan TA🙂
<!--![testestes](/Screenshot/10-1.png)-->
- Pada UML **MOJOKERTO** buka file konfigurasi dengan perintah ```nano /etc/squid/squid.conf``` untuk menambahkan:
  ```
  acl google-site dstdomain .google.com
  deny_info http://monta.if.its.ac.id all
  
  http_reply_access deny google-site all
  
  http_access allow USERS 
  http_access allow deny all
  ```
  ![testestes](/Screenshot/8-1.png)

- Lakukan restart squid3 dengan perintah ```service squid3 restart```
</br></br></br>


<a name="11"></a>
## SOAL NO 11
### Untuk menandakan bahwa Proxy Server ini adalah Proxy yang dibuat oleh Anri, Bu Meguri meminta Anri untuk mengubah error page default squid menjadi seperti berikut: 
![testestes](/Screenshot/soal11.jpg)
### (Note : File error page bisa diunduh dengan cara wget 10.151.36.202/ERR_ACCESS_DENIED Tidak perlu di extract, cukup cp -r)
- Download file error page dengan perintah ```wget 10.151.36.202/ERR_ACCESS_DENIED``` pada direktori ```/usr/share/squid/errors/en``` maka akan tersimpan di ***ERR_ACCESS_DENIED.1*** 
- Hapus file ***ERR_ACCESS_DENIED*** yang ada dengan perintah ```rm ERR_ACCESS_DENIED```
- Menggunakan perintah ```mv ERR_ACCESS_DENIED.1 ERR_ACCESS_DENIED``` untuk memindahkan file page error ke ***ERR_ACCESS_DENIED***
- Lakukan restart squid3 dengan perintah ```service squid3 restart```
![testestes](/Screenshot/11-1.png)

- Akses ```its.ac.id``` maka hasilnya: 
![testestes](/Screenshot/11-2.png)
</br></br></br>


<a name="12"></a>
## SOAL NO 12
### Karena Bu Meguri dan Anri adalah tipe orang pelupa, maka untuk memudahkan mereka, Anri memiliki ide ketika menggunakan proxy cukup dengan mengetikkan domain janganlupa-ta.b12.pw dan memasukkan port 8080. 
- Lakukan setting DNS Server pada UML **MALANG** dengan instalasi ```apt-get install bind9 -y```
- Edit file konfigurasi dengan perintah ```nano /etc/bind/named.conf.local``` seperti gambar:
![testestes](/Screenshot/12-1.png)

- Buat folder ***jarkom*** dengan perintah ```mkdir /etc/bind/jarkom```
- Copy file _db.local_ dengan perintah ```cp /etc/bind/db.local /etc/bind/jarkom/janganlupa-ta.b12.pw```
- Buka file tersebut dan edit dengan perintah ```nano /etc/bind/jarkom/janganlupa-ta.b12.pw```
- Edit seperti: </br>
  ![testestes](/Screenshot/12-2.png)

- Menggunakan perintah ```service bind9 restart``` untuk merestart.

- Atur proxy browser pada device dengan IP Address ```janganlupa-ta.b12.pw``` dan port ```8080```
![testestes](/Screenshot/12-3.png)
</br></br></br>

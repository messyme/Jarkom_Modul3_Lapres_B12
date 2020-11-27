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
</br></br></br>


<a name="2"></a>
## SOAL NO 2
### SURABAYA ditunjuk sebagai perantara (DHCP Relay) antara DHCP Server dan client
![testestes](/Screenshot/2-1.png)
![testestes](/Screenshot/2-2.png)
![testestes](/Screenshot/2-3.png)
![testestes](/Screenshot/2-4.png)
</br></br></br>


<a name="3"></a>
## SOAL NO 3
### Client pada subnet 1 mendapatkan range IP dari 192.168.0.10 sampai 192.168.0.100 dan 192.168.0.110 sampai 192.168.0.200.
![testestes](/Screenshot/3-1.png)
![testestes](/Screenshot/3-2.png)
![testestes](/Screenshot/3-3.png)
</br></br></br>


<a name="4"></a>
## SOAL NO 4
### Client pada subnet 3 mendapatkan range IP dari 192.168.1.50 sampai 192.168.1.70.
![testestes](/Screenshot/4-1.png)
![testestes](/Screenshot/4-2.png)
![testestes](/Screenshot/4-3.png)
</br></br></br>


<a name="5"></a>
## SOAL NO 5
### Client mendapatkan DNS Malang dan DNS 202.46.129.2 dari DHCP
![testestes](/Screenshot/5-1.png)
</br></br></br>


<a name="6"></a>
## SOAL NO 6
### Client di subnet 1 mendapatkan peminjaman alamat IP selama 5 menit, sedangkan client pada subnet 3 mendapatkan peminjaman IP selama 10 menit.
![testestes](/Screenshot/6-1.png)
![testestes](/Screenshot/6-2.png)
</br></br></br>


<a name="7"></a>
## SOAL NO 7
### Pertama, akses ke proxy hanya bisa dilakukan oleh Anri sendiri sebagai user TA. User autentikasi milik Anri memiliki format: User : userta_b12, Password : inipassw0rdta_b12
![testestes](/Screenshot/7-1.png)
![testestes](/Screenshot/7-2.png)
![testestes](/Screenshot/7-3.png)
</br></br></br>


<a name="8"></a>
## SOAL NO 8
### Anri sudah menjadwal pengerjaan TA-nya, setiap hari Selasa-Rabu pukul 13.00-18.00. Bu Meguri membatasi penggunaan internet Anri hanya pada jadwal yang telah ditentukan itu saja. Maka diluar jam tersebut, Anri tidak dapat mengakses jaringan internet dengan proxy tersebut. Jadwal bimbingan dengan Bu Meguri adalah
![testestes](/Screenshot/7-1.png)
</br></br></br>


<a name="9"></a>
## SOAL NO 9
###  setiap hari Selasa-Kamis pukul 21.00 - 09.00 keesokan harinya (sampai Jumat jam 09.00). Agar Anri bisa fokus mengerjakan TA, 
![testestes](/Screenshot/7-1.png)
</br></br></br>


<a name="10"></a>
## SOAL NO 10
###  setiap dia mengakses google.com, maka akan di redirect menuju monta.if.its.ac.id agar Anri selalu ingat untuk mengerjakan TA🙂
![testestes](/Screenshot/7-1.png)
</br></br></br>


<a name="11"></a>
## SOAL NO 11
### Untuk menandakan bahwa Proxy Server ini adalah Proxy yang dibuat oleh Anri, Bu Meguri meminta Anri untuk mengubah error page default squid menjadi seperti berikut: 
![testestes](/Screenshot/soal11.jpg)
### (Note : File error page bisa diunduh dengan cara wget 10.151.36.202/ERR_ACCESS_DENIED Tidak perlu di extract, cukup cp -r)
![testestes](/Screenshot/11-0.png)
![testestes](/Screenshot/11-1.png)
![testestes](/Screenshot/11-1.png)
</br></br></br>


<a name="12"></a>
## SOAL NO 12
### Karena Bu Meguri dan Anri adalah tipe orang pelupa, maka untuk memudahkan mereka, Anri memiliki ide ketika menggunakan proxy cukup dengan mengetikkan domain janganlupa-ta.b12.pw dan memasukkan port 8080. 
![testestes](/Screenshot/12-1.png)
![testestes](/Screenshot/12-2.png)
![testestes](/Screenshot/12-3.png)
</br></br></br>

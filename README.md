# Jarkom-Modul-4-E02-2021

Berikut adalah laporan resmi Praktikum Jaringan Komputer Modul 4 tahun 2021

Anggota Kelompok E02:

- 05111940000050 - Erki Kadhafi Rosyid
- 05111940000063 - Ryan Garnet Andrianto
- 05111940000141 - Muhammad Farhan Haykal

![image](./images/topologi_soal.png)

## Intro

## Cisco Packet Tracer - Metode VLSM
### Topologi

### Tree Pembagian IP

### Tabel Pembagian IP
Setelah melakukan pembagian IP menggunakan tree, daftar IP disajikan ke dalam table

| Name | Hosts Needed | Hosts Available | Unused Hosts | Network Address | Slash |       Mask      |         Usable Range        |   Broadcast  |  Wildcard |
|:----:|:------------:|:---------------:|:------------:|:---------------:|:-----:|:---------------:|:---------------------------:|:------------:|:---------:|
|  A3  |     2021     |       2046      |      25      |    10.30.0.0    |  /21  |  255.255.248.0  |   10.30.0.1 - 10.30.7.254   |  10.30.7.255 | 0.0.7.255 |
|  A6  |     1001     |       1022      |      21      |    10.30.8.0    |  /22  |  255.255.252.0  |   10.30.8.1 - 10.30.11.254  | 10.30.11.255 | 0.0.3.255 |
|  A15 |      721     |       1022      |      301     |    10.30.12.0   |  /22  |  255.255.252.0  |  10.30.12.1 - 10.30.15.254  | 10.30.15.255 | 0.0.3.255 |
|  A2  |      701     |       1022      |      321     |    10.30.16.0   |  /22  |  255.255.252.0  |  10.30.16.1 - 10.30.19.254  | 10.30.19.255 | 0.0.3.255 |
|  A9  |      521     |       1022      |      501     |    10.30.20.0   |  /22  |  255.255.252.0  |  10.30.20.1 - 10.30.23.254  | 10.30.23.255 | 0.0.3.255 |
|  A11 |      502     |       510       |       8      |    10.30.24.0   |  /23  |  255.255.254.0  |  10.30.24.1 - 10.30.25.254  | 10.30.25.255 | 0.0.1.255 |
|  A13 |      252     |       254       |       2      |    10.30.26.0   |  /24  |  255.255.255.0  |  10.30.26.1 - 10.30.26.254  | 10.30.26.255 | 0.0.0.255 |
|  A1  |      101     |       126       |      25      |    10.30.27.0   |  /25  | 255.255.255.128 |  10.30.27.1 - 10.30.27.126  | 10.30.27.127 | 0.0.0.127 |
|  A12 |      13      |        14       |       1      |   10.30.27.128  |  /28  | 255.255.255.240 | 10.30.27.129 - 10.30.27.142 | 10.30.27.143 |  0.0.0.15 |
|  A4  |       2      |        2        |       0      |   10.30.27.144  |  /30  | 255.255.255.252 | 10.30.27.145 - 10.30.27.146 | 10.30.27.147 |  0.0.0.3  |
|  A5  |       2      |        2        |       0      |   10.30.27.148  |  /30  | 255.255.255.252 | 10.30.27.149 - 10.30.27.150 | 10.30.27.151 |  0.0.0.3  |
|  A7  |       2      |        2        |       0      |   10.30.27.152  |  /30  | 255.255.255.252 | 10.30.27.153 - 10.30.27.154 | 10.30.27.155 |  0.0.0.3  |
|  A8  |       2      |        2        |       0      |   10.30.27.156  |  /30  | 255.255.255.252 | 10.30.27.157 - 10.30.27.158 | 10.30.27.159 |  0.0.0.3  |
|  A10 |       2      |        2        |       0      |   10.30.27.160  |  /30  | 255.255.255.252 | 10.30.27.161 - 10.30.27.162 | 10.30.27.163 |  0.0.0.3  |
|  A14 |       2      |        2        |       0      |   10.30.27.164  |  /30  | 255.255.255.252 | 10.30.27.165 - 10.30.27.166 | 10.30.27.167 |  0.0.0.3  |

Daftar IP dari tabel tersebut akan digunakan pada konfigurasi pada Cisco Packet Tracer, salah satu contoh nya adalah pada konfigurasi subnet A1 yang terletak pada daerah Client Jipangu. Pertama adah contoh konfigurasi Router Pucci yang mengarah gateway ke subnet A1. 

![image](./images/pucci_vlsm.png)

Pada gambar di atas, ipv4 address dari pucci diarahkan ke ip yang terdaftar di tabel subnet A1 ditambah 1. Sedangkan untuk Client Jipangu dapat dilihat seperti di bawah ini.

![image](./images/jipangu_vlsm.png)

Pada gambar di atas, Client Jipangu akan memiliki IP yang berada dalam interval usable IP yang terdapat pada table subnet A1. Pada kasus di atas, IP Jipangu akan memiliki ip yang tertera di table **ditambah 2**. Untuk host dan router lainnya akan memiliki konfigurasi serupa seperti yang telah tertera di atas

### Tabel Routing Table
Untuk mengirim paket yang melalui lebih dari satu router maka akan memerlukan routing agar paket dapat sampai di tujuan. Untuk routing table dari VLSM dapat di lihat pada gambar di bawah ini

1. Pada router FOOSHA
```
10.30.0.0/21 via 10.30.27.150
10.30.27.0/25 via 10.30.27.150
10.30.16.0/22 via 10.30.27.150
10.30.20.0/22 via 10.30.27.158
10.30.24.0/23 via 10.30.27.158
10.30.27.128/28 via 10.30.27.158
10.30.26.0/24 via 10.30.27.158
10.30.12.0/22 via 10.30.27.158
10.30.27.144/30 via 10.30.27.150
10.30.27.164/30 via 10.30.27.158
```

2. Pada router WATER7
```
0.0.0.0/0 via 10.30.27.149
10.30.27.0/25 via 10.30.27.146
10.30.0.0/21 via 10.30.27.146
```

3. Pada router PUCCI
```
0.0.0.0/0 via 10.30.27.145
```

4. Pada router GUANHAO
```
10.30.27.128/28 via 10.30.24.3
10.30.26.0/24 via 10.30.27.162
0.0.0.0/0 via 10.30.27.157
10.30.12.0/22 via 10.30.27.162
10.30.27.164/30 via 10.30.27.162
```

5. Pada router ALABASTA
```
0.0.0.0/0 via 10.30.24.1
```

6. Pada router OIMO
```
10.30.12.0/22 via 10.30.26.3
0.0.0.0/0 via 10.30.27.161
```

7. Pada router SEASTONE
```
0.0.0.0/0 via 10.30.26.1
```

Setelah konfigurasi di atas di tambahkan di setiap router, maka 

## GNS3 - Metode CIDR
### Gambar Topologi
Pada metode CIDR, kami melakukan perhitungan sebagai berikut

![image](./images/topologi_cidr.png)

Pada topologi di atas, kami tidak memperhitungkan server untuk dibuat subnet tersendiri sehingga pada hasil akhir kami mendapat IP dengan subnet terbesar yaitu `/16`

### Tree pembagian

### Tabel Pembagian IP
### Tabel Routing Table


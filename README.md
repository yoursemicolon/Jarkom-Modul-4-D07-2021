# Jarkom-Modul-4-D07-2021
### Anggota kelompok:
Anggota | NRP | 
------------- | ------------- | 
Amanda Rozi Kurnia | 05111940000094 | 
Dyandra Paramitha W. | 05111940000119 |
Daanii Nabil Ghinannafsi Kusnanta | 05111940000163 |

## Notes
[Soal Shift 4](https://docs.google.com/document/d/1hf5Vi5nbEq6YY-nqmK7XUTHGNL_KVEFVc14mW9k0FAg/edit?usp=sharing) <br>
**Prefix:** 192.195

## Daftar Isi
* [Topologi](#topologi)
* [VLSM](#vlsm)
  * [Subnetting](#vlsm-subnetting)
  * [Praktik pada GNS3](#vlsm-gns3)
<!--   * [Praktik pada CPT](#vlsm-cpt) -->
* [CIDR](#cidr)
  * [Subnetting](#cidr-subnetting)
  * [Praktik pada CPT](#cidr-cpt)
<!--   * [Praktik pada GNS3](#cidr-gns3) -->
* [Kendala](#kendala)
* [Referensi](#referensi)

## <a name="topologi"></a> Topologi
<!-- gambar topologi -->
* Pembagian IP menggunakan prefix IP yang telah ditentukan
* Pembagian IP dan routing harus seefisien mungkin
* Pastikan semua node pada GNS3 dapat melakukan ping ke its.ac.id

## <a name="vlsm"></a> VLSM
### <a name="vlsm-subnetting"></a> Subnetting
1. Melakukan subnetting pada topologi yang diberikan sehingga terbentuk 13 subnet seperti pada gambar berikut.
<image src="img/1.png" width="700">

2. Menentukan jumlah alamat IP yang dibutuhkan oleh tiap subnet dan melakukan *labelling* netmask berdasarkan jumlah IP yang dibutuhkan <br>

Subnet | Jumlah IP | Netmask |
------------- | ------------- | ------------- | 
A1 | 1001 | /22 | 
A2 | 2 | /30 |
A3 | 701 | /22 |
A4 | 2 | /30
A5 | 2021 | /21 |
A6 | 101 | /25 |
A7 | 13 | /28 |
A8 | 502 | /23 |
A9 | 2 | /30 |
A10 | 521 | /22 |
A11 | 2 | /30 |
A12 | 721 | /22 |
A13 | 252 | /24 |
Total | 5841 | /19 |

3. Subnet besar yang dibentuk memiliki NID <......> dengan netmask /19. Perhitungan pembagian IP berdasarkan NID dan netmask menggunakan pohon sebagai berikut
<image src="img/vlsm.png" width="700">
<image src="img/nid-vlsm.PNG" width="700">


<!-- ### <a name="vlsm-cpt"></a> Praktik pada CPT -->
### <a name="vlsm-gns3"></a> Praktik pada GNS3
#### Topologi ####
Sebelum melakukan konfigurasi, terlebih dahulu dibuat topologi pada GNS. 
<image src="img/topologi-gns.png" width="700">

Agar dapat terhubung dengan internet, maka dihubungkan dengan DHCP dan melakukan command `echo nameserver 192.168.122.1 > /etc/resolv.conf`

#### Konfigurasi IP ####
Setting IP untuk setiap node pada file /etc/network/interfaces sesuai dengan pembagian IP pada setiap subnet. 

##### Foosha (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
        address 192.195.8.1
        netmask 255.255.252.0

auto eth2
iface eth2 inet static
         address 192.195.27.146
         netmask 255.255.255.252

auto eth3
iface eth3 inet static
       address 192.195.27.154
       netmask 255.255.255.252
```
<image src="img/foosha-1.PNG" width="700">

##### Water7 (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.27.145
netmask 255.255.255.252

auto eth1
iface eth1 inet static
address 192.195.12.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.195.27.149
netmask 255.255.255.252
```


<image src="img/water7.PNG" width="700">

##### Pucci (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.27.150
netmask 255.255.255.252

auto eth1
iface eth1 inet static
address 192.195.27.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 192.195.0.1
netmask 255.255.248.0
```


<image src="img/pucci.PNG" width="700">

##### Guanhao (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.27.153
netmask 255.255.255.252

auto eth1
iface eth1 inet static
address 192.195.16.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.195.27.157
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 192.195.24.1
netmask 255.255.254.0
```

<image src="img/guanhao1.PNG" width="700">
<image src="img/guanhao2.PNG" width="700">

##### Alabasta (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.24.3
netmask 255.255.254.0

auto eth1
iface eth1 inet static
address 192.195.27.129
netmask 255.255.255.240
```

<image src="img/alabasta.PNG" width="700">

##### OIMO (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.27.158
netmask 255.255.255.252

auto eth1
iface eth1 inet static
address 192.195.26.1
netmask 255.255.255.0
```

<image src="img/oimo.PNG" width="700">

##### SEASTONE (Sebagai Router) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.26.2
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.195.20.1
netmask 255.255.252.0
```

<image src="img/seastone.PNG" width="700">


##### BLUENO (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.8.2
netmask 255.255.252.0
gateway 192.195.8.1
```

<image src="img/blueno.PNG" width="700">

##### CIPHER (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.12.2
netmask 255.255.252.0
gateway 192.195.12.1
```

<image src="img/cipher.PNG" width="700">

##### JIPANGU (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.27.2
netmask 255.255.255.128
gateway 192.195.27.1
```

<image src="img/jipangu.PNG" width="700">

##### COURTYARD (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.0.2
netmask 255.255.248.0
gateway 192.195.0.1
```

<image src="img/courtyard.PNG" width="700">

##### CALMBELT (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.0.3
netmask 255.255.248.0
gateway 192.195.0.1
```

<image src="img/calmbelt.PNG" width="700">

##### JABRA (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.16.2
netmask 255.255.252.0
gateway 192.195.16.1
```

<image src="img/jabra.PNG" width="700">

##### MAINGATE (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.24.2
netmask 255.255.254.0
gateway 192.195.24.1
```

<image src="img/maingate.PNG" width="700">

##### Jorge (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.27.130
netmask 255.255.255.240
gateway 192.195.27.129
```

<image src="img/jorge.PNG" width="700">

##### Ennieslobby (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.26.2
netmask 255.255.255.0
gateway 192.195.26.1
```

<image src="img/ennieslobby.PNG" width="700">

##### Elena (Sebagai Client) #####
```bash
auto eth0
iface eth0 inet static
address 192.195.20.2
netmask 255.255.252.0
gateway 192.195.20.1
```

<image src="img/elena.PNG" width="700">

#### Konfigurasi Router ####
##### Foosha #####

```bash
route add -net 192.195.0.0 netmask 255.255.248.0 gateway 192.195.27.145
route add -net 192.195.12.0 netmask 255.255.252.0 gateway 192.195.27.145
route add -net 192.195.16.0 netmask 255.255.252.0 gateway 192.195.27.153
route add -net 192.195.20.0 netmask 255.255.252.0 gateway 192.195.27.153
route add -net 192.195.24.0 netmask 255.255.254.0 gateway 192.195.27.153
route add -net 192.195.26.0 netmask 255.255.255.0 gateway 192.195.27.153
route add -net 192.195.27.0 netmask 255.255.255.128 gateway 192.195.27.145
route add -net 192.195.27.128 netmask 255.255.255.240 gateway 192.195.27.153
route add -net 192.195.27.156 netmask 255.255.255.252 gateway 192.195.27.153
route add -net 192.195.27.148 netmask 255.255.255.252 gateway 192.195.27.1 
```
Apabila dilihat menggunakan command `route -n`:

<image src="img/foosha-2.PNG" width="700">

##### Water7 #####

```bash
route add -net 192.195.0.0 netmask 255.255.248.0 gateway 192.195.27.150
route add -net 192.195.27.0 netmask 255.255.255.128 gateway 192.195.27.150
route add -net 0.0.0.0 netmask 0.0.0.0 gateway 192.195.27.146
```
Apabila dilihat menggunakan command `route -n`:

<image src="img/water7-1.PNG" width="700">

##### Pucci #####

```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gateway 192.195.27.149
```

Apabila dilihat menggunakan command `route -n`:

<image src="img/pucci-1.PNG" width="700">

##### GUANHAO #####
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gateway 192.195.27.154
route add -net 192.195.20.0 netmask 255.255.252.0 gateway 192.195.27.158
route add -net 192.195.26.0 netmask 255.255.255.0 gateway 192.195.27.158
route add -net 192.195.27.128 netmask 255.255.255.240 gateway 192.195.24.3
```

Apabila dilihat menggunakan command `route -n`:

<image src="img/guanhao3.PNG" width="700">

##### ALABASTA #####
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gateway 192.195.24.1
```

Apabila dilihat menggunakan command `route -n`:

<image src="img/alabasta-1.PNG" width="700">

##### OIMO #####
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gateway 192.195.27.157
route add -net 192.195.20.0  netmask 255.255.252.0 gateway 192.195.26.2
```

Apabila dilihat menggunakan command `route -n`:

<image src="img/oimo-1.PNG" width="700">

##### SEASTONE #####
```bash
route add -net 0.0.0.0 netmask 0.0.0.0 gateway 192.195.26.1
```
Apabila dilihat menggunakan command `route -n`:

<image src="img/seastone-1.PNG" width="700">

#### Testing ####
- ping its.ac.id dari ELENA

  <image src="img/testing1.PNG" width="700">
- ping its.ac.id dari CALMBELT

  <image src="img/testing2.PNG" width="700">
- ping its.ac.id dari CIPHER

  <image src="img/testing3.PNG" width="700">

- ping its.ac.id dari PUCCI

  <image src="img/testing4.PNG" width="700">

- ping its.ac.id dari ENIESLOBBY

  <image src="img/testing5.PNG" width="700">

- ping its.ac.id dari JORGE

  <image src="img/testing6.PNG" width="700">

- ping dari OIMO ke PUCCI

  <image src="img/testing6.PNG" width="700">

- ping dari PUCCI ke MAINGATE

  <image src="img/testing7.PNG" width="700">

- ping dari ELENA ke COURTYARD

  <image src="img/testing8.PNG" width="700">

- ping dari JABRA ke JIPANGU

  <image src="img/testing9.PNG" width="700">
  
## <a name="cidr"></a> CIDR
### <a name="cidr-subnetting"></a> Subnetting
### <a name="cidr-cpt"></a> Praktik pada CPT
<!-- ### <a name="cidr-gns3"></a> Praktik pada GNS3 -->

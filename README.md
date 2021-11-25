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

## <a name="topologi"></a> Topologi
<!-- gambar topologi -->
* Pembagian IP menggunakan prefix IP yang telah ditentukan
* Pembagian IP dan routing harus seefisien mungkin
* Pastikan semua node pada GNS3 dapat melakukan ping ke its.ac.id

## <a name="vlsm"></a> VLSM
### <a name="vlsm-subnetting"></a> Subnetting
1. Melakukan subnetting pada topologi yang diberikan sehingga terbentuk 13 subnet seperti pada gambar berikut.
<!-- gambar subnetting pada topologi -->

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


<!-- ### <a name="vlsm-cpt"></a> Praktik pada CPT -->
### <a name="vlsm-gns3"></a> Praktik pada GNS3

## <a name="cidr"></a> CIDR
### <a name="cidr-subnetting"></a> Subnetting
### <a name="cidr-cpt"></a> Praktik pada CPT
<!-- ### <a name="cidr-gns3"></a> Praktik pada GNS3 -->

# Forensik

## Penulis: [Rifqihz](https://github.com/rifqihz)
## Daftar Isi:

| Forensik  |
| ------------- |
| [Glory of the Garden](#1-glory-of-the-garden-50-pts)|
| [So Meta](#2-so-meta-150-pts)|
| [What Lies Within](#3-what-lies-within-150-pts)|
| [Shark on wire 1](#4-shark-on-wire-1-150-pts)|
| [WhitePages](#5-whitepages-250-pts)|
| [like1000](#6-like1000-250-pts)|
| [Investigative Reversing 0](#7-investigative-reversing-0-300-pts)|

---
## 1. Glory of the Garden (50 pts)

### Soal:

This [garden](https://2019shell1.picoctf.com/static/438c667542717e152254bb4ae9297eb1/garden.jpg) contains more than it seems.
    
### Pembahasan:

Gunakan `strings` lalu flagnya ada di baris terakhir
<details>
<summary>Tekan untuk melihat flag</summary>
picoCTF{more_than_m33ts_the_3y35a97d3bB}
</details>

## 2. So Meta (150 pts)

### Soal:
Find the [flag](https://2019shell1.picoctf.com/static/61e816c3ab6abee2bda49f438bd49571/pico_img.png) in this picture.

### Pembahasan:

Gunakan `exiftool` untuk melihat [metadata](https://id.wikipedia.org/wiki/Metadata) dari gambar. Flagnya terdapat di bagian Artist
<details>
<summary>Tekan untuk melihat flag</summary>
picoCTF{s0_m3ta_43f253bb}
</details>

## 3. What Lies Within (150 pts)
### Soal:
Theres something in the [building](https://2019shell1.picoctf.com/static/aec3861fc4d5bce4d39dc0db196426de/buildings.png). Can you retrieve the flag?
### Pembahasan:
Menggunakan [zsteg](https://github.com/zed-0xff/zsteg) untuk menemukan flag yang tersembunyi di dalam gambar
<details>
<summary>Tekan untuk melihat flag</summary>
picoCTF{h1d1ng_1n_th3_b1t5}
</details>

## 4. shark on wire 1 (150 pts)
### Soal:
We found this [packet capture](https://2019shell1.picoctf.com/static/ae9ca8cff43ed638ed5d137f9ece7455/capture.pcap). Recover the flag
### Pembahasan:
Lakukan follow stream pada protokol UDP hingga stream ke 6
<details>
<summary>Tekan untuk melihat flag</summary>
picoCTF{StaT31355_636f6e6e}
</details>

## 5. WhitePages (250 pts)

### Soal:
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://2019shell1.picoctf.com/static/e134178261c6fa36e9058d5408118dd9/whitepages.txt) is all blank!
### Pembahasan:
File whitepages dibuka dengan text editor, lalu copy karakter pertama lalu ganti semua karakter yang sama/sesuai dengan karakter pertama dengan angka 0,lalu karakter kosong yang ada diantara angka 0 di copy lalu diganti semua dengan angka 1.  
Hasilnya akan menjadi seperti ini : 
```
00001010000010010000100101110000011010010110001101101111010000110101010001000110000010100000101000001001000010010101001101000101010001010010000001010000010101010100001001001100010010010100001100100000010100100100010101000011010011110101001001000100010100110010000000100110001000000100001001000001010000110100101101000111010100100100111101010101010011100100010000100000010100100100010101010000010011110101001001010100000010100000100100001001001101010011000000110000001100000010000001000110011011110111001001100010011001010111001100100000010000010111011001100101001011000010000001010000011010010111010001110100011100110110001001110101011100100110011101101000001011000010000001010000010000010010000000110001001101010011001000110001001100110000101000001001000010010111000001101001011000110110111101000011010101000100011001111011011011100110111101110100010111110110000101101100011011000101111101110011011100000110000101100011011001010111001101011111011000010111001001100101010111110110001101110010011001010110000101110100011001010110010001011111011001010111000101110101011000010110110001011111011001000110010000110101011000110011001001100101001100100110011000110111001101110110011000111000001110010110011000110011001100000011010100110001011000110011100000110010011000100110011001100101011001010011011101100100001110010011100100110110011001010110011001111101000010100000100100001001
```
Lalu decode hasil binarynya (bisa memakai [cyberchef](https://gchq.github.io/CyberChef/)) lalu ubah ke text  
<details>
<summary>Tekan untuk melihat flag</summary>
picoCTF{not_all_spaces_are_created_equal_dd5c2e2f77f89f3051c82bfee7d996ef}
</details>

## 6. like1000 (250 pts)
### Soal:

### Pembahasan:

<details>
<summary>Tekan untuk melihat flag</summary>
</details>

## 7. Investigative Reversing 0 (300 pts)
### Soal:

### Pembahasan:

<details>
<summary>Tekan untuk melihat flag</summary>
</details>

# Forensik

## Penulis: Saihan Nabawi
## Daftar Isi:

| Forensik  |
| ------------- |
| [unzip](#1-unzip-50)|
| [extensions](#2-extensions-150)|
| [c0rrupt](#3-c0rrupt-250)|
| [m00nwalk](#4-m00nwalk-250)|
| [shark on wire 2](#5-shark-on-wire-2-300)|
| [m00nwalk2]()|
| [Investigative Reversing 1]()|

---
## 1. unzip (50)

### Soal:

Can you unzip this [file](https://2019shell1.picoctf.com/static/37762a7e5774d7d6c1bc79e8e1758ef9/flag.zip) and get the flag?
    
### Pembahasan:

kita bisa menemukan flag dengan mengekstrak file flag.zip

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCtf{unz1pp1ng_1s_3a5y}
  ```
</details>

## 2. extensions (150)

### Soal:

This is a really weird text file [TXT](https://2019shell1.picoctf.com/static/45886ed4b6d5d1dc74c4944fcf4b4041/flag.txt)? Can you find the flag?

### Pembahasan:

pertama kita coba melihat isi dari "flag.txt" menggunakan text editor atau command cat

```
┌─[nabawi@parrot]─[~/Downloads]
└──╼ $cat flag.txt 
�PNG
�
IHDR���^�sRGB���gAMA��
                      �a	pHYs%%IR$�&�IDA
```

muncul sejumlah karakter dengan header PNG, lalu ubah ekstensi dari txt ke png maka flag akan ditemukan

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{now_you_know_about_extensions}
  ```
</details>

## 3. c0rrupt (250)

### soal : 

We found this [file](https://2019shell1.picoctf.com/static/3435d990f1d20fe3563cbb897b4c96db/mystery). Recover the flag. You can also find the file in /problems/c0rrupt_0_1fcad1344c25a122a00721e4af86de13.

### pembahasan :

pertama kita kita coba cek menggunakan command file

```
┌─[nabawi@parrot]─[~/Downloads]
└──╼ $file mystery 
mystery: data
```

mencoba buka menggunakan hex editor terdapat footer file PNG tetapi header bukan PNG

header : 
```
89 65 4E 34 0D 0A B0
```
footer :
```
49 45 4E 44 AE 42 60 82
```
Ubah header dari "89 65 4E 34 0D 0A B0" ke "89 50 4E 47 0D 0A 1A 0A"

lalu kita coba cek menggunakan pngcheck

```
┌─[nabawi@parrot]─[~/Downloads]
└──╼ $pngcheck mystery 
mystery:  invalid chunk name "C"DR" (43 22 44 52)
ERROR: mystery
```
terlihat error di chunk "C"DR" kita ubah ke chunk name "C"DR" menjadi "IHDR" menggunakan hex editor
 setelah itu kita cek kembali dan akan terlihat seperti ini

```
┌─[nabawi@parrot]─[~/Downloads]
└──╼ $pngcheck mystery 
mystery  CRC error in chunk pHYs (computed 38d82c82, expected 495224f0)
ERROR: mystery
```
kita rubah crc dari chunk pHYs yang tadinya "49 52 24 f0" menjadi "38 d8 2c 82". setelah itu kita coba cek lagi  dengan pngcheck.

```
┌─[✗]─[nabawi@parrot]─[~/Downloads]
└──╼ $pngcheck mystery 
mystery invalid chunk length (too large)
ERROR: mystery
```
karena tidak ter spesifikasi mana chunk yang error kita akan coba cek chunk ya satu persatu, setelah di telaah ternyata ada chunk .DET, yang mana bukan merupakan chunk dari PNG, kita rubah chunknyake IDAT lalu merubah length nya dari AA AA FF A5 menjadi 00 00 FF A5 lalu kita coba check lagi

```
┌─[✗]─[nabawi@parrot]─[~/Downloads]
└──╼ $pngcheck mystery 
OK: mystery (1642x1095, 24-bit RGB, non-interlaced, 96.3%).
```
lalu kita bisa buka dengan aplikasi penampil gambar

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{c0rrupt10n_1847995}
  ```
</details>

## 4. m00nwalk (250)
 
### Soal :

Decode this [message](https://2019shell1.picoctf.com/static/fe892e7bef69b386ce5638053c0d312c/message.wav) from the moon. You can also find the file in /problems/m00nwalk_0_05441e9344c829ba5a648e8b28ef1564.

### Pembahasan :

untuk mendapatkan flag, kita bisa merekam kembali suara menggunakan aplikasi sstv decoder.

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{beep_boop_im_in_space}
  ```
</details>

## 5. shark on wire 2 (300)

### Soal :

We found this [packet capture](https://2019shell1.picoctf.com/static/dcd259894e0efe9d6e91da2af47e6369/capture.pcap). Recover the flag that was pilfered from the network. You can also find the file in /problems/shark-on-wire-2_0_3e92bfbdb2f6d0e25b8d019453fdbf07.

### Pembahasan :

Pertama kita buka file capture.pcap menggunakan wireshark, lalu kita follow udp stream, kita bisa temukan di stream ke 32 "start" dari ip "10.0.0.66", setelah itu kita temukan pada stream berikutnya "aaaaaa" tetapi dari ip yang sama, kita filter ip address ke "10.0.0.66", kita dapat lihat ip "10.0.0.66" mengirim menggunakan udp protocol ke setiap port berbeda, lalu kita tulis portnya dan kita dapatkan bilangan desimal:

```
112 105 099 111 067 084 070 123 112 049 076 076 102 051 114 051 100 095 100 097 116 097 095 118 049 097 095 115 116 051 103 048 125
```

lalu kita rubah ke ascii, dan kita akan mendapat flag nya.

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{p1LLf3r3d_data_v1a_st3g0}
  ```
</details>
 

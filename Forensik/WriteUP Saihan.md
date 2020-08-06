# Forensik

## Penulis: Saihan Nabawi
## Daftar Isi:

| Forensik  |
| ------------- |
| [unzip]()|
| [extensions]()|
| [c0rrupt]()|
| [m00nwalk]()|
| [shark on wire 2]()|
| [m00nwalk2]()|
| [Investigative Reversing 1]()|

---
## 1. unzip

### Soal:

Can you unzip this file and get the flag?
    
### Pembahasan:

kita bisa menemukan flag dengan mengekstrak file flag.zip

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCtf{unz1pp1ng_1s_3a5y}
  ```
</details>

## 2. extensions

### Soal:

This is a really weird text file TXT? Can you find the flag?

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

## c0rrupt

### soal : 

We found this file. Recover the flag. You can also find the file in /problems/c0rrupt_0_1fcad1344c25a122a00721e4af86de13.

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
terlihat error di chunk "C"DR" kita ubah ke chunk name "C"DR" menjadi "IHDR" menggunakan hex editor. setelah itu kita cek kembali dan akan terlihat seperti ini

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
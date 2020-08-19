# Keterampilan Umum

## Penulis: [joulephicar](https://github.com/joulephicar)
## Daftar Isi:

| Keterampilan Umum                                |
| ------------------------------------------------ |
| [The Factory’s Secret](#1-the-factorys-secret-1) |
| [2Warm](#2-2warm-50)                             |
| [Lets Warm Up](#3-lets-warm-up-50)               |
| [Warmed Up](#4-warmed-up-50)                     |
| [Bases](#5-bases-50)                             |
| [First Grep](#6-first-grep-50)                   |
| [Resources](#7-resources-50)                     |
| [strings it](#8-strings-it-50)|

---
## 1. The Factory’s Secret (1)

### Soal:

There appear to be some mysterious glyphs hidden inside this [abandoned factory](https://2019game.picoctf.com/game)... I wonder what would happen if you collected them all?

### Pembahasan:

Soal ini berkaitan dengan *story* yang ada pada game picoCTF 2019. Anda diminta untuk mencari beberapa potongan *glyph* yang tersebar di beberapa ruangan dan nantinya didapat sebuah *qr code* yang berisi kata sandi untuk dimasukan ke dalam komputer agar mendapatkan flagnya. Write-UP lebih lengkap telah dibuat oleh **Andrew Chang** atau **fourthpencil** melalui [kanal youtubenya](https://www.youtube.com/channel/UCcL-1qHt9A8CIHtyfIM0ILA).

## 2. 2Warm (50)

### Soal:

Can you convert the number 42 (base 10) to binary (base 2)?

### Pembahasan:

Kita dapat menggunakan *tools online* maupun kalkulator bawaan OS (Windows maupun Linux). Selain itu, kita bisa melakukan konversi memakai python dengan fungsi <code>bin()</code> berikut contohnya di ipython.

```py
In [1]: bin(42)                                           
Out[1]: '0b101010'
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{101010}
  ```
</details>

## 3. Lets Warm Up (50)

### Soal:

If I told you a word started with <code>0x70</code> in hexadecimal, what would it start with in ASCII?

### Pembahasan:

Sama seperti soal sebelumnya, untuk mengubah heksadesimal ke [ASCII](https://duckduckgo.com/?q=ascii) dapat menggunakan kalkulator maupun bahasa python. Untuk bahasa python kita dapat menggunakan fungsi <code>chr()</code>

```py
In [1]: chr(0x70)
Out[1]: 'p'
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{p}
  ```
</details>

## 4. Warmed Up (50)

### Soal:

What is 0x3D (base 16) in decimal (base 10).

### Pembahasan:

Seperti biasa, kita dapat menggunakan python dengan langsung mengetik "0x3d" di interpreternya.

```py
In [1]: 0x3d                                             
Out[1]: 61
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{61}
  ```
</details>

## 5. Bases (50)

### Soal:

What does this <code>bDNhcm5fdGgzX3IwcDM1</code> mean? I think it has something to do with bases.

### Pembahasan:

Untuk soal ini, terdapat hint berupa **bases**, jika mencari kata kunci tersebut ditambah kata *encode / decode* maka terdapat satu kosa kata yaitu *radix* dan *base32, base64, base85,* dst. Dari daftar *radix / base* yang terkenal kita bisa melihat bentuk kata ini mirip dengan hasil *encode base64*. Maka bisa kita coba di python menggunakan library **base64** untuk melakukan *decode*.

```py
import base64
unk_s = "bDNhcm5fdGgzX3IwcDM1"
dec_s = base64.b64decode(unk_s)

print("picoCTF{" + str(dec_s)[2:-1] + "}")
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{l3arn_th3_r0p35}
  ```
</details>

## 6. First Grep (50)

### Soal:

Can you find the flag in [file?](https://2019shell1.picoctf.com/static/458ae91cb23746189bf490f0c8d9a919/file) This would be really tedious to look through manually, something tells me there is a better way. You can also find the file in /problems/first-grep_2_04dbf496b78e6c37c0097cdfef734d88 on the shell server.

### Pembahasan:

Untuk soal ini, sesuai dengan judulnya kita menggunakan command *grep* yang tersedia di *shell*. 

```bash
$ grep "picoCTF" file
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{grep_is_good_to_find_things_eda8911c}
  ```
</details>

## 7. Resources (50)

### Soal:

We put together a bunch of resources to help you out on our website! If you go over there, you might even find a flag! https://picoctf.com/resources

### Pembahasan:

Flag berada pada halaman tersebut.

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{r3source_pag3_f1ag}
  ```
</details>

## 8. strings it (50)

### Soal:

Can you find the flag in file without running it? You can also find the file in /problems/strings-it_5_1fd17da9526a76a4fffce289dee10fbb on the shell server.

### Pembahasan:

Menggunakan perintah "strings" kita dapat menemukan flagnya.

```bash
$ strings strings | grep "picoCTF"
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{5tRIng5_1T_dd38f284}
  ```
</details>


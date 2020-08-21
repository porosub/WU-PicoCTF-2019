# Kriptografi

## Penulis: [vnwrywn]
## Daftar Isi:

| Kriptografi           |
| -------------         |
| [The Numbers]()|
| [13]()|
| [Easy1]()|
| [Caesar]()|
| [Flags]()|
| [Mr-Worldwide](#1-Mr-Worldwide-200)|
| [Tapping](#2-Tapping-200)|

---
## 1. Mr-Worldwide (200)

### Soal:
A musician left us a [message](https://2019shell1.picoctf.com/static/46e165b0a953075440f3a544fdb4cff1/message.txt). What's it mean?
...

### Pembahasan:
Pada challenge ini kita diberikan serangkaian angka yang dikelompokkan. Di mana dalam satu kelompok terdapat dua bilangan yang disusun seperti sebuah koordinat. Koordinat-koordinat ini dapat dicari menggunakan layanan peta, seperti google maps.

![Koordinat pertama](http://i.imgur.com/g714QQV.png)

Semua lokasi pada titik-titik tersebut adalah:
```
* Nakanocho, Kamigyo Ward, Kyoto, Japan
* Odesa, Odessa Oblast, Ukraine
* Dayton, OH 45402, United States
* European Side, Hoca Paşa, 34110 Fatih/İstanbul, Turkey
* Hazza' Bin Zayed the First St - Al Manhal - Abu Dhabi - United Arab Emirates
* 50480 Kuala Lumpur, Federal Territory of Kuala Lumpur, Malaysia
* Kirkos, Addis Ababa, Ethiopia
* Av Nueva Loja, Loja, Ecuador
* Martelaarsgracht 5, 1012 TN Amsterdam, Netherlands
* Sleepy Hollow, NY 10591, United States
* 1 Chadrick Cove, Kodiak, AK 99615, United States
* Faculty Of Engineering, Al Azaritah WA Ash Shatebi, Qism Bab Sharqi, Alexandria Governorate, Egypt
``` 

Ternyata (dan untungnya), tidak semua lokasi merujuk pada suatu tempat secara spesifik. Perlu diingat bahwa terdapat **_** setelah tempat keenam. Jika kita memulai dengan nama negara dari masing masing tempat, kita akan mendapatkan JUSTUM_EENUUE, yang ternyata bukanlah flagnya. Maka, kita beralih ke nama kota yang akan memberikan kita KODIAK_ALASKA yang ternyata adalah flagnya.

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{KODIAK_ALASKA}</code>

</details>
...

## 2. Tapping (200)

### Soal:
Theres tapping coming in from the wires. What's it saying nc 2019shell1.picoctf.com 49914.
### Pembahasan:
Pada soal ini diberikan sebuah kode morse yang dapat langsung di*decode*. Kode morse merupakan encoding untuk huruf latin yang terdiri dari titik dan garis. Anda dapat menggunakan petunjuk berikut untuk mendapatkan flagnya.

![Morse](https://upload.wikimedia.org/wikipedia/commons/b/b5/International_Morse_Code.svg)

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>PICOCTF{M0RS3C0D31SFUN903140448}</code>

</details>
...

## 3. la cifra de (200)

### Soal:
I found this cipher in an old book. Can you figure out what it says? Connect with nc 2019shell1.picoctf.com 61559.
### Pembahasan:
Di challenge ini kita diberikan beberapa paragraf text yang tampaknya diencode dengan shifting encryption. Pertama-tama saya mencoba melakukan dekripsi menggunakan cypher caesar secara bruteforce. Ternyata, teks ini tidak diencripsi menggunakan cipher caesar, maka dari itu, kita berlanjut ke cipher vigenere. Pertama-tama kita melakukan cryptoanalisis (Kasiski's test) untuk mencari panjang *key* yang paling mungkin. Janggalnya, hasilnya mengatakan kemungiknan terbesar key sepanjang 2 huruf, yang merupakan hal yang tidak lazim. Ternyata, benar saja, tidak ada hasil yang dicari.

Setelah bersakit-sakit kepala, akhirnya saya mencoba melakukan cryptoanalisis pada paragraf pertama saya. Hasilnya adalah key sepanjang 4 karakter merupakan yang paling mungkin.

![Hasil cryptoanalisys](http://i.imgur.com/aMUkRwj.png)

Selanjutnya kita dapat langsung melakukan dekripsi dengan jumlah huruf yang diketahui. Hasilnya adalah ternyata teks itu dienkripsi dengan *key* "flag". Tipikal. Akan tetapi, jika kita mencoba untuk melakukan dekripsi pada keseluruhan teks menggunakan key "flag", hasilnya tidak konsisten.

![Hasil decrypt](http://i.imgur.com/ROmTv8C.png)

Dapat dilihat bahwa key "flag" dapat digunakan sampai pertengahan kata yang seharusnya mengatakan "Vigenere", tetapi tertulis "Vigenzlp". Dapat ditafsir bahwa key yang digunakan diubah pada pertengahan itu. Ternyata *key*-nya diubah menjadi "gfla".

![Perubahan key](http://i.imgur.com/dNJYcur.png)

Dapat disimpulkan bahwa key untuk seksi berikutnya adalah "agfl", dan "lagf" untuk berikutnya lagi. Setelah itu dapat dilihat hasil dekripsi secara total dari teks tersebut.

>It is interesting how in history people often receive credit for things they did not create

>During the course of history, the Vigenère Cipher has been reinvented many times

>It was falsely attributed to Blaise de Vigenère as it was originally described in 1553 by Giovan Battista Bellaso in his book La cifra del. Sig. Giovan Battista Bellaso

>For the implementation of this cipher a table is formed by sliding the lower half of an ordinary alphabet for an apparently random number of places with respect to the upper halfpicoCTF{b311a50_0r_v1gn3r3_c1ph3rb6cdf651}

>The first well-documented description of a polyalphabetic cipher however, was made around 1467 by Leon Battista Alberti.

>The Vigenère Cipher is therefore sometimes called the Alberti Disc or Alberti Cipher.

>In 1508, Johannes Trithemius invented the so-called tabula recta (a matrix of shifted alphabets) that would later be a critical component of the Vigenère Cipher.

>Bellaso’s second booklet appeared in 1555 as a continuation of the first. The lower halves of the alphabets are now shifted regularly, but the alphabets and the index letters are mixed by means of a mnemonic key phrase, which can be different with each correspondent.

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{b311a50_0r_v1gn3r3_c1ph3rb6cdf651}</code>

</details>
...
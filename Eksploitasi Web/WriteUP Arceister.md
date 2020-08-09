# Eksploitasi Web

## Penulis: [Arceister](https://github.com/Arceister)
## Daftar Isi:

| Exploitasi Web |
| ------------- |
| [Insp3ct0r](#1.-insp3ct0r)|
| [dont-use-client-side](#2.-dont-use-client-side)|
| [logon]()|
| [where are the robots]()|
| [Client-side-again]()|
| [Open-to-admins]()|
| [picobrowser]()|

---
## 1. Insp3ct0r (50)

### Soal:

Kishor Balan tipped us off that the following code may need inspection: `https://2019shell1.picoctf.com/problem/61676/` ([link](https://2019shell1.picoctf.com/problem/61676/)) or http://2019shell1.picoctf.com:61676
    
### Pembahasan:

Sesuai namanya inspector, ini sudah menunjukkan bahwa kita disuruh untuk meng-*inspect* web tersebut. Coba kita *inspect* dulu webnya:
<br>

![HTML Page Source](https://lh3.googleusercontent.com/YCzcplTi4Xvts4OeCy1el5T5ylyEMacFqqlRL1ywFigDU8MTzxC4XRMIum60NyqHvh49vU__EHBYT_iFavA5TelIuS4Q4HljzPBQmaT31x8EwQI9kGIBqVjBSKeqFzSEY8tIYF8N2w=w2400)
<sub>*ini sebenernya view page source, sih*</sub>
<br>

Oke, dari source HTML web ini, kita dapet 1 bagian Flag dari 3 bagian yaitu `picoCTF{tru3_d3`

*"Terus 2nya lagi gimana?"*<br>
Inget aja kalo Frontend dasar itu terdiri dari 3 Unsur, yaitu **HTML, CSS, dan JS.**<br> 
<br>Oke kita coba *inspect* CSS dan JSnya:
<br>

![CSS Page Source](https://lh3.googleusercontent.com/pw/ACtC-3eofJ3wwlrkv_yGnzQbc7uU5ZMZhDSsIwQA-OS2iU98804VVnAgiX38EJ2Y46pBRcwttbRGUMvUdcZhMvWKc--wz4IcENC0TWZo6wXufdFtkwsaIhc4d2uYjC-8rYPkGrmQwwTL8Z1cMB6qbH-8dXXT=w1128-h634-no?authuser=0)
<sub>*ini source CSSnya*</sub>

![JS Page Source](https://lh3.googleusercontent.com/pw/ACtC-3dz6eUEPibWSDGp9Iv_LD02eTuCdRP-U4dsoKzKcMAEbsVoG0Zvw11_suBBWUOIJu6Kl2suVy3RA2Bve5EOI31K8i1wwBAuXqjJ2dmOoRDLOmb_p6eyDRS-IuzgorjDeV0TRkLy8TX3c7slh2Q7kr7L=w1128-h634-no?authuser=0)
<sub>*ini source JSnya*</sub><br>

Dari 2 source tersebut maka flag bagian kedua dan ketiga sudah ditemukan, yaitu `t3ct1ve_0r_ju5t` dan `_lucky?1638dbe7}`.

<details><summary>Tekan untuk melihat flag</summary>

  picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?1638dbe7}

</details>


## 2. dont-use-client-side (100)

### Soal:

Can you break into this super secure portal? https://2019shell1.picoctf.com/problem/37893/ ([link](https://2019shell1.picoctf.com/problem/37893/)) or http://2019shell1.picoctf.com:37893

### Pembahasan:

Kita dikasih lagi sebuah web, kali ini web tersebut menyuruh kita memasukkan password untuk mendapat flagnya.<br>

![Page](https://lh3.googleusercontent.com/pw/ACtC-3cIYKQKzsXf8e8XtjgW4ukGewrxlpw1AcH4lFgCD0bbaCbwanKbDT1Qlb2yD5uorvd6IwEineCg23BHpfMK2yTIkFph5mbVaDozikXS7kR-_HSjAVT_d7X5vTeNbr2Srjmc_we3tB037n4L1Ts_gzAb=w1128-h634-no?authuser=0)

*Eits tunggu dulu,* ada sesuatu yang *mengganjal* disini. Apa itu? ya **judul challengenya**.

Oke, langsung aja kita *view source page*, dan hasilnya

![PageSource](https://lh3.googleusercontent.com/pw/ACtC-3d4s5v02oir2znQ85TRYgn2bjjIKauA5ccdw7P0nQjaeobJtE1lZdw3-G88IeAzPgMfI4ZCoODQB13NJGIpIiE1EuRifwt9B21-QNKqhzMXmr-cCRjGsxtY8ixIKa7-OeF2GsB1FG27-7xBK-HP7ZTm=w1128-h634-no?authuser=0)

*Well*, kita mendapatkan flagnya berbentuk **Javascript**. Jika split dirubah menjadi 4, dan diurutkan menurut substring maka kita akan menemukan flagnya:
```
checkpass.substring(0, 4) == 'pico')
checkpass.substring(4, 8) == 'CTF{')
checkpass.substring(8, 12) == 'no_c') 
checkpass.substring(12, 16) == 'lien')
checkpass.substring(16, 20) == 'ts_p')
checkpass.substring(20, 24) == 'lz_9')
checkpass.substring(24, 28) == '0ff3')
checkpass.substring(28, 32) == '4}')
```
<sub>*ini udah diurutin sama dihilangin ifnya*</sub>

Sekarang kita coba memasukkan flag yang sudah kita dapatkan sebagai password di web tersebut.

![PassVerified](https://lh3.googleusercontent.com/pw/ACtC-3cvLaJtKRbZYojfbHnAOpbXFuDeZ9qJI1qlJR8wlABWS7l2Xujw__cxw-EtIDj0xiXnv3TjcJwYBh8vEQVwpdX9IHzUZaU9nkdGww_Tg9o1NBdTtnUf3FaI2mE3g6m155tobanXfSuxn4qYJNGxMq2C=w1128-h634-no?authuser=0)

*Tadaa!* Verifikasi sukses. Intinya client side ini hanya untuk memvalidasi flag yang kita dapatkan. **Cara dapet flagnya ya jangan liat client side**, sesuai petunjuk soal.

![pepelaugh](https://i.kym-cdn.com/photos/images/original/001/460/439/32f.jpg)

<details>
<summary>Tekan untuk melihat flag</summary>

  picoCTF{no_clients_plz_90ff34}

</details>

## 
# Eksploitasi Web

## Penulis: [Arceister]
## Daftar Isi:

| Exploitasi Web |
| ------------- |
| [Insp3ct0r](#1.-insp3ct0r)|
| [dont-use-client-side]()|
| [logon]()|
| [where are the robots]()|
| [Client-side-again]()|
| [Open-to-admins]()|
| [picobrowser]()|

---
## 1. Insp3ct0r

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
``` 
picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?1638dbe7}
```
</details>


## 2. dont-use-client-side

### Soal:

### Pembahasan:

## 
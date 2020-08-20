# Eksploitasi Web

## Penulis: [vnwrywn](https://github.com/vnwrywn)
## Daftar Isi:

| Exploitasi Web |
| ------------- |
| [Insp3ct0r]()|
| [dont-use-client-side]()|
| [logon](#1-logon-100)|
| [where are the robots]()|
| [Client-side-again]()|
| [Open-to-admins]()|
| [picobrowser]()|

---
## 1. logon (100)

### Soal:

The factory is hiding things from all of its users. Can you login as logon and find what they've been looking at? https://2019shell1.picoctf.com/problem/12284/ ([link](https://2019shell1.picoctf.com/problem/12284/)) or http://2019shell1.picoctf.com:12284

### Pembahasan:

Pada soal ini kita dihadapkan dengan sebuah antarmuka login.

![Page](http://i.imgur.com/1obuZ1k.png)

Janggalnya, kita dapat melakukan login dengan username dan password apapun. Jika kita melakukan login, kita akan melihat text "No flag for you".

![No flag](http://i.imgur.com/HyYuXF5.png)

Jika kita lihat menggunakan inspector, kita tidak akan menemukan hal yang janggal.

![Inspect element](https://i.imgur.com/s9hIt3R.png)

Maka dari itu, kita harus memeriksa hal yang berkaitan erat dengan kredensial login, yaitu cookies.

![Cookie](https://i.imgur.com/D4xqiMq.png)

Dapat dilihat bahwa terdapat cookie admin yang bernilai False. Kita dapat mengubah nilai cookie tersebut menjadi True dan menyimpannya. Setelah itu, kita hanya perlu melakukan reload pada laman flag dan flag akan ditampilkan.

![Flag](http://i.imgur.com/jd9lihB.png)

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{th3_c0nsp1r4cy_l1v3s_6f2c20e9}</code>

</details>
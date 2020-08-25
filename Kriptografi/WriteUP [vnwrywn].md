# Kriptografi

## Penulis: [vnwrywn]
## Daftar Isi:

| Kriptografi           |
| -------------         |
| [The Numbers](#1-The-Numbers-50)|
| [Caesar](#2-Caesar-100)|
| [Flags](#3-Flags-200)|
| [Mr-Worldwide](#4-Mr-Worldwide-200)|
| [Tapping](#5-Tapping-200)|
| [la cifra de](#6-la-cifra-de-200)|
| [rsa-pop-quiz](#7-rsa-pop-quiz-300)|
| [waves over lambda](#8-waves-over-lambda-300)|

---
## 1. The Numbers (50)

### Soal:
The [numbers](https://2019shell1.picoctf.com/static/eb3589c566dd3f809908053460acb817/the_numbers.png)... what do they mean?
...

### Pembahasan:
Pada soal ini kita diberikan gambar sebagai berikut

![Soal](https://imgur.com/T47IWfE.png)

Dapat dilihat bahwa setiap bilangan dipisahkan dengan sebuah spasi, dan bilangan tersebut tidak ada yang melebihi 26. Maka dari itu *ciphertext* ini kemungkinan besar dienkripsi menggunakan *letter number* (A1Z26) *cipher*. ciphertext ini dapat dipecahkan dengan mengubah setiap angka menjadi huruf pada indeks tersebut (contoh: 1=A dan 26=Z). Atau anda dapat menggunakan [peralatan daring](https://www.dcode.fr/letter-number-cipher) untuk memecahkannya.

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>PICOCTF{THENUMBERSMASON}</code>

</details>

## 2. Caesar (100)

### Soal:
Decrypt this [message](https://2019shell1.picoctf.com/static/1f33970830e651254c964ee5d04f0e85/ciphertext). You can find the ciphertext in /problems/caesar_6_238b8f4604d91ecb59cda5b4f0e66fc8 on the shell server.
...

### Pembahasan:
Pada challenge ini kita diberikan seutas huruf yang sudah berada dalam format flag yang benar. Akan tetapi, (tentu saja) itu bukanlah flagnya. Berdasarkan judul dari challenge ini, dapan diterka bahwa flag ini dienkripsi menggunakan *caesar cipher*. *Caesar cipher* merupakan *cipher* substitusi monoalfabetik yang dilakukan dengan "menggeser" urutan huruf. Flag dari challenge ini dapat didapatkan dengan melakukan serangan *bruteforce* pada teks yang berada dalam kurung kurawal. Salah satu cara yang paling mudah untuk melakukan ini adalah dengan menggunakan [peralatan daring](https://www.dcode.fr/caesar-cipher).

![Hasil](http://i.imgur.com/X9DwAEj.png)

Dapat dilihat bahwa melakukan pergeseran sebanyak 15 akan mengasilkan flag yang dicari.

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{crossingtherubiconojovpqjs}</code>

</details>

## 3. Flags (200)

### Soal:
What do the [flags](https://2019shell1.picoctf.com/static/ae23b7df04365ab0213f0158c5b5d694/flag.png) mean?
...

### Pembahasan:
Pada challenge ini kita diberikan serangkaian bendera yang beragam. Bendera ini ternyata merupakan [*International Code of Signals*](https://en.wikipedia.org/wiki/International_Code_of_Signals). Anda dapat mendapatkan flagnya dengan menggunakan petunjuk berikut.

![Petunjuk](https://upload.wikimedia.org/wikipedia/commons/f/fa/ICS-flags.png)

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>PICOCTF{F1AG5AND5TUFF}</code>

</details>

## 4. Mr-Worldwide (200)

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

## 5. Tapping (200)

### Soal:
Theres tapping coming in from the wires. What's it saying nc 2019shell1.picoctf.com 49914.
### Pembahasan:
Pada soal ini diberikan sebuah kode morse yang dapat langsung di*decode*. Kode morse merupakan encoding untuk huruf latin yang terdiri dari titik dan garis. Anda dapat menggunakan petunjuk berikut untuk mendapatkan flagnya.

![Morse](https://upload.wikimedia.org/wikipedia/commons/b/b5/International_Morse_Code.svg)

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>PICOCTF{M0RS3C0D31SFUN903140448}</code>

</details>

## 6. la cifra de (200)

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
>
>During the course of history, the Vigenère Cipher has been reinvented many times
>
>It was falsely attributed to Blaise de Vigenère as it was originally described in 1553 by Giovan Battista Bellaso in his book La cifra del. Sig. Giovan Battista Bellaso
>
>For the implementation of this cipher a table is formed by sliding the lower half of an ordinary alphabet for an apparently random number of places with respect to the upper halfpicoCTF{b311a50_0r_v1gn3r3_c1ph3rb6cdf651}
>
>The first well-documented description of a polyalphabetic cipher however, was made around 1467 by Leon Battista Alberti.
>
>The Vigenère Cipher is therefore sometimes called the Alberti Disc or Alberti Cipher.
>
>In 1508, Johannes Trithemius invented the so-called tabula recta (a matrix of shifted alphabets) that would later be a critical component of the Vigenère Cipher.
>
>Bellaso’s second booklet appeared in 1555 as a continuation of the first. The lower halves of the alphabets are now shifted regularly, but the alphabets and the index letters are mixed by means of a mnemonic key phrase, which can be different with each correspondent.

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{b311a50_0r_v1gn3r3_c1ph3rb6cdf651}</code>

</details>

## 7. rsa-pop-quiz (300)

### Soal:
Class, take your seats! It's PRIME-time for a quiz... nc 2019shell1.picoctf.com 61751
### Pembahasan:
Pada challenge ini kita diberikan delapan soal mengenai kriptosistem RSA. Setiap soal diawali dengan pertanyaan apakah suatu variabel dapat dicari, dan kemudian, apabila memang dapat dicari, nilai dari variabel tersebut akan ditanyakan. Kita akan membahas soal soal tersebut satu-persatu.

>#### NEW PROBLEM ####
>q : 60413
>p : 76753
>##### PRODUCE THE FOLLOWING ####
>n
n dapat dicari jika p dan q adalah bilangan prima. Dikarenakan p dan q adalah bilangan prima, maka jawabannya adalah Y. Dengan mengalikan p dan q, n dapat ditemukan.

>#### NEW PROBLEM ####
>p : 54269
>n : 5051846941
>##### PRODUCE THE FOLLOWING ####
>q
Dikarenakan p*q = n, maka q = n/p. q dapat dicari.

>#### NEW PROBLEM ####
>e : 3
>n :  12738162802910546503821920886905393316386362759567480839428456525224226445173031635306683726182522494910808518920409019414034814409330094245825749680913204566832337704700165993198897029795786969124232138869784626202501366135975223827287812326250577148625360887698930625504334325804587329905617936581116392784684334664204309771430814449606147221349888320403451637882447709796221706470239625292297988766493746209684880843111138170600039888112404411310974758532603998608057008811836384597579147244737606088756299939654265086899096359070667266167754944587948695842171915048619846282873769413489072243477764350071787327913
>##### PRODUCE THE FOLLOWING ####
>q
>p
n merupakan hasil dari p*q. Akan tetapi, hal ini tidak menjadikan p dan q dapat ditemukan. Hal ini dikarenakan n merupakan sebuah bilangan yang sangat besar. Kecuali terdapat kelemahan pada p dan q (seperti nilai p atau q terlalu kecil), pencarian p akan membutuhkan waktu yang sangat lama.

>#### NEW PROBLEM ####
>q : 66347
>p : 12611
>##### PRODUCE THE FOLLOWING ####
>totient(n)
totient(n) dapat dicari dengan mengalikan (p-1) dan (q-1).

>#### NEW PROBLEM ####
>plaintext : 6357294171489311547190987615544575133581967886499484091352661406414044440475205342882841236357665973431462491355089413710392273380203038793241564304774271529108729717
>e : 3
>n : 29129463609326322559521123136222078780585451208149138547799121083622333250646678767769126248182207478527881025116332742616201890576280859777513414460842754045651093593251726785499360828237897586278068419875517543013545369871704159718105354690802726645710699029936754265654381929650494383622583174075805797766685192325859982797796060391271817578087472948205626257717479858369754502615173773514087437504532994142632207906501079835037052797306690891600559321673928943158514646572885986881016569647357891598545880304236145548059520898133142087545369179876065657214225826997676844000054327141666320553082128424707948750331
>##### PRODUCE THE FOLLOWING ####
>ciphertext
c dapat dicari dengan rumus berikut: m^e mod n

>#### NEW PROBLEM ####
>ciphertext : 107524013451079348539944510756143604203925717262185033799328445011792760545528944993719783392542163428637172323512252624567111110666168664743115203791510985709942366609626436995887781674651272233566303814979677507101168587739375699009734588985482369702634499544891509228440194615376339573685285125730286623323
>e : 3
>n : 27566996291508213932419371385141522859343226560050921196294761870500846140132385080994630946107675330189606021165260590147068785820203600882092467797813519434652632126061353583124063944373336654246386074125394368479677295167494332556053947231141336142392086767742035970752738056297057898704112912616565299451359791548536846025854378347423520104947907334451056339439706623069503088916316369813499705073573777577169392401411708920615574908593784282546154486446779246790294398198854547069593987224578333683144886242572837465834139561122101527973799583927411936200068176539747586449939559180772690007261562703222558103359
>##### PRODUCE THE FOLLOWING ####
>plaintext
m tidak dapat dicari tanpa mengetahui d.

>#### NEW PROBLEM ####
>q : 92092076805892533739724722602668675840671093008520241548191914215399824020372076186460768206814914423802230398410980218741906960527104568970225804374404612617736579286959865287226538692911376507934256844456333236362669879347073756238894784951597211105734179388300051579994253565459304743059533646753003894559
>p : 97846775312392801037224396977012615848433199640105786119757047098757998273009741128821931277074555731813289423891389911801250326299324018557072727051765547115514791337578758859803890173153277252326496062476389498019821358465433398338364421624871010292162533041884897182597065662521825095949253625730631876637
>e : 65537
>##### PRODUCE THE FOLLOWING ####
>d
d dapat dicari dengan mencari (1 + x totient(n))/e yang bernilai bulat, di mana x merupakan bilangan bulat sembarang.

>#### NEW PROBLEM ####
>p : 153143042272527868798412612417204434156935146874282990942386694020462861918068684561281763577034706600608387699148071015194725533394126069826857182428660427818277378724977554365910231524827258160904493774748749088477328204812171935987088715261127321911849092207070653272176072509933245978935455542420691737433
>ciphertext : 9276182891752530901219927412073143671948875482138883542938401204867776171605127572134036444953137790745003888189443976475578120144429490705784649507786686788217321344885844827647654512949354661973611664872783393501992112464825441330961457628758224011658785082995945612195073191601952238361315820373373606643521463466376095236371778984942891123936191796720097900593599447528583257806196551724676380135110693228330934418147759387990754368525068685861547977993085149359162754890674487823080750579601100854795031284533864826255207300350679553486505961837349042778851010569582458629638648589442067576234798724906377157351
>e : 65537
>n : 23952937352643527451379227516428377705004894508566304313177880191662177061878993798938496818120987817049538365206671401938265663712351239785237507341311858383628932183083145614696585411921662992078376103990806989257289472590902167457302888198293135333083734504191910953238278860923153746261500759411620299864395158783509535039259714359526738924736952759753503357614939203434092075676169179112452620687731670534906069845965633455748606649062394293289967059348143206600765820021392608270528856238306849191113241355842396325210132358046616312901337987464473799040762271876389031455051640937681745409057246190498795697239
>##### PRODUCE THE FOLLOWING ####
>plaintext
m dapat dicari dengan rumus berikut: c^d mod n. Dan d dapat dicari dengan mencari (1 + x totient(n))/e yang bernilai bulat, di mana x merupakan bilangan bulat sembarang.

Setelah menyelesaikan soal terakhir, adna akan diberitahubahwa jika anda mengubah plaintext terakhir menjadi hexadecimal lalu didecode menggunakan ASCII, flagnya dapat ditemukan.

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{wA8_th4t$_ill3aGal..o1828d357}</code>

</details>

## 8. waves over lambda (300)

### Soal:
We made alot of substitutions to encrypt this. Can you decrypt it? Connect with nc 2019shell1.picoctf.com 45185.
### Pembahasan:
Pada challenge ini kita mendapatkan sebuah teks yang tidak koheren. Berdasarkan deskripsi soal ini, Teks ini dienkripsi menggunakan substitusi, sebuah kriptosistem yang memiliki kelemahan fatal; dapat dideteksi menggunakan pencocokan rata-rata persebaran huruf pada keseluruhan kata yang ada pada kamus suatu bahasa. Untuk menghemat waktu, kita dapat menggunakan sebuah [*tool*](https://www.dcode.fr/monoalphabetic-substitution) daring untuk memecahkan enkripsinya.

![Hasil dekripsi](http://i.imgur.com/fiRl5oE.png)

<details>
<summary>Tekan untuk melihat flag</summary>

  <code>picoCTF{frequency_is_c_over_lambda_mupgpennod}</code>

</details>

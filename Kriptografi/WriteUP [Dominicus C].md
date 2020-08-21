# Kriptografi

## Penulis: [Dominicus C]
## Daftar Isi:

| Kriptografi           |
| -------------         |
| [The Numbers]()|
| [13]()|
| [Easy1]()|
| [Caesar]()|
| [Flags]()|

---
## 1. The Numbers ()

### Soal:
The numbers... what do they mean?
...

### Pembahasan:
Setiap huruf adalah angka dari 1-26, begitupun sebaliknya setiap angka adalah huruf dari A-Z
-Terjemahkan setiap angka menjadi huruf-
cipher : A1Z26
flag : PICOCTF{THENUMBERSMASON}
...

## 2. 13 ()

### Soal:
Cryptography can be easy, do you know what ROT13 is? cvpbPGS{abg_gbb_onq_bs_n_ceboyrz}
### Pembahasan:
ROT13 adalah sandi caesar dengan pergeseran 13/k=13
--Terjemahkan setiap huruf menjadi huruf yg telah digeser-
cipher : caesar
flag : picoCTF{not_too_bad_of_a_problem}
...

## 3. Easy1 ()

### Soal:
The one time pad can be cryptographically secure, but not when you know the key. Can you solve this? We've given you the encrypted flag, key, and a table to help UFJKXQZQUNB with the key of SOLVECRYPTO. Can you use this table to solve it?.
### Pembahasan:
dekripsi + kunci = enkripsi
kita dikasih enkripsi + kunci berarti nanti hasilnya dekripsi
flag + SOLVECRYPTO = UFJKXQZQUNB
cipher = one time pad
flag : picoCTF{CRYPTOISFUN}
...

## 4. caesar ()

### Soal:
Decrypt this message. You can find the ciphertext in /problems/caesar_4_33e5994add902b2321c8c38c8b962eff on the shell server.
### Pembahasan:
diketahui picoCTF{odaeeuzsftqdgnuoazxvymiumq} dengan jumlah 26 huruf
cek pergeseran tiap huruf hingga menemukan kata yg bermakna menggunakan caesar chiper (ternyata k=14)
cipher = caesar
flag = picoCTF{crossingtherubiconljmawiae}
...

## 5. Flags ()

### Soal:
What do the flags mean?
### Pembahasan:
diketahui berbagai bendera dengan 2 kurawal
hint : PICOCTF{}
flag = PICOCTF{F???????????FF}
googling -> cryptography flag -> military alphabet flag
cipher = Military Phonetic Alphabet & Signal Flags
flag = PICOCTF{F1AG5AND5TUFF}
...
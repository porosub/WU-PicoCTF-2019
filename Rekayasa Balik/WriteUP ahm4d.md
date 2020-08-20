# Rekayasa Balik

## Penulis: [ahm4ddm](https://github.com/ahm4ddm)
## Daftar Isi:

| Rekayasa Balik  |
| ------------- |
| [vault-door-training](#1-vault-door-training-50)|
| [asm1](#2-asm1-200)|
| [vault-door-4](#3-vault-door-4-250)|
| [asm3](#4-asm3-300)|
| [droids0](#5-droids0-300)|
| [vault-door-6](#6-vault-door-6-350)|


---
## 1. vault-door-training (50)

### Soal:
Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility. The source code for the training vault is here: [VaultDoorTraining.java](https://2019shell1.picoctf.com/static/56c37b7d53ba094dd5b05587ad27d3cf/VaultDoorTraining.java)
    
### Pembahasan:
Kita download dulu file [VaultDoorTraining.java](https://2019shell1.picoctf.com/static/56c37b7d53ba094dd5b05587ad27d3cf/VaultDoorTraining.java), setelah itu kita buka menggunakan text editor (saya menggunakan sublime text). 
```
	public boolean checkPassword(String password) {  
    	return password.equals("w4rm1ng_Up_w1tH_jAv4_e57d01a632a");  
    }
```
Flag terlihat jelas ada fungsi check password.
<details>
	<summary>Flagnya</summary>

	picoCTF{w4rm1ng_Up_w1tH_jAv4_e57d01a632a}

</details>  


## 2. asm1 (200)

### Soal:
What does asm1(0x53e) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2019shell1.picoctf.com/static/646a8167294d5c95b6446576264f24ab/test.S) located in the directory at /problems/asm1_4_431c7088e03c0028398793773ccf89d7.

### Pembahasan:
Kita lihat dulu source codenya. 
```
asm1:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	cmp    DWORD PTR [ebp+0x8],0x35d 	
	<+10>:	jg     0x512 <asm1+37> 			
	<+12>:	cmp    DWORD PTR [ebp+0x8],0x133
	<+19>:	jne    0x50a <asm1+29>
	<+21>:	mov    eax,DWORD PTR [ebp+0x8]
	<+24>:	add    eax,0xb
	<+27>:	jmp    0x529 <asm1+60>
	<+29>:	mov    eax,DWORD PTR [ebp+0x8]
	<+32>:	sub    eax,0xb
	<+35>:	jmp    0x529 <asm1+60>
	<+37>:	cmp    DWORD PTR [ebp+0x8],0x53e	
	<+44>:	jne    0x523 <asm1+54>
	<+46>:	mov    eax,DWORD PTR [ebp+0x8]
	<+49>:	sub    eax,0xb
	<+52>:	jmp    0x529 <asm1+60>
	<+54>:	mov    eax,DWORD PTR [ebp+0x8]
	<+57>:	add    eax,0xb
	<+60>:	pop    ebp
	<+61>:	ret    
```
setelah dianalisa flag meminta return dari *0x53e*.  
*0x53e* dibandingkan dengan *0x35d* karena lebih besar jadi masuk ke <code><+10>:	jg     0x512 <asm1+37></code> lalu dibandingkan lagi <code><+37>:	cmp    DWORD PTR [ebp+0x8],0x53e</code>, karena sama lalu dilakukan <code>sub</code> sebanyak *0xb* dan itu adalah flagnya.
<details>
	<summary>Flagnya</summary>

	picoCTF{0x533}

</details>

## 3. vault-door-4 (250)

### Soal:
This vault uses ASCII encoding for the password. The source code for this vault is here: [VaultDoor4.java](https://2019shell1.picoctf.com/static/b8a4ba51f30b373f6df7682709e43c8d/VaultDoor4.java)

### Pembahasan:
Kita lihat dulu source codenya.
ada yang menarik yaitu fungsi <code>checkPassword</code> dan hint dari soal adalah harus mengetahui perbedaan bilangan octal, decimal, dan hexadecimal. bisa diselesaikan dengan cara manual yaitu konversi semua bilangan itu ke ascii (bisa dilakukan dengan tools atau manual).

cara lain dengan penyelesaian :
```
    public boolean checkPassword(String password) {
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 070 , 060 ,
            'f' , '8' , 'e' , '1' , 'e' , '0' , '4' , '7' ,
        };
        passBytes=myBytes;
        for (int i=0; i<32; i++) {
            if (passBytes[i] != myBytes[i]) {
                return false;
            }
            System.out.print((char)passBytes[i]);
        }
        return true;
    }
```    
Kita harus menyamakan *passByte* dengan *myBytes* (kalau tidak maka acces denied). lalu menampilkan setelah perulangan selesai, maka akan menampilkan flag.
<details>
    <summary>Flagnya</summary>

    picoCTF{jU5t_4_bUnCh_0f_bYt3s_80f8e1e047}

</details>  

## 4. asm3 (300)

### Soal:
What does asm3(0xd46c9935,0xdfe28722,0xb335450f) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2019shell1.picoctf.com/static/7fa30288613be44a6a39c1191ccf1971/test.S) located in the directory at /problems/asm3_2_376e88472c6a9317470a12cc31d506a4.

### Pembahasan:
kita lihat dulu source code.
setelah dianalisa dan mencari referensi dari internet, ternyata source code kita ubah agar bisa dicompile
<code>test.S</code>
```
.intel_syntax noprefix
.global asm3
asm3:
        push   ebp
        mov    ebp,esp
        xor    eax,eax
        mov    ah,BYTE PTR [ebp+0xa]
        shl    ax,0x10
        sub    al,BYTE PTR [ebp+0xf]
        add    ah,BYTE PTR [ebp+0xe]
        xor    ax,WORD PTR [ebp+0x10]
        nop
        pop    ebp
        ret    

```
lalu buat source code menggunakan bahasa C untuk menampilkan flag (masukkan parameter sesuai pada soal)
<code>soltest.c</code>
```
 #include <stdio.h>
 int asm3(int, int, int);
 int main(int argc, char* argv[]){
    printf("flag: 0x%x",asm3(0xd46c9935,0xdfe28722,0xb335450f));
    return 0;
 }
```
lalu compile dengan gcc dengan perintah:
```
gcc -masm=intel -m32 -c test.S -o test.o
gcc -m32 test.o soltest.o -o test
gcc -m32 -c soltest.c -o soltest.o
gcc -m32 test.o soltest.o -o test
./test
```
<details>
    <summary>Flagnya</summary>

    picoCTF{0xa72e}

</details>  

## 5. droids0 (300)
### Soal:
Where do droid logs go. Check out this file. You can also find the file in /problems/droids0_0_205f7b4a3b23490adffddfcfc45a2ca3.

### Pembahasan:
hint dari soal itu adalah dengan menjalankan dengan emulator android.
kita download dulu soalnya untuk dianalisa (saya menggunakan scp) dengan perintah 
```
$scp ahm4d@2019shell1.picoctf.com:/problems/droids0_0_205f7b4a3b23490adffddfcfc
5a2ca3/zero.apk /home/ahm4d/
```
setelah itu kita coba jalankan dengan emulator terserah, saya memakai android studio, setelah itu pilih opsi **Profile or debug APK** lalu klik run. hmmm kita klik flag tidak ada apa-apa.
coba kita lihat log ternyata ada flag.
intinya button flag tidak langsung menampilkan flag dilayar. tapi kita harus lihat dibagian lognya.
<details>
    <summary>Flagnya</summary>

    picoCTF{a.moose.once.bit.my.sister}

</details> 

## 6. vault-door-6 (350)

### Soal:
This vault uses an XOR encryption scheme. The source code for this vault is here: [VaultDoor6.java](https://2019shell1.picoctf.com/static/baceedcb57993355ba6eac807ca041b0/VaultDoor6.java)

### Pembahasan:
kita lihat dulu source codenya.
da yang menarik yaitu fungsi <code>checkPassword</code>. pembahasan soal ini adalah kita harus melakukan xor *0x55* agar menampilkan flag. saya melakukan penyelesaian di python.
berikut penyelesaian:
```
flag = ''
flagRaw = [0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x34, 0x30, 0x31, 0x30, 0x36, 0x30, 0x31]
for i in flagRaw:
  flag += chr(i ^ 0x55)
print("picoCTF{" + flag +"}")
```
jalankan, lalu didapatkan flagnya.
<details>
    <summary>Flagnya</summary>

    picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_aedeced}

</details>
# Rekayasa Balik

## Penulis: [ahm4ddm]
## Daftar Isi:

| Rekayasa Balik  |
| ------------- |
| [vault-door-training](#1-vault-door-training)|
| [vault-door-1](#2-vault-door-1)|
| [asm1](#3-asm1)|
| [vault-door-4]()|
| [asm3]()|
| [vault-door-6]()|
| [Time’s Up]()|

---
## 1. vault-door-training

### Soal:
Your mission is to enter Dr. Evil's laboratory and retrieve the blueprints for his Doomsday Project. The laboratory is protected by a series of locked vault doors. Each door is controlled by a computer and requires a password to open. Unfortunately, our undercover agents have not been able to obtain the secret passwords for the vault doors, but one of our junior agents obtained the source code for each vault's computer! You will need to read the source code for each level to figure out what the password is for that vault door. As a warmup, we have created a replica vault in our training facility. The source code for the training vault is here: [VaultDoorTraining.java](https://2019shell1.picoctf.com/static/56c37b7d53ba094dd5b05587ad27d3cf/VaultDoorTraining.java)
    
### Pembahasan:
Kita download dulu file [VaultDoorTraining.java](https://2019shell1.picoctf.com/static/56c37b7d53ba094dd5b05587ad27d3cf/VaultDoorTraining.java), setelah itu kita buka menggunakan text editor (saya menggunakan sublime text).  
Flag terlihat jelas ada fungsi check password.
<details>
	<summary>Flagnya</summary>

	picoCTF{w4rm1ng_Up_w1tH_jAv4_e57d01a632a}

</details>  

## 2. vault-door-1

### Soal:
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://2019shell1.picoctf.com/static/955f5aeef623b09378306dd6c1f88f96/VaultDoor1.java)

### Pembahasan:
Kita download dulu file [VaultDoor1.java](https://2019shell1.picoctf.com/static/955f5aeef623b09378306dd6c1f88f96/VaultDoor1.java), setelah itu kita buka menggunakan text editor(saya menggunakan sublime text).  
Flag terlihat jelas tapi kita disuruh mengurutkan terlebih dahulu.
<details>
	<summary>Flagnya</summary>

	picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_51e7fd}

</details>

## 3 asm1

### Soal:
What does asm1(0x53e) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://2019shell1.picoctf.com/static/646a8167294d5c95b6446576264f24ab/test.S) located in the directory at /problems/asm1_4_431c7088e03c0028398793773ccf89d7.

### Pembahasan:
Kita lihat dulu source codenya. setelah dianalisa flag meminta return dari *0x53e*.  
*0x53e* dibandingkan dengan *0x35d* karena lebih besar jadi masuk ke <code><+10>:	jg     0x512 <asm1+37></code> lalu dibandingkan lagi <code><+37>:	cmp    DWORD PTR [ebp+0x8],0x53e</code>, karena sama lalu dilakukan <code>sub</code> sebanyak *0xb* dan itu adalah flagnya.
<details>
	<summary>Flagnya</summary>

	0x533

</details>

## 4. vault-door-3

### Soal
This vault uses for-loops and byte arrays. The source code for this vault is here: [VaultDoor3.java](https://2019shell1.picoctf.com/static/effb51263df645722a6eb4e1e82c69da/VaultDoor3.java)

### Pembahasan:
Kita download dulu file [VaultDoor3.java](https://2019shell1.picoctf.com/static/effb51263df645722a6eb4e1e82c69da/VaultDoor3.java), setelah itu kita buka menggunakan text editor.  
kita fokus ke fungsi <code>checkPassword</code>, lalu mengurutkan secara manual.  
cara lain yaitu dengan mengakalinya dengan comment *password.length*, lalu kita isi *password* dengan isi string *s*, dan menampilkan setelah perulangan selesai menggunakan keyword *new String(buffer)* (karena ada pembuatan objek baru dari buffer yang mana itu nanti akan menampilkan flag yang valid).
<details>
	<summary>Flagnya</summary>

	picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_c33f38}

</details>



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

## 2. vault-door-1 (100)

### Soal:
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: [VaultDoor1.java](https://2019shell1.picoctf.com/static/955f5aeef623b09378306dd6c1f88f96/VaultDoor1.java)

### Pembahasan:
Kita download dulu file [VaultDoor1.java](https://2019shell1.picoctf.com/static/955f5aeef623b09378306dd6c1f88f96/VaultDoor1.java), setelah itu kita buka menggunakan text editor(saya menggunakan sublime text).
```
	public boolean checkPassword(String password) {
		return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == '7' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == '1' &&
               password.charAt(30) == 'f' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == 'e' &&
               password.charAt(26) == '5' &&
               password.charAt(31) == 'd';
```
Flag terlihat jelas tapi kita disuruh mengurutkan terlebih dahulu.
<details>
	<summary>Flagnya</summary>

	picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_51e7fd}

</details>

## 3. asm1 (200)

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

	0x533

</details>

## 4. vault-door-3 (200)

### Soal
This vault uses for-loops and byte arrays. The source code for this vault is here: [VaultDoor3.java](https://2019shell1.picoctf.com/static/effb51263df645722a6eb4e1e82c69da/VaultDoor3.java)

### Pembahasan:
Kita download dulu file [VaultDoor3.java](https://2019shell1.picoctf.com/static/effb51263df645722a6eb4e1e82c69da/VaultDoor3.java), setelah itu kita buka menggunakan text editor.  
kita fokus ke fungsi <code>checkPassword</code>, lalu mengurutkan secara manual.  
cara lain yaitu dengan mengakalinya dengan comment *password.length*, lalu kita isi *password* dengan isi string *s*, dan menampilkan setelah perulangan selesai menggunakan keyword *new String(buffer)* (karena ada pembuatan objek baru dari buffer yang mana itu nanti akan menampilkan flag yang valid). 
```
public boolean checkPassword(String password) {
       /* if (password.length() != 32) {
            return false;
        */}
        password = "jU5t_a_sna_3lpm13g34c_u_4_m3rf48"
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        System.out.println(new String(buffer));
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm13g34c_u_4_m3rf48");
    }
```
<details>
	<summary>Flagnya</summary>

	picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_c33f38}

</details>
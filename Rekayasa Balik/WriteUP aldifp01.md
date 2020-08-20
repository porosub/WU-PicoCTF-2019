# Rekayasa Balik

## Penulis: Aldi Fianda Putra
## Daftar Isi:

| Rekayasa Balik  |
| ------------- |
| [vault-door-1](#1-vault-door-1-100)|
| [vault-door-3](#2-vault-door-3-200)|
| [asm2](#5-asm2-250)|
| [vault-door-5](#3-vault-door-5-300)|
| [Need For Speed](#6-need-for-speed-400)|
| [vault-door-7](#4-vault-door-7-400)|
| [Time’s Up](#7-times-up-400)|

---
## 1. vault door 1 (100)

### Soal:
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: VaultDoor1.java

### Pembahasan:
Pertama, file VaultDoor1.java dibuka dengan IDE ataupun text editor dan diperoleh kode berikut

```
import java.util.*;

class VaultDoor1 {
    public static void main(String args[]) {
        VaultDoor1 vaultDoor = new VaultDoor1();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
	String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
	}
    }

    // I came up with a more secure way to check the password without putting
    // the password itself in the source code. I think this is going to be
    // UNHACKABLE!! I hope Dr. Evil agrees...
    //
    // -Minion #8728
    public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == '3' &&
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
               password.charAt(27) == 'd' &&
               password.charAt(30) == '8' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == '0' &&
               password.charAt(26) == '9' &&
               password.charAt(31) == 'f';
    }
}
```

maka diperoleh kondisi checkPassword, sehingga tinggal mengurutkan 32 char dari 0 sampai 31 sehingga diperoleh passwordnya sebagai berikut
d35cr4mbl3_tH3_cH4r4cT3r5_9d038f

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_9d038f}
  ```
</details>

## 2. vault door 3 (200)

### Soal:
This vault uses for-loops and byte arrays. The source code for this vault is here: VaultDoor3.java

### Pembahasan:
diperoleh file java dengan kode berikut

```
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
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
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm17ga45_u_4_mbrf4c");
    }
}
```
apabila diperhatikan, berdasarkan kodenya 8 huruf pertama sudah berurutan sedangkan sisanya diacak, sehingga kita tinggal membalikan kode untuk mengacaknya kembali dengan kode berikut
dengan mengisi angka yang dikosongkan pada looping sebagai berikut dengan membuat file java baru
```
public class vaultdoor3Solution {
    public static void main(String[] args){
        String password = "jU5t_a_sna_3lpm17ga45_u_4_mbrf4c";
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (i=8; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (i=16; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String yangbenarnya = new String(buffer);
        System.out.println(yangbenarnya);
    }
}
```
sehingga diperoleh hasil output sebagai berikut
jU5t_a_s1mpl3_an4gr4m_4_u_5baf7c

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_5baf7c}
  ```
</details>

## 3. vault door 5 (300)

### Soal:
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding! The source code for this vault is here: VaultDoor5.java

### Pembahasan:
diperoleh file java berikut
```
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTMxJTMxJTM3JTM3JTY2JTM3JTM4JTMz";
        return base64Encoded.equals(expected);
    }
}

```
maka diperoleh hint bahwa passwordnya disembunyikan dalam format base64 sehingga kita decode terlebih dahulu sehingga diperoleh
%63%30%6e%76%33%72%74%31%6e%67%5f
%66%72%30%6d%5f%62%61%35%65%5f%36
%34%5f%31%31%37%37%66%37%38%33

karena formatnya terlihat seperti format pada url, maka kalimat tersebut di terjemahkan dengan URL decode sehingga diperoleh
c0nv3rt1ng_fr0m_ba5e_64_1177f783

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{c0nv3rt1ng_fr0m_ba5e_64_1177f783}
  ```
</details>

## 4. vault door 7 (400)

### Soal :
This vault uses bit shifts to convert a password string into an array of integers. Hurry, agent, we are running out of time to stop Dr. Evil's nefarious plans! The source code for this vault is here: VaultDoor7.java

### Pembahasan :
Diperoleh file java berikut
```
import java.util.*;
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.security.*;

class VaultDoor7 {
    public static void main(String args[]) {
        VaultDoor7 vaultDoor = new VaultDoor7();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Each character can be represented as a byte value using its
    // ASCII encoding. Each byte contains 8 bits, and an int contains
    // 32 bits, so we can "pack" 4 bytes into a single int. Here's an
    // example: if the hex string is "01ab", then those can be
    // represented as the bytes {0x30, 0x31, 0x61, 0x62}. When those
    // bytes are represented as binary, they are:
    //
    // 0x30: 00110000
    // 0x31: 00110001
    // 0x61: 01100001
    // 0x62: 01100010
    //
    // If we put those 4 binary numbers end to end, we end up with 32
    // bits that can be interpreted as an int.
    //
    // 00110000001100010110000101100010 -> 808542562
    //
    // Since 4 chars can be represented as 1 int, the 32 character password can
    // be represented as an array of 8 ints.
    //
    // - Minion #7816
    public int[] passwordToIntArray(String hex) {
        int[] x = new int[8];
        byte[] hexBytes = hex.getBytes();
        for (int i=0; i<8; i++) {
            x[i] = hexBytes[i*4]   << 24
                 | hexBytes[i*4+1] << 16
                 | hexBytes[i*4+2] << 8
                 | hexBytes[i*4+3];
        }
        return x;
    }

    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        int[] x = passwordToIntArray(password);
        return x[0] == 1096770097
            && x[1] == 1952395366
            && x[2] == 1600270708
            && x[3] == 1601398833
            && x[4] == 1716808014
            && x[5] == 1734293602
            && x[6] == 1701067056
            && x[7] == 892756537;
    }
}
```
Program diatas dari komentar yang disalipkan kita mengetahui program ini berguna untuk mengubah format ASCII menjadi byte lalu dari byte menjadi hexadecimal yang dimuat dalam string 4 bit.
Maka, caranya adalah menkonvert array x tersebut menjadi biner sehingga diperoleh

```
10000010101111101100010001100011110100010111110011000001100110101111101100010001100010111010010111110111001101101000001100011100110010101000110100101001110110011101011111001110000110001011001010110010000111001001100000110101001101100110001000111001
```
apabila langsung dikonvert maka diperoleh string berikut
```
¾ÄcÑ|Áû¥÷6Ê)Ù×Î²²56b9

atau apabila terkendala berikut dalam bentuk yang bisa di ketik pada terminal 

\xC2\x82\xC2\xBE\xC3\x84\x63\xC3\x91\x7C\xC3\x81\xC2\x9A\xC3\xBB\x11\xC2\x8B\xC2\xA5\xC3\xB7\x36\xC2\x83\x1C\xC3\x8A\xC2\x8D\x29\xC3\x99\xC3\x97\xC3\x8E\x18\xC2\xB2\xC2\xB2\x1C\xC2\x98\x35\x36\x62\x39
```
Ini adalah format utf-8, sehingga tinggal kita konvert lagi menjadi ascii biasa, sehingga diperoleh
A_b1t_0f_b1t_sh1fTiNg_8bed9056b9

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{A_b1t_0f_b1t_sh1fTiNg_8bed9056b9}
  ```
</details>

## 5. asm2 (250)

### Soal :
What does asm2(0xc,0x15) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. Source located in the directory at /problems/asm2_1_909e8254810b229a481cafb41b58a005.

### Pembahasan : 
Berikut adalah source code dari file assembly nya
```
asm2:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	sub    esp,0x10
	<+6>:	mov    eax,DWORD PTR [ebp+0xc]
	<+9>:	mov    DWORD PTR [ebp-0x4],eax
	<+12>:	mov    eax,DWORD PTR [ebp+0x8]
	<+15>:	mov    DWORD PTR [ebp-0x8],eax
	<+18>:	jmp    0x50c <asm2+31>
	<+20>:	add    DWORD PTR [ebp-0x4],0x1
	<+24>:	add    DWORD PTR [ebp-0x8],0xaf
	<+31>:	cmp    DWORD PTR [ebp-0x8],0xa3d3
	<+38>:	jle    0x501 <asm2+20>
	<+40>:	mov    eax,DWORD PTR [ebp-0x4]
	<+43>:	leave  
	<+44>:	ret    

```
Pada baris 0 sampai dengan baris 3 adalah proses inisialisasi, pada 3 baris pertama tidak tampak dimana variabel 0xc dan 0x15 disimpan, sehingga liat baris berikutnya. Pada baris 9 dan 15 adalah tempat menyimpan nilai 0xc dan 0x15 dimana ebp-0x4 menyimpan 0xc dan ebp-0x8 menyimpan 0x15

setelah menyimpan ke ebp-0x4 dan ebp-0x8, maka lanjut ke baris dibawahnya dimana lompat ke baris 31, dibaris 31 ada perintah cmp yaitu compare untuk membandingkan variabel ebp-0x8 (0x15) dengan 0xa3d3, apabila lebih kecil(memang lebih kecil 0x15) maka lanjut ke baris 38 dimana ada perintah jle yaitu lompat ke baris 20 jika lebih kecil, apabila diperhatikan akan terjadi looping pada baris 20 ke 31 yaitu nilai variabel ebp-04 akan terus ditambah 0x1 dan ebp-0x8 akan terus ditambah dengan 0xaf sampai nilai ebp-0x8 lebih besar dari 0xa3d3
sehingga bisa menggunakan kode berikut

class loop{
    public static void main (String[] args){
        //e4 = ebp-0x4
        //e8 = ebp-0x8
        int e4 = 12;
        int e8 = 21;
        while(e8<=41939){
            e4+=1;
            e8+=175;
        }
        System.out.println(Integer.toHexString(e4));
    }
}

sehingga nantinya akan menghasilkan flag 0xfc
Note: Untuk soal ini sudah coba cara lain dan tetap menghasilkan output 0xfc, tetapi ketika menginputkan di picoctf tetap menyatakan jawaban incorrect padahal hasilnya tetap 0xfc

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{0xfc}
  ```
</details>

## 6. Need for Speed (400)

### Soal :
The name of the game is speed. Are you quick enough to solve this problem and keep it above 50 mph? need-for-speed.

### Pembahasan :
dicek file need for speed ini file apa dulu, setelah di cek adalah file ELF, lalu dicoba dijalankan dan menghasilkan output berikut
```
Keep this thing over 50 mph!
============================

Creating key...
Not fast enough. BOOM!
```
Maka dicoba lihat codingannya dengan menggunakan tools untuk reversing seperti IDA, Ghidra dsb.
Berikut tampilan ketika membuka ghidra
![](/Rekayasa%20Balik/ss_writeup_aldifp01/nfs1.png)
Maka kita mencari main class dari kodingan tersebut, cek pada bagian symbol tree dan terdapat main class yang codingannya sebagai berikut
```
undefined8 main(void)

{
  header();
  set_timer();
  get_key();
  print_flag();
  return 0;
}
```
Pada program tersebut, yang pertama kali dijalankan adalah fungsi header(), maka double klik untuk menuju fungsi tersebut dan kita memperoleh codingan yang menampilkan hal pertama kali yang kita lihat di terminal
```
void header(void)

{
  uint local_c;
  
  puts("Keep this thing over 50 mph!");
  local_c = 0;
  while (local_c < 0x1c) {
    putchar(0x3d);
    local_c = local_c + 1;
  }
  puts("\n");
  return;
}
```
Karena kita hanya membutuhkan flagnya maka kita cukup mengecek bagian yang berkaitan dengan flag yaitu fungsi decrypt_flag(), get_key(), dan print_flag(). Berikut adalah source code masing-masing fungsi
```
void decrypt_flag(int param_1)

{
  int local_1c [4];
  uint local_c;
  
  local_1c[0] = param_1;
  local_c = 0;
  while (local_c < 0x37) {
    flag[(int)local_c] =
         flag[(int)local_c] ^
         *(byte *)((long)local_1c +
                  (long)(int)((local_c - ((int)local_c >> 0x1f) & 1) + ((int)local_c >> 0x1f)));
    if ((int)local_c % 3 == 2) {
      local_1c[0] = local_1c[0] + 1;
    }
    local_c = local_c + 1;
  }
  return;
}

void get_key(void)

{
  puts("Creating key...");
  key = calculate_key();
  puts("Finished");
  return;
}

void print_flag(void)

{
  puts("Printing flag:");
  decrypt_flag((ulong)key);
  puts(flag);
  return;
}
```
Pada fungsi decrypt_key() sepertinya adalah fungsi untuk menampilkan angka-angka random pada flag seperti beberapa soal sebelumnya yang memiliki angka dan huruf random di akhir flagnya. Maka kita lewatkan saja dan langsung ke fungsi get_key(). Pada fungsi get_key() dia memanggil fungsi lain yakni fungsi calculate_key() berikut source codenya

```
undefined8 calculate_key(void)

{
  int local_c;
  
  local_c = -0x4449873c;
  do {
    local_c = local_c + -1;
  } while (local_c != -0x2224c39e);
  return 0xdddb3c62;
}
```
Pada fungsi tersebut, dia akan mengembalikan nilai dari alamat 0xdddb3c62, maka kita simpan dulu sebagai clue untuk jawabannya. Untuk fungsi print_flag() hanya memprint flag yang kita peroleh di terminal, sehingga flag kemungkinan disembunyikan dalam fungsi calculate_key() ini.

Ketika membuka fungsi get_key() tadi, pada bagian assembly kita bisa melihat ada string 32 bit yang diperoleh ketika fungsi get_key() selesai memanggil calculate_key()
```
                             **************************************************************
                             *                          FUNCTION                          *
                             **************************************************************
                             undefined get_key()
             undefined         AL:1           <RETURN>
                             get_key                                         XREF[3]:     Entry Point(*), main:0010099c(c), 
                                                                                          00100b74  
        001008d7 55              PUSH       RBP
        001008d8 48 89 e5        MOV        RBP,RSP
        001008db 48 8d 3d        LEA        RDI,[s_Creating_key..._00100ade]                 = "Creating key..."
                 fc 01 00 00
        001008e2 e8 69 fd        CALL       puts                                             int puts(char * __s)
                 ff ff
        001008e7 b8 00 00        MOV        EAX,0x0
                 00 00
        001008ec e8 50 ff        CALL       calculate_key                                    undefined calculate_key()
                 ff ff
        001008f1 89 05 65        MOV        dword ptr [key],EAX                              = ??
                 07 20 00
        001008f7 48 8d 3d        LEA        RDI,[s_Finished_00100aee]                        = "Finished"
                 f0 01 00 00
        001008fe e8 4d fd        CALL       puts                                             int puts(char * __s)
                 ff ff
        00100903 90              NOP
        00100904 5d              POP        RBP
        00100905 c3              RET
```
Maka, kita coba mencari alamat key pada program ini pada bagian fungsi get_key() dengan menggunakan kode berikut dan sekaligus hasilnya (sebetulnya masih kurang paham apakah kode ini memanggil pada fungsi atau mencari alamat pada fungsi, karena nanti juga menggunakan kode call untuk memanggil fungsi. Maka kita coba debug dengan menggunakan gdb, sumber referensi untuk kode-kode software gdb dari https://www.ibm.com/support/pages/debugger-commands-aix-dbx-solaris-dbx-linux-gdb) 
![](![](https://github.com/divisi-security-poros/WU-PicoCTF-2019/blob/rekayasa-2/Rekayasa%20Balik/ss_writeup_aldifp01/nfs2.png)
```
(gdb) x/32i get_key()
'get_key' has unknown return type; cast the call to its declared return type
(gdb) x/32i get_key
   0x5555555548d7 <get_key>:    push   %rbp
   0x5555555548d8 <get_key+1>:  mov    %rsp,%rbp
   0x5555555548db <get_key+4>:  lea    0x1fc(%rip),%rdi        # 0x555555554ade
   0x5555555548e2 <get_key+11>: callq  0x555555554650 <puts@plt>
   0x5555555548e7 <get_key+16>: mov    $0x0,%eax
   0x5555555548ec <get_key+21>: callq  0x555555554841 <calculate_key>
   0x5555555548f1 <get_key+26>: mov    %eax,0x200765(%rip)        # 0x55555575505c <key>
   0x5555555548f7 <get_key+32>: lea    0x1f0(%rip),%rdi        # 0x555555554aee
   0x5555555548fe <get_key+39>: callq  0x555555554650 <puts@plt>
   0x555555554903 <get_key+44>: nop
   0x555555554904 <get_key+45>: pop    %rbp
   0x555555554905 <get_key+46>: retq   
   0x555555554906 <print_flag>: push   %rbp
   0x555555554907 <print_flag+1>:       mov    %rsp,%rbp
   0x55555555490a <print_flag+4>:       lea    0x1e6(%rip),%rdi        # 0x555555554af7
   0x555555554911 <print_flag+11>:      callq  0x555555554650 <puts@plt>
   0x555555554916 <print_flag+16>:      mov    0x200740(%rip),%eax        # 0x55555575505c <key>
   0x55555555491c <print_flag+22>:      mov    %eax,%edi
   0x55555555491e <print_flag+24>:      callq  0x5555555547ba <decrypt_flag>
   0x555555554923 <print_flag+29>:      lea    0x2006f6(%rip),%rdi        # 0x555555755020 <flag>
   0x55555555492a <print_flag+36>:      callq  0x555555554650 <puts@plt>
   0x55555555492f <print_flag+41>:      nop
   0x555555554930 <print_flag+42>:      pop    %rbp
   0x555555554931 <print_flag+43>:      retq   
   0x555555554932 <header>:     push   %rbp
   0x555555554933 <header+1>:   mov    %rsp,%rbp
   0x555555554936 <header+4>:   sub    $0x10,%rsp
   0x55555555493a <header+8>:   lea    0x1cf(%rip),%rdi        # 0x555555554b10 <title>
   0x555555554941 <header+15>:  callq  0x555555554650 <puts@plt>
   0x555555554946 <header+20>:  movl   $0x0,-0x4(%rbp)
   0x55555555494d <header+27>:  jmp    0x55555555495d <header+43>
   0x55555555494f <header+29>:  mov    $0x3d,%edi
(gdb) 

```
maka diperoleh beberapa alamat yang bertanda <key> yaitu 0x55555575505c <key> dan diperhatikan pun alamat yang bertanda <key> dibawahnya juga memiliki alamat yang sama maka kita asumsikan ini adalah alamat dari flag yang kita cari.

Karena pada awal program ditampilkan string "Keep this thing over 50 mph!" maka bisa kita anggap pada program ini kita disuruh untuk menetapkan kecepatannya, maka kita bisa menggunakan kode "set" pada program gdb untuk menetapkan kecepatannya(????). Karena tadi pada fungsi calculate_key() kita memperoleh hasil kembalian 0xdddb3c62 maka kita coba set nilai tersebut ke alamat key yang diperoleh tadi dengan kode berikut.
```
(gdb) set *0x55555575505c=0xdddb3c62
```
Lalu ketika sudah selesai kita memanggil fungsi print_flag() saja dan diperoleh flagnya
```
(gdb) set *0x55555575505c=0xdddb3c62
(gdb) call (int) print_flag()
Printing flag:
PICOCTF{Good job keeping bus #3044d295 speeding along!}  <=== FLAG
$1 = 56
(gdb) 
```
![](https://github.com/divisi-security-poros/WU-PicoCTF-2019/blob/rekayasa-2/Rekayasa%20Balik/ss_writeup_aldifp01/nfs3-flag.png)
Note: flagnya harus PICOCTF bukan picoCTF, tadi coba picoCTF error terus. Lalu diganti PICOCTF baru berhasil.

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  PICOCTF{Good job keeping bus #3044d295 speeding along!}
  ```
</details>


## 7. Times Up (400)

### Soal :
Time waits for no one. Can you solve this before time runs out? times-up, located in the directory at /problems/time-s-up_2_af1f9d8c14e16bcbe591af8b63f7e286.

### Pembahasan :
apabila dijalankan, akan menghasilkan output berikut di terminal
```
aldifp@yeet:~/Downloads$ chmod u+x times-up 
aldifp@yeet:~/Downloads$ ./times-up 
Challenge: (((((930539767) + (1181663714)) + ((856582956) - (1829395316))) + (((-1643528655) + (-2096886184)) - ((-1707775392) + (-99716392)))) + ((((1865653964) + (890205809)) + ((107796394) + (104165492))) + (((-689395166) + (332092222)) + ((1407115857) + ((1716934084) + ((1739019604) + (98724769)))))))
Setting alarm...
Solution? Alarm clock
aldifp@yeet:~/Downloads$ ./times-up 
Challenge: (((((-49451200) + (1582584178)) - ((1362608585) + (-2026784124))) + (((1260328643) + (1806337254)) + ((-409794585) + (182787472)))) - ((((855455784) + (-970426272)) + ((1748305336) + (751220))) + (((140473844) - (968261581)) + ((-1722414546) - (-1166469945)))))
Setting alarm...
Solution? Alarm clock
aldifp@yeet:~/Downloads$ ./times-up 
Challenge: ((((((553821067) - (262901970)) + ((1155802879) + (-981775392))) - (((294119884) + (280872066)) + ((655199101) + (-2025844732)))) + ((((778592896) + (-1257435136)) + ((-1635430208) - (713727124))) + (((-2037626534) + (-1634563798)) - ((2146529585) + (778414658))))) + ((((-1777977491) + (375915895)) - ((1331900600) + (-1285020888))) + (((496315348) + (-154118224)) + (((1435449249) + (1494050812)) + (-448275972)))))
Setting alarm...
Solution? Alarm clock
aldifp@yeet:~/Downloads$ 
```
Ketika dijalankan 3 kali soalnya ternyata bertukar atau acak dan kita tidak sempat membuat jawabannya satu detik pun. Maka kita coba cek dengan menggunakan Ghidra seperti soal need-for-speed dan berikut source-codenya
```
undefined8 main(void)

{
  init_randomness();
  printf("Challenge: ");
  generate_challenge();
  putchar(10);
  fflush(stdout);
  puts("Setting alarm...");
  fflush(stdout);
  ualarm(5000,0);
  printf("Solution? ");
  __isoc99_scanf(&DAT_00100e68,&guess);
  if (guess == result) {
    puts("Congrats! Here is the flag!");
    system("/bin/cat flag.txt");
  }
  else {
    puts("Nope!");
  }
  return 0;
}
```
Pada fungsi main tersebut terdapat alarm yang terus, maka untuk mengakali supaya jawaban langsung digenerate sekaligus dengan soal kita menggunakan pwntools yang terdapat pada python. Apabila belum memiliki pwntools bisa diinstall dengan kode berikut. Namun untuk soal ini kita melakukannya di shell picoctf langsung karena file flagnya tersimpan di server karena nanti akan menghasilkan output berikut apabila dijalankan di komputer kita
```
oot@yeet:/home/aldifp/Downloads# python3 times-up_answer.py 
[+] Starting local process './times-up': pid 6927
[*] Switching to interactive mode
Setting alarm...
Solution? Congrats! Here is the flag!
/bin/cat: flag.txt: No such file or directory
[*] Process './times-up' stopped with exit code 0 (pid 6927)
[*] Got EOF while reading in interactive
```
![](/Rekayasa%20Balik/ss_writeup_aldifp01/timesuppico.png)
Karena kita tidak memiliki flag.txt jadi kita lakukan langsung di shell picoctf karena kemungkinan besar file flagnya ada di server. Ketika sudah masuk di shell picoctf, kita menggunakan vim untuk membuat source code berikut
```
from pwn import *
tgt=process('./times-up')
tgt.recvuntil("Challenge: ")
soal=tgt.recvline()
ans=eval(soal)
tgt.sendline(str(ans))
tgt.interactive()
```
dimana tgt adalah variabel dari target kita yakni program times-up, karena file kodingan tidak bisa dibuat di direktori file soal maka file ans.py atau jawabannya dibuat di home akun shell pico kita. lalu recvuntil adalah receive until dimana kita memperoleh output sampai ditemukan kembali kalimat "Challenge: ". recvline berguna untuk memperoleh satu baris kalimat yang kita cari dari variabel tgt yang nantinya akan disimpan pada variabel soal. Varibel soal ini nantinya akan dikembalikan dalam tipe integer dan diubah lagi menjadi string ketika flagnya dikirim ke shell(mungkin agak banyak salah penjelasannya, source penggunaan pwntool => http://folk.uio.no/laszloe/ctf/pwn_tools.pdf)

Sehingga menghasilkan output berikut
picoCTF{Gotta go fast. Gotta go FAST. #2d5896e7}
![](/Rekayasa%20Balik/ss_writeup_aldifp01/timesuppico2.png)

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{Gotta go fast. Gotta go FAST. #2d5896e7}
  ```
</details>

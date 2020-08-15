# Rekayasa Balik

## Penulis: Aldi Fianda Putra
## Daftar Isi:

| Rekayasa Balik  |
| ------------- |
| [vault-door-1](#1-vault-door-1-100)|
| [vault-door-3](#2-vault-door-3-200)|
| [asm2](#5-asm2-250)|
| [vault-door-5](#3-vault-door-5-300)|
| [Need For Speed]()|
| [vault-door-7](#4-vault-door-7-400)|
| [Time’s Up]()|

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

## 7. Times Up (400)

### Soal :
Time waits for no one. Can you solve this before time runs out? times-up, located in the directory at /problems/time-s-up_2_af1f9d8c14e16bcbe591af8b63f7e286.

### Pembahasan :
apabila dijalankan, akan menghasilkan output berikut di terminal
```
Challenge: (((((-12670668) + (-1525983192)) - ((-487639676) + (-1456687918))) + (((730127022) + (1847512308)) + ((-785510976) + (-1746866173)))) + ((((496937776) + (-1563843520)) - ((-904243887) + (-2020528688))) - (((1451319968) - (-1389348315)) + ((499030898) + (-1697184120)))))
Setting alarm...
Solution? Alarm clock
```

# Rekayasa Balik

## Penulis: [Seseorang01]
## Daftar Isi:

| Rekayasa Balik  |
| ------------- |
| [vault-door-1]()|
| [vault-door-3]()|
| [asm2]()|
| [vault-door-5]()|
| [Need For Speed]()|
| [vault-door-7]()|
| [Time’s Up]()|

---
## 1. vault-door-1

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

maka diperoleh kondisi checkPassword, sehingga tinggal mengurutkan 32 char dari 0 sampai 31 sehingga diperoleh passwordnya sebagai berikut
d35cr4mbl3_tH3_cH4r4cT3r5_9d038f
```
<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_9d038f}
  ```
</details>

## 2. vault-door-3

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

sehingga diperoleh hasil output sebagai berikut
jU5t_a_s1mpl3_an4gr4m_4_u_5baf7c
```

<details>
  <summary>Tekan untuk melihat flag</summary>
  
  ```
  picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_5baf7c}
  ```
</details>

## 3. vault-door-5

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

## 4. asm2

### Soal :

### Pembahasan : 

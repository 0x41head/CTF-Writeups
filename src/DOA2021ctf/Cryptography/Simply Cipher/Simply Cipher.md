# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Cryptography/Simply%20Cipher/ques.png)

## Solution:
In this challenge we arre provided with the encrypted text `Vwshc'j htpn mj iwxuk kq jt JMGJMG_HKRKV!`

I had no clue what this cipher could have been so I copy pasted this cipher into a [cipher identifier](https://www.dcode.fr/cipher-identifier)

Here it showed that the cipher had a high probabilty of being a Vigenere Cipher.

This was a problem as I had no clue what the key for the cipher could be.

Luckily https://www.dcode.fr/vigenere-cipher allowed me to enter some "known plaintext word". 

I tried a bunch of different words before trying 'flag' 

![flag](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Cryptography/Simply%20Cipher/flag.png)

The key was `CIPHER` and the flag text was `CIPHER_AGAIN!`
### Notes:
### Reference:

### Tags:
`Crypto` 
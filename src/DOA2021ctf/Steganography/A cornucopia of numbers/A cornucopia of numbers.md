# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/A%20cornucopia%20of%20numbers/ques.png)

## Solution:

In this question we are given a txt file with the following text:
```
01010010 01000101 00111001 00110111 01010001 01111010 01000010 01110101 01010110 01101101 01010110 01010011 01001110 01010100 01000101 01110111 01100010 01101100 00111001 01110100 01001110 01000101 01010010 01110101 01001101 01111010 01010101 00110001 01100110 01010001 00111101 00111101
```
Decoding this binary I got a base64 string
```
RE97QzBuVmVSNTEwbl9tNERuMzU1fQ==
```
Decoding that got me the flag :
```
DO{C0nVeR510n_m4Dn355}
```
### Notes:
### Reference:

### Tags:
`Forensics` `Steganography`
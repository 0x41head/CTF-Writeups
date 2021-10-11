# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Hash%20Cracking/Hash7/ques.png)

## Solution:

Very similar to [Hash4](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Hash%20Cracking/Hash4/hash4.html) ,[Hash5](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Hash%20Cracking/Hash5/hash5.html) and [Hash 6](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Hash%20Cracking/Hash6/hash6.html)

```
$ ./hashid.py -m '$6$veryrandomsalt$t8EIWEiDpWYzeC1c44q7f6ZENOuO2wagnrJBPs4d/PptWxAxlnH7qRcf0xnKagaOEHBN9dGBV5Y1syJSB3s6H1'
Analyzing '$6$veryrandomsalt$t8EIWEiDpWYzeC1c44q7f6ZENOuO2wagnrJBPs4d/PptWxAxlnH7qRcf0xnKagaOEHBN9dGBV5Y1syJSB3s6H1'
[+] SHA-512 Crypt [Hashcat Mode: 1800]
```

```
$ hashcat -m 1800 -a 0 '$6$veryrandomsalt$t8EIWEiDpWYzeC1c44q7f6ZENOuO2wagnrJBPs4d/PptWxAxlnH7qRcf0xnKagaOEHBN9dGBV5Y1syJSB3s6H1' rockyou.txt --show 
$6$veryrandomsalt$t8EIWEiDpWYzeC1c44q7f6ZENOuO2wagnrJBPs4d/PptWxAxlnH7qRcf0xnKagaOEHBN9dGBV5Y1syJSB3s6H1:igetmoney
```

### Notes:

### Reference:
https://unicornsec.com/home/tryhackme-crack-the-hash

https://resources.infosecinstitute.com/topic/hashcat-tutorial-beginners/

### Tags:
`Hash` 
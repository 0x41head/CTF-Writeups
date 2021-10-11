# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Hash%20Cracking/Hash6/ques.png)

## Solution:

Very similar to [Hash4](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Hash%20Cracking/Hash4/hash4.html) and [Hash5](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Hash%20Cracking/Hash5/hash5.html)

```
$ ./hashid.py -m '$1$veryrand$QetWu27IoJ2FFSG30xKAQ.'
Analyzing '$1$veryrand$QetWu27IoJ2FFSG30xKAQ.'
[+] MD5 Crypt [Hashcat Mode: 500]
[+] Cisco-IOS(MD5) [Hashcat Mode: 500]
[+] FreeBSD MD5 [Hashcat Mode: 500]
```

```
$ hashcat -m 500 -a 0 '$1$veryrand$QetWu27IoJ2FFSG30xKAQ.' rockyou.txt --show
$1$veryrand$QetWu27IoJ2FFSG30xKAQ.:scottiebanks
```

### Notes:

### Reference:
https://unicornsec.com/home/tryhackme-crack-the-hash

https://resources.infosecinstitute.com/topic/hashcat-tutorial-beginners/

### Tags:
`Hash` 
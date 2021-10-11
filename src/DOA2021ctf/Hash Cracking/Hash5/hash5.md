# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Hash%20Cracking/Hash5/ques.png)

## Solution:

Very similar to (Hash4)[]

```
$ ./hashid.py -m '$2a$10$QlR/ZlXgQPWfx9JmRffMZutcL3o3w6JAiRbfvGda4u09lrfOvgcH6'
Analyzing '$2a$10$QlR/ZlXgQPWfx9JmRffMZutcL3o3w6JAiRbfvGda4u09lrfOvgcH6'
[+] Blowfish(OpenBSD) [Hashcat Mode: 3200]
[+] Woltlab Burning Board 4.x 
[+] bcrypt [Hashcat Mode: 3200]
```

```
$ hashcat -m 3200 -a 0  '$2a$10$QlR/ZlXgQPWfx9JmRffMZutcL3o3w6JAiRbfvGda4u09lrfOvgcH6' rockyou.txt --show
$2a$10$QlR/ZlXgQPWfx9JmRffMZutcL3o3w6JAiRbfvGda4u09lrfOvgcH6:cowabunga
```

### Notes:

### Reference:
https://unicornsec.com/home/tryhackme-crack-the-hash

https://resources.infosecinstitute.com/topic/hashcat-tutorial-beginners/

### Tags:
`Hash` 
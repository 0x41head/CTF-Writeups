# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Hash%20Cracking/Hash4/ques.png)

## Solution:

Doing the same thing we did in the last three questions didn't work this time.

![nottheanswer](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Hash%20Cracking/Hash4/1.png) 

So the next thing I did was try to identify the hash using [Hash-Identifier](https://tools.kali.org/password-attacks/hash-identifier)

```
$ ./hashid.py -m '451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723'
Analyzing '451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723'
[+] Snefru-256 
[+] SHA-256 [Hashcat Mode: 1400]
[+] RIPEMD-256 
[+] Haval-256 
[+] GOST R 34.11-94 [Hashcat Mode: 6900]
[+] GOST CryptoPro S-Box 
[+] SHA3-256 [Hashcat Mode: 5000]
[+] Skein-256 
[+] Skein-512(256) 
```
We can see a number of hashes that `451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723` could be.

I first tried `1400` as my hashcat mode.

```
$ hashcat -m 1400 -a 0 -o cracked.txt '451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723' rockyou.txt 
hashcat (v5.1.0) starting...

* Device #1: WARNING! Kernel exec timeout is not disabled.
             This may cause "CL_OUT_OF_RESOURCES" or related errors.
             To disable the timeout, see: https://hashcat.net/q/timeoutpatch
nvmlDeviceGetFanSpeed(): Not Supported

OpenCL Platform #1: NVIDIA Corporation
======================================
* Device #1: GeForce MX150, 1010/4042 MB allocatable, 3MCU

INFO: All hashes found in potfile! Use --show to display them.

Started: Mon Oct 11 17:16:34 2021
Stopped: Mon Oct 11 17:16:35 2021
```

and checked the contents of `cracked.txt`

```
451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723:happyfamily
```

The hash was cracked and I retrieved the flag

### Notes:
```
$ ./hashid.py -m '451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723'
Analyzing '451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723'
[+] Snefru-256 
[+] SHA-256 [Hashcat Mode: 1400]
[+] RIPEMD-256 
[+] Haval-256 
[+] GOST R 34.11-94 [Hashcat Mode: 6900]
[+] GOST CryptoPro S-Box 
[+] SHA3-256 [Hashcat Mode: 5000]
[+] Skein-256 
[+] Skein-512(256) 
```
The hash `451716a045ca5ec7f25e191ab5244c61aaeeb008c4753a2065e276f1baba4723`could have technically belonged to any of the hash types given above
I got lucky as I just chose the first hashcat mode from above i.e. `1400` .

As a rule of thumb, first try all hashcat modes then go looking for the other hash types given above.

### Reference:
https://unicornsec.com/home/tryhackme-crack-the-hash

https://resources.infosecinstitute.com/topic/hashcat-tutorial-beginners/

### Tags:
`Hash` 
# Problem Statement:
![q4](https://user-images.githubusercontent.com/53595853/135750378-78a1e93e-4654-4cb5-bf13-ef4c9b35324a.png)


## Solution:

The challenge contained a `.txt` file file with the following text:
```
Ever used RSA Encryption?

cyphertext = 10400286653072418349777706076384847966640064725838262071
n = 23519325203263800569051788832344215043304346715918641803
e = 71
```
Unciphering this RSA encryption using RSACtfTool I got the flag

```
$ python3 RsaCtfTool.py -n 23519325203263800569051788832344215043304346715918641803 -e 71 --uncipher 10400286653072418349777706076384847966640064725838262071
private argument is not set, the private key will not be displayed, even if recovered.

[*] Testing key /tmp/tmpve86_p91.
[*] Performing mersenne_primes attack on /tmp/tmpve86_p91.
 24%|█████████████████▉                                                          | 12/51 [00:00<00:00, 68200.07it/s]
[*] Performing system_primes_gcd attack on /tmp/tmpve86_p91.
100%|███████████████████████████████████████████████████████████████████████| 7007/7007 [00:00<00:00, 733270.66it/s]
[*] Performing fibonacci_gcd attack on /tmp/tmpve86_p91.
100%|███████████████████████████████████████████████████████████████████████| 9999/9999 [00:00<00:00, 161604.08it/s]
[*] Performing pastctfprimes attack on /tmp/tmpve86_p91.
100%|████████████████████████████████████████████████████████████████████████| 113/113 [00:00<00:00, 1057938.29it/s]
[*] Performing factordb attack on /tmp/tmpve86_p91.
[*] Attack success with factordb method !

Results for /tmp/tmpve86_p91:

Unciphered data :
HEX : 0x6473637b7430305f6d7563685f6d3474685f383839387d
INT (big endian) : 9621269132073872010525638902903988134500010392708266109
INT (little endian) : 11993657127041496499871362328745731192598296696556057444
utf-8 : dsc{t00_much_m4th_8898}
STR : b'dsc{t00_much_m4th_8898}'
```

### Notes:
### Reference:
### Tags:
`Crypto` 
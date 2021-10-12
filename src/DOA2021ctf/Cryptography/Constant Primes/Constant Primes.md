# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Cryptography/Constant%20Primes/ques.png)

## Solution:
This challenge came accompnied with a PEM RSA private key file and some encrypted text.

I used RSACtfTool to dump all the parameters of the private key.
```
$ python3 RsaCtfTool.py --dumpkey --key id_rsa
private argument is not set, the private key will not be displayed, even if recovered.
n: 6682669787535606635993287896641983501298577520322405381880667699429293248249880135523414618303313461640928583929883384586229757283439591741435143918813267
e: 65537
d: 1245027970548083632535484462486818416327504028611876798034132667196113196532172132358378811626065371085166960566608788272800224255834470207284908804798673
p: 107463941641714513567663994750835343310501579557929436616696679781596584684287
q: 62185228695739372264534353091172447847235419898011544232913573133394316922541

``` 
And then used the dumped values as input parameters for RSACtfTool to decipher the encrypted text.
```
$ python3 RsaCtfTool.py -n 6682669787535606635993287896641983501298577520322405381880667699429293248249880135523414618303313461640928583929883384586229757283439591741435143918813267 -e 65537 --uncipher 0x2085f3d3573cd709fad84bed9fe8dde419fb7c8e96aa95ec4651a3bc07b5552f321e03404943744d931a4a51a817cf190880a5efbf94aa828c45da5b31dcdefc
private argument is not set, the private key will not be displayed, even if recovered.

[*] Testing key /tmp/tmpo0aku_gu.
[*] Performing mersenne_primes attack on /tmp/tmpo0aku_gu.
 24%|█████████████████▉                                                          | 12/51 [00:00<00:00, 56807.73it/s]
[*] Performing system_primes_gcd attack on /tmp/tmpo0aku_gu.
100%|███████████████████████████████████████████████████████████████████████| 7007/7007 [00:00<00:00, 526033.44it/s]
[*] Performing fibonacci_gcd attack on /tmp/tmpo0aku_gu.
100%|████████████████████████████████████████████████████████████████████████| 9999/9999 [00:00<00:00, 92156.88it/s]
[*] Performing pastctfprimes attack on /tmp/tmpo0aku_gu.
100%|█████████████████████████████████████████████████████████████████████████| 113/113 [00:00<00:00, 784695.95it/s]
[*] Performing factordb attack on /tmp/tmpo0aku_gu.
[*] Attack success with factordb method !

Results for /tmp/tmpo0aku_gu:

Unciphered data :
HEX : 0x000000000000000000000000000000000000000000000000000000000000000000000000000000007d647261685f746168745f74306e5f73315f4153527b4f44
INT (big endian) : 3074611973687495957380722994585818588376354850331241959236
INT (little endian) : 3577709902134466373061792066659718936003299812835724795912841936081230802293987207449114838506716387761084937458663882515354370797684440561438165393473536
utf-8 : }drah_taht_t0n_s1_ASR{OD
utf-16 : 摽慲彨慴瑨瑟渰獟弱十筒䑏
STR : b'\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00}drah_taht_t0n_s1_ASR{OD'
```
The deciphered text was a bit jumbled up but it take much to find what the flag was.

### Notes:
### Reference:

### Tags:
`Crypto` `RSA`
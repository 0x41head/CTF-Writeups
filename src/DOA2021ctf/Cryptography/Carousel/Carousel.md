# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Cryptography/Carousel/ques.png)

## Solution:
In this challenge we are provided with the encrypted text `s~LC_fcfb0>bN`

Bruting forcing my way through the different ciphers on [cryptii.com](https://cryptii.com/), I discovered that it was a ROT47 encryption and the decrypted text gave me the flag.
```
DO{r07473_m3}
```
### Notes:
### Reference:

### Tags:
`Crypto`

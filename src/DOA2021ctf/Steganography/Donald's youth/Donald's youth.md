# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/Donald's%20youth/ques.png)

## Solution:

In this question we are given a .jpg image of Donald Duck 

![Donald](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/Donald's%20youth/steg.jpg)

The question mentioned something about a rock concert. That gave me the idea to try brute-forcing this image for hidden data using 'rockyou.txt'

```
$ stegseek steg.jpg rockyou.txt
StegSeek 0.6 - https://github.com/RickdeJager/StegSeek

[i] Found passphrase: "062504012"         
[i] Original filename: "flag1.txt".
[i] Extracting to "steg.jpg.out".
```
Bingo !

The extracted file contained the following:
```
DO{4re_y00u_using_a_fast_steg_solve?_
second part: https://drive.google.com/file/d/1uEKzT1i20H4_RYiwF2KQ9lRPj-BJzjCi/view?usp=sharing
```
It said that it was a two part flag

Going to the drive link I get another image of Donald Duck, this time a bit angrier.

![AngryDOnald](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/Donald's%20youth/angrysteg.png)

Running this new png through `zsteg` gives me the second part of the flag.
```
$ zsteg angrysteg.png
imagedata           .. file: Apple DiskCopy 4.2 image \376, 33488896 bytes, 0x10001 tag size, GCR CLV ssdd (400k), 0x0 format
b1,bgr,lsb,xy       .. text: "or_ls4_by1ng_ok4y??}"
b2,r,lsb,xy         .. file: 5View capture file
b2,r,msb,xy         .. file: VISX image file
b2,g,lsb,xy         .. file: 5View capture file
b2,g,msb,xy         .. file: VISX image file
b2,b,lsb,xy         .. file: 5View capture file
b2,b,msb,xy         .. file: VISX image file
b2,rgb,lsb,xy       .. file: 5View capture file
b2,rgb,msb,xy       .. file: VISX image file
b2,bgr,lsb,xy       .. file: 5View capture file
b2,bgr,msb,xy       .. file: VISX image file
b4,r,msb,xy         .. text: ["w" repeated 9 times]
b4,g,msb,xy         .. text: ["w" repeated 10 times]
b4,b,msb,xy         .. text: ["w" repeated 11 times]
b4,rgb,msb,xy       .. text: ["w" repeated 28 times]
b4,bgr,msb,xy       .. text: ["w" repeated 29 times]
```

Joining them and removing the ?s (as told in the question) gives me the flag.

### Notes:
### Reference:

### Tags:
`Forensics` `Steganography` `jpg` `png` `image`
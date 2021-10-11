# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/Queen's%20gambit/ques.png)

## Solution:

In this question we are given a .png image of Freddie Mercury

```
$ exiftool Freddie_Mercury.png 
ExifTool Version Number         : 11.88
File Name                       : Freddie_Mercury.png
Directory                       : .
File Size                       : 457 kB
File Modification Date/Time     : 2021:10:09 11:17:44+05:30
File Access Date/Time           : 2021:10:09 11:17:44+05:30
File Inode Change Date/Time     : 2021:10:09 11:17:44+05:30
File Permissions                : rw-rw-r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 562
Image Height                    : 787
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Warning                         : [minor] Text chunk(s) found after PNG IDAT (may be ignored by some readers)
Author                          : RE97VzNfYVIzX3RoM19DaDRtUDEwblN9
Image Size                      : 562x787
Megapixels                      : 0.442
```

The author tag has some base64 text. Decoding this got me the flag

```
DO{W3_aR3_th3_Ch4mP10nS}
```
### Notes:
### Reference:

### Tags:
`Forensics` `Steganography`
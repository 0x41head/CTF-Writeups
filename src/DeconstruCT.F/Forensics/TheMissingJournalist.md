# Problem Statement:
![q2](https://user-images.githubusercontent.com/53595853/135742436-c0f510a9-3136-468d-a704-4dae4f859d0f.png)

## Solution:
In this challenge we are provided a `.gif` file

![the_journalist](https://user-images.githubusercontent.com/53595853/135742507-6716ad0a-1a8b-4b7d-992b-a998d07b43bc.gif)

I first decided to look into the metadata of the gif using exiftool

```
$ exiftool the_journalist.gif
ExifTool Version Number         : 11.88
File Name                       : the_journalist.gif
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2021:10:01 15:56:51+05:30
File Access Date/Time           : 2021:10:01 15:56:50+05:30
File Inode Change Date/Time     : 2021:10:01 15:56:53+05:30
File Permissions                : rw-rw-r--
File Type                       : GIF
File Type Extension             : gif
MIME Type                       : image/gif
GIF Version                     : 89a
Image Width                     : 498
Image Height                    : 314
Has Color Map                   : Yes
Color Resolution Depth          : 8
Bits Per Pixel                  : 6
Background Color                : 0
Animation Iterations            : Infinite
XMP Toolkit                     : Image::ExifTool 10.40
Creator                         : Anish Raghavendra
Rights                          : aDNfdzQ1X2w0NXRfczMzbl80dF90aDRfbTB2MTM1
Title                           : The Journalist
Frame Count                     : 40
Duration                        : 4.00 s
Image Size                      : 498x314
Megapixels                      : 0.156
```
There seems to be , what looks like a base64 encrypted string

Decrypting it we get,

```
$ echo "aDNfdzQ1X2w0NXRfczMzbl80dF90aDRfbTB2MTM1"|base64 -d
h3_w45_l45t_s33n_4t_th4_m0v135
```

I tried putting this as the answer, after formatting it to the flag format. 
But it wasn't the flag

Next I checked for any embedded file inside using binwalk.

```
$ binwalk -e the_journalist.gif

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             GIF image data, version "89a", 498 x 314
2267488       0x229960        Zip archive data, at least v1.0 to extract, name: message/
2267526       0x229986        Zip archive data, at least v2.0 to extract, compressed size: 112074, uncompressed size: 113455, name: message/message.pdf
2379840       0x245040        End of Zip archive, footer length: 22
```
There seems to be a message.pdf inside it.

![21](https://user-images.githubusercontent.com/53595853/135742801-257d0e93-2013-464a-8c12-f34e0b285425.png)

I try that string I got, when looking into the metadata, as my password.

![22](https://user-images.githubusercontent.com/53595853/135742876-fd7e03ce-f399-4e06-9dfb-5641e494607c.png)

and retrieve the flag !

### Notes:
### Reference:

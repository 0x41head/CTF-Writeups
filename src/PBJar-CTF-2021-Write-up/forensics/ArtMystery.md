 
# Problem Statement:

![artmys](https://user-images.githubusercontent.com/53595853/133997989-20d37eab-2fcd-403b-b86f-3c40bf8b14ef.png)

## Solution:

Downloading the `art.png` file I saw that it was corrupted.

![ar](https://user-images.githubusercontent.com/53595853/133999159-e57d5535-945d-4fb1-bde3-a14f853e9e0a.png)

I then decided to run a check to ensure it was actually a png file.

```
$ file art.png
art.png: PNG image data, 0 x 0, 8-bit/color RGBA, non-interlaced
```

After that, I decided to run `pngcheck` on the file to see what the issue was.

```
pngcheck -v art.png
File: art.png (896610 bytes)
  chunk IHDR at offset 0x0000c, length 13:  invalid image dimensions (0x0)
ERRORS DETECTED in art.png
```

The size of the png was invaid

Next, I looked into the hexdump of the png.
```
$ hexdump -C -n 64 art.png 
00000000  89 50 4e 47 0d 0a 1a 0a  00 00 00 0d 49 48 44 52  |.PNG........IHDR|
00000010  00 00 00 00 00 00 00 00  08 06 00 00 00 60 44 4c  |.............`DL|
00000020  b6 00 00 80 00 49 44 41  54 78 da ec bd f9 53 15  |.....IDATx....S.|
00000030  d9 96 3f da 75 6b 70 9e  4b 4b 2d e7 79 40 05 01  |..?.ukp.KK-.y@..|
```

After a bit of inspection, I saw that the width and height of the image had been maipulated to be 0.

Assuming that the CRC of the IHDR header chunk had not been manipulated with, I decided to do a brute force check with the CRC to get the height and width of the image.

I wrote this piece of code given below to do just that:

```
import os
import binascii
import struct

misc = open("art.png","rb").read()

for i in range(65535):
    for j in range(65535):
        data = misc[12:16] + struct.pack('>i',i)+ struct.pack('>i',j)+misc[24:29]
        crc32 = binascii.crc32(data) & 0xffffffff
        if crc32 == 0x60444cb6:
            print(i,j)
```

The above code when executed gave me `688 688`. Converting 688 to hex we get `2b0`

After changing these values using a hex editor, I checked the hexdump again:

```
hexdump -C -n 64 art.png
00000000  89 50 4e 47 0d 0a 1a 0a  00 00 00 0d 49 48 44 52  |.PNG........IHDR|
00000010  00 00 02 b0 00 00 02 b0  08 06 00 00 00 60 44 4c  |.............`DL|
00000020  b6 00 00 80 00 49 44 41  54 78 da ec bd f9 53 15  |.....IDATx....S.|
00000030  d9 96 3f da 75 6b 70 9e  4b 4b 2d e7 79 40 05 01  |..?.ukp.KK-.y@..|
```

I ran the file through `pngcheck` again, to check for any other errors

```
$ pngcheck -v art.png
File: art.png (896610 bytes)
  chunk IHDR at offset 0x0000c, length 13
    688 x 688 image, 32-bit RGB+alpha, non-interlaced
  chunk IDAT at offset 0x00025, length 32768
    zlib: deflated, 32K window, maximum compression
  chunk IDAT at offset 0x08031, length 32768
  chunk IDAT at offset 0x1003d, length 32768
  chunk IDAT at offset 0x18049, length 32768
  chunk IDAT at offset 0x20055, length 32768
  chunk IDAT at offset 0x28061, length 32768
  chunk IDAT at offset 0x3006d, length 32768
  chunk IDAT at offset 0x38079, length 32768
  chunk IDAT at offset 0x40085, length 32768
  chunk IDAT at offset 0x48091, length 32768
  chunk IDAT at offset 0x5009d, length 32768
  chunk IDAT at offset 0x580a9, length 32768
  chunk IDAT at offset 0x600b5, length 32768
  chunk IDAT at offset 0x680c1, length 32768
  chunk IDAT at offset 0x700cd, length 32768
  chunk IDAT at offset 0x780d9, length 32768
  chunk IDAT at offset 0x800e5, length 32768
  chunk IDAT at offset 0x880f1, length 32768
  chunk IDAT at offset 0x900fd, length 32768
  chunk IDAT at offset 0x98109, length 32768
  chunk IDAT at offset 0xa0115, length 32768
  chunk IDAT at offset 0xa8121, length 32768
  chunk IDAT at offset 0xb012d, length 32768
  chunk IDAT at offset 0xb8139, length 32768
  chunk IDAT at offset 0xc0145, length 32768
  chunk IDAT at offset 0xc8151, length 32768
  chunk IDAT at offset 0xd015d, length 32768
  chunk IDAT at offset 0xd8169, length 11493
  chunk IEND at offset 0xdae5a, length 0
No errors detected in art.png (30 chunks, 52.6% compression).
```
I opened the file and

![art](https://user-images.githubusercontent.com/53595853/134005162-c7a5b9c1-bf8b-4dc7-b216-cc4edf433dfa.png)

retrieved the flag!

### Notes:

**First 34 bytes explained**

`89 50 4e 47 0d 0a 1a 0a` - PNG file header

`49 48 44 52` - IHDR 

`00 00 00 00` - width

`00 00 00 00` - height

`08` - Bit depth

`06` - Color type 

`00` - Compression method

`00` - Filter method

`00` - Interlace method

`60 44 4c b6` - CRC

**Why 65535 in range ?**

65535 when converted to hex gives us `00 00 ff ff` + I thought that the height and width couldn't be greater than that as the size of the image was just 875kb

### Reference:

https://ctf-wiki.mahaloz.re/misc/picture/png/

http://www.libpng.org/pub/png/spec/1.2/PNG-Chunks.html

### Tags:
`Forensics` , `png` , `image`
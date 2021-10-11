# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/Phreak%20File/ques.png)

## Solution:

In this question we are given a .bmp file. However, when I tried to download it by the normal method (right click then save image) I was met with this webpage

![Nope](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Steganography/Phreak%20File/1.png)

Nothing I did worked here so I used `wget` to download the file.

```
$ wget -c 'https://files-digitaloverdose.ractf.co.uk/challenge-files/46/cbab78f3fe289f8d9cf1ae26acb92749/phreak_file.bmp'
--2021-10-11 22:23:58--  https://files-digitaloverdose.ractf.co.uk/challenge-files/46/cbab78f3fe289f8d9cf1ae26acb92749/phreak_file.bmp
Resolving files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)... 2600:9000:2244:2600:e:5f3e:3c0:93a1, 2600:9000:2244:5800:e:5f3e:3c0:93a1, 2600:9000:2244:3000:e:5f3e:3c0:93a1, ...
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:2600:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:5800:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:3000:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:1800:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:ca00:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:2c00:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:4600:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|2600:9000:2244:2e00:e:5f3e:3c0:93a1|:443... failed: No route to host.
Connecting to files-digitaloverdose.ractf.co.uk (files-digitaloverdose.ractf.co.uk)|54.192.171.114|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8509484 (8.1M) [image/bmp]
Saving to: ‘phreak_file.bmp’

phreak_file.bmp                                            100%[========================================================================================================================================>]   8.12M  3.38MB/s    in 2.4s    

2021-10-11 22:24:02 (3.38 MB/s) - ‘phreak_file.bmp’ saved [8509484/8509484]
```
After downloading and trying to open the file. It became clear that something was wrong with it.

So,I decided to use the `file` command to get some more info and found out that it was actually a wav file.

```
$ file 'phreak_file.bmp'
phreak_file.bmp: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz
```
After changing the file extension I tried listening to the audio and the sounds were similar to DTMF tones. My suspicion was further validated as in the question there was mention of some old phone from 1999.

I used (https://unframework.github.io/dtmf-detect/)[https://unframework.github.io/dtmf-detect/] to detect the DTMF tones.
After decoding the DTMF Tones I got:
```
22222337777777769999333444555337777
```
which when converted to text gave me:
```
ACCESSMZFILES
```

which when changed to the flag format was accepted as the correct flag (:

### Notes:
### Reference:
https://unframework.github.io/dtmf-detect/

### Tags:
`Forensics` `Steganography` `wav` `audio`
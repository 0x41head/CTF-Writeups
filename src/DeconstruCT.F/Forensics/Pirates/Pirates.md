# Problem Statement:
![q1](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Forensics/Pirates/ques.png)

## Solution:

In this challenge we are provided with a `network_listen.pcap` file.

For staters, I opened this file using Wireshark.
Filtering out the `http` requests I can see a packet with the info `GET /i_COULD_have_the_flag.mp4.torrent HTTP/1.1`

![11](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Forensics/Pirates/1.png)

I tried going to the website associated with this packet, `http://192.168.192.121:8080/i_COULD_have_the_flag.mp4.torrent` but I got no response.

So I took a step backwards, and followed the TCP stream of the HTTP request.

![12](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Forensics/Pirates/2.png)

There I found the flag

### Notes:

### Reference:
### Tags:
`Forensics` , `Wireshark` 
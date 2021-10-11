# Problem Statement:
![q1](https://user-images.githubusercontent.com/53595853/135741811-50fa9e98-971d-4af1-b664-a18ff2099bf3.png)

## Solution:

In this challenge we are provided with a `network_listen.pcap` file.

For staters, I opened this file using Wireshark.
Filtering out the `http` requests I can see a packet with the info `GET /i_COULD_have_the_flag.mp4.torrent HTTP/1.1`

![11](https://user-images.githubusercontent.com/53595853/135742201-a8bc731d-ecee-4ccc-9738-fae3f235dede.png)

I tried going to the website associated with this packet, `http://192.168.192.121:8080/i_COULD_have_the_flag.mp4.torrent` but I got no response.

So I took a step backwards, and followed the TCP stream of the HTTP request.

![12](https://user-images.githubusercontent.com/53595853/135742336-6ab429da-28cc-4597-94bc-d8ad673f68e8.png)

There I found the flag

### Notes:

### Reference:
### Tags:
`Forensics` , `Wireshark` 
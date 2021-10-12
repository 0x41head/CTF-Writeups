# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/git%20commit%20-m%20whatever/ques.png)

## Solution:
In this question we are given a URL to visit.

![1](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/notrequired/1.png)

After looking around the webpage for a while I intercepepted it using burp suite.

I then changed the page parameter in the url to something random and got this.

![2](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/notrequired/2.png)

After searching around a bit, I tried my hand in local file inclusions (LFI).

I used this awseome payload site for reference [https://github.com/payloadbox/rfi-lfi-payload-li](https://github.com/payloadbox/rfi-lfi-payload-list) 

We use the LFI wrapper given above to encode index.php in base64 and then decode it to find the source code.

![3](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/notrequired/3.png)

The file `/bin/secrets.txt` seemed suspicious.

Trying to access it using the file parameter in the URL we retreive the flag.

![flag](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/notrequired/flag.png)
### Notes:
### Reference:
https://medium.com/@Aptive/local-file-inclusion-lfi-web-application-penetration-testing-cc9dc8dd3601

https://github.com/payloadbox/rfi-lfi-payload-list
### Tags:
`Web` `git` 
# Problem Statement:
![q10](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/ques.png)

## Solution:
This challenge involved a lot of to and fro from between the website and me.

Going to the link given in the challenge we can see that we have an input field.
Typing a random name here give us the following webpage:

![Untitled](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/1.png)

I initially checked the source code for this webpage but after finding nothing useful there I intercepted it using burp suite.

(The next bit of the challenge just involves me going to and from between the request and webpage.So instead of writing anything I am just goning to paste screenshots of burp suite)

![Un1](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/2.png)
![Un2](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/3.png)
![Un3](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/4.png)
![Un4](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/5.png)
![Un5](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/6.png)
![Un6](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Please/7.png)


### Notes:
Basic Authorization uses base64 encoding 

### Reference:

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization

https://www.geeksforgeeks.org/http-headers-date/
### Tags:
`Web`,`Burp Suite` 
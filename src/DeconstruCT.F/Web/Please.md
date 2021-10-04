# Problem Statement:
![q10](https://user-images.githubusercontent.com/53595853/135763540-fb26eb8b-bcb5-4e34-bb97-86bd36db8b20.png)

## Solution:
This challenge involved a lot of to and fro from between the website and me.

Going to the link given in the challenge we can see that we have an input field.
Typing a random name here give us the following webpage:

![Untitled](https://user-images.githubusercontent.com/53595853/135764200-43ca141f-738e-49ba-8664-55bd1aff1b0c.png)

I initially checked the source code for this webpage but after finding nothing useful there I intercepted it using burp suite.

(The next bit of the challenge just involves me going to and from between the request and webpage.So instead of writing anything I am just goning to paste screenshots of burp suite)

![Un1](https://user-images.githubusercontent.com/53595853/135764865-40725618-1f5d-4a10-9e66-376485f611d3.png)
![Un2](https://user-images.githubusercontent.com/53595853/135764857-0d9af1d4-ae03-4bfc-a40c-389119f32fbf.png)
![Un3](https://user-images.githubusercontent.com/53595853/135764860-928f6744-01a7-4280-adce-e69fb9ceaf61.png)
![Un4](https://user-images.githubusercontent.com/53595853/135764861-6ad7654c-cbd9-4645-9199-776dee4243ba.png)
![Un5](https://user-images.githubusercontent.com/53595853/135764862-ffff2b3b-d69c-4243-a463-ff01e38bbc1a.png)
![Un6](https://user-images.githubusercontent.com/53595853/135764863-188a08fa-3aa3-4b37-95dc-5999c027b121.png)



### Notes:
Basic Authorization uses base64 encoding 

### Reference:

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization

https://www.geeksforgeeks.org/http-headers-date/
### Tags:
`Web`,`Burp Suite` 
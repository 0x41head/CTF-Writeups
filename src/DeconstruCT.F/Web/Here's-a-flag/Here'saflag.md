# Problem Statement:
![web1](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Web/Here's-a-flag/ques.png)

## Solution:
I opened the webpage and looked at it's source code.

It had a external css and js file.

The flag was in the css file.
```

.contain-flag::after {
  z-index: -64209;
  caesar-cipher: +3;
  flag: "gvf{zh0frph_wr_ghfrqvwuxfwi}";
}
```
The code tells us that it's a +3 caeser cipher.

Decrypting this we get our flag. 

### Notes:
There was a rickroll in the js file


### Reference:
### Tags:
`Web` 
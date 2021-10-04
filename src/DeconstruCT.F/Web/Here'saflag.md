# Problem Statement:
![web1](https://user-images.githubusercontent.com/53595853/135755509-ac7ecb89-1bac-45c9-81f9-f6217d3a451d.png)

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

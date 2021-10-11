# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Reversing/Dyns%2C%20Syms%2C%20and%20Tabs/ques.png)

## Solution:

This challenge came attached with a `chall` file.

According to this question, I have to find the C file name before the `chall` file was compiled.

I used `rabin2` to show all the exported symbols and then used `grep` along with some basic regex to get all C files.

```
$ rabin2 -qs chall | grep -i '\.c$'
0x00000000 0 crtstuff.c
0x00000000 0 u_f0unD_dA_f1a4y4Y.c
0x00000000 0 crtstuff.c
```
Putting `u_f0unD_dA_f1a4y4Y` in the proper flag notation, I retrieved the flag.

### Notes:
### Reference:
(https://www.youtube.com/watch?v=ubpBELyn0YM&list=PLfoNkunx5xzEZFfkiy2qBu1OONqtL0aiz&index=2)

(https://r2wiki.readthedocs.io/en/latest/tools/rabin2/)

### Tags:
`Reversing` 
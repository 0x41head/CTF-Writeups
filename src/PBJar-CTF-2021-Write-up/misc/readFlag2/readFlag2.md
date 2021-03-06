# Problem Statement:
![rf2](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/readFlag2/ques.png)

## Solution:

To retrive this flag, I took the same approach as I did with [readFlag1](https://0x41head.github.io/CTF-Writeups/book/PBJar-CTF-2021-Write-up/misc/readFlag1/readFlag1.html) and
looked into the contract source code in the Ropsten network https://ropsten.etherscan.io/address/0x585C403bC5c7eb62BF3630c7FeF1F837603bA866

However this time, as stated in the question, I was greeted with neither the source code nor the ABI just the bytecode.

![rf2-2](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/readFlag2/bytecode.png)

The challenge however explicitly stated that `the ABI of the smart contract is same as the previous one`.

So, to interact with the contract I decided to use https://mycrypto.com

![rf2-3](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/readFlag2/flag.png)

and I got the flag! 

### Notes:
**Always look at the numbering of the questions**

As more people had solved readFlag3 than readFlag2, the ordering of the questions showed readFlag3 before readFlag2. 
Leading me to belive that the question was referring to the ABI of readFlag3. I spent two hours brainstorming on this before realising my 
mistake.

**Double-check your network when using mycrypto**

I spent a good 30 minutes trying to understand why the get function was not retriving anything, before realising that I was in the Ethereum Mainnet

### Reference:
https://chowdera.com/2021/09/20210901002857800n.html
### Tags:
`Misc` , `Blockchain`
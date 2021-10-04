# Problem Statement:
![owner](https://user-images.githubusercontent.com/53595853/133981817-470e2197-cc00-4af4-9ce2-12269b603c2a.png)

## Solution:

The first thing I did was check the url given in the challenge. After the site loaded, it asked me to connect my metamask wallet to it.
After connecting my wallet, the website greeted me with this.

![notowner](https://user-images.githubusercontent.com/53595853/133991228-c331c25f-7047-41f4-b000-d19217219647.png)

Next, I checked out the [contract address of the challenge](https://ropsten.etherscan.io/address/0x850C8db4739F66869757f09752811c4b692F02b8)

The transactions of the contract, contained a few contract owner changes. This meant that I had to somehow become the owner of this contract.

Checking the [Contract source code](https://ropsten.etherscan.io/address/0x850C8db4739F66869757f09752811c4b692F02b8#code) 
I found that I was only able to see the bytecode.

I decided to run this byte code through a [decompiler](https://ropsten.etherscan.io/bytecode-decompiler?a=0x850C8db4739F66869757f09752811c4b692F02b8)

>**Decomiled Code:**

```
def storage:
  unknowna18a186bAddress is addr at storage 0

def unknowna18a186b() payable: 
  return unknowna18a186bAddress

#
#  Regular functions
#

def _fallback() payable: # default function
  revert

def changeOwner(address _newOwnerAddr) payable: 
  require calldata.size - 4 >=′ 32
  require _newOwnerAddr == _newOwnerAddr
  unknowna18a186bAddress = _newOwnerAddr
```

From the decompiled code, I saw that there is a changeOwner function which takes a ethereum wallet address as input.

From here I tried guesing the ABI of the contract from this decompiled code.
After a bit of trial and error, and refrence from [readFlag1](https://github.com/0x41head/PBJar-CTF-2021-Write-up/blob/main/misc/readFlag1.md) and 
[readFlag3](https://github.com/0x41head/PBJar-CTF-2021-Write-up/blob/main/misc/readFlag3.md) I came up with this.

```
[
  {
    "constant": true,
    "inputs": [
      {
        "name": "_newOwnerAddr",
        "type": "address"
      }
    ],
    "name": "changeOwner",
    "outputs": [],
    "payable": false,
    "stateMutability": "nonpayable",
    "type": "function"
  }
]
```

Using this ABI, I attempted to interact with the contract.

![interract with contract](https://user-images.githubusercontent.com/53595853/133996613-08edda66-a62e-4e2b-945a-95a0f2fdbb4a.png)

Success!
The transaction went through which made me the owner of that contract.

I went back to the webpage and retrived the flag.

![falg](https://user-images.githubusercontent.com/53595853/133997002-357aa004-b2a0-48f5-b305-a32a55052eb0.png)


### Notes:

`"stateMutability":"nonpayable"` for write functions

`"stateMutability":"view"` for read functions

This challenge was probably the most difficult one I solved as I had no prior experience coding in blockchain or solidity.

### Reference:

https://www.sitepoint.com/compiling-smart-contracts-abi/

https://ethereum.stackexchange.com/questions/31481/web3-js-can-i-call-a-smart-contract-function-without-knowing-the-abi

### Tags:
`Misc` , `Blockchain`
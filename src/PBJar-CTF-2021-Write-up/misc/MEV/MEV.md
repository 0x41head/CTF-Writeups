# Problem Statement:

![mev](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/MEV/ques.png)

## Solution:

As someone with no prior knowledge about MEVs, it took some research from my part to understand how tipping works in MEVs

```
   1. Bidding gas fees that are above or the same as a target transaction’s to ensure your transaction goes 
      through before or after it; or
   2. Tipping a miner to directly arrange transactions in a mined block to your selection

In the case of #1, you may detect them when seeing one or more failed transactions with either the same or 
very slightly lower gas price used than a successful one right before it. The failed transactions indicate 
a ‘victim’ or other arbitrage bots losing out.

For #2, these can be seen when a mined block has one or more transactions with extremely low gas price such as 0 or 1 gwei.
```

The excerpt from https://beinchain.com/the-rise-of-mev-in-ethereum-technical-view was extremely influential in helping me decipher the flag.

The first thing I did was look into the transactions that were involved in the [block mentioned in the challenge](https://etherscan.io/block/12983883)

Keeping point #2 in mind, I looked for transactions with low gas prices.
The very first transaction in the block had a low gas price of 0.01 gwei.

![gwei](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/MEV/bribe.png)

Looking further into the transaction hash I confirmed that it is a private transaction.

![trans](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/MEV/bribe_details.png)

I then checked the internal transactions to see the exact amount of ether that was sent to the miner of the block `0xb7e390864a90b7b923c9f9310c6f98aafe43f707`

![internaltx](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/PBJar-CTF-2021-Write-up/misc/MEV/flag.png)

I discovered the bribe, and more importantly the flag!

### Notes:
### Reference:
https://ethereum.org/en/developers/docs/mev/

https://beinchain.com/the-rise-of-mev-in-ethereum-technical-view

### Tags:
`Misc` , `Blockchain`
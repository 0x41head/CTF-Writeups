# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Log%20Analysis/Backup%20Policy/ques.png)

## Solution:

This challenge came along with `more.7z` file which when extracted gave me `more.log`.

Similar to [Ingress](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Log%20Analysis/Ingress/Ingress.html) and [Investigation](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Log%20Analysis/Investigation/Investigation.html),I tried usign grep to find specific words in the log
```
$ strings more.log | grep -i 'pass'
2021-08-03 08:55:00 45.85.1.176 GET ../..//passwords.bckp - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 27
2021-08-03 08:55:00 45.85.1.176 GET archives/passwords.txt - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 21
2021-08-03 08:55:00 45.85.1.176 GET passwords.tgz - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 21
2021-08-03 08:55:00 45.85.1.176 GET backup/passwords.old - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:00 45.85.1.176 GET 2/passwords.archived - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 24
2021-08-03 08:55:00 45.85.1.176 GET 4/passwords.copy - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 24
2021-08-03 08:55:00 45.85.1.176 GET 2/passwords.7z - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 26
2021-08-03 08:55:00 45.85.1.176 GET 4/passwords.7z - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 20
2021-08-03 08:55:00 45.85.1.176 GET 1/passwords.archived - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 28
2021-08-03 08:55:00 45.85.1.176 GET 1/passwords.archived - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 21
2021-08-03 08:55:08 45.85.1.176 GET 3/passwords.txt - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:08 45.85.1.176 GET 3/passwords.tgz - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 29
2021-08-03 08:55:08 45.85.1.176 GET passwords.backup - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 28
2021-08-03 08:55:08 45.85.1.176 GET 4/passwords.zip - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 24
2021-08-03 08:55:08 45.85.1.176 GET ../../..//passwords.tgz - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 21
2021-08-03 08:55:08 45.85.1.176 GET old/passwords.txt - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 20
2021-08-03 08:55:08 45.85.1.176 GET 2/passwords.copy.copy - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:08 45.85.1.176 GET backup/passwords.copy - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 30
2021-08-03 08:55:08 45.85.1.176 GET 2/passwords.backup - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:08 45.85.1.176 GET backup/passwords.2 - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 27
2021-08-03 08:55:08 45.85.1.176 GET backup/passwords.7z - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 26
2021-08-03 08:55:08 45.85.1.176 GET 1/passwords.copy - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:08 45.85.1.176 GET ../../..//passwords.old - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 29
2021-08-03 08:55:08 45.85.1.176 GET passwords.zip - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 30
2021-08-03 08:55:08 45.85.1.176 GET archives/passwords.zip - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 26
2021-08-03 08:55:08 45.85.1.176 GET ../../..//passwords.txt - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 27
2021-08-03 08:55:08 45.85.1.176 GET archives/passwords.2 - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 21
2021-08-03 08:55:08 45.85.1.176 GET 4/passwords.old - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 25
2021-08-03 08:55:08 45.85.1.176 GET ../../..//passwords.7z - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 21
2021-08-03 08:55:08 45.85.1.176 GET 1/passwords.archived - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:08 45.85.1.176 GET passwords.old - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 25
2021-08-03 08:55:08 45.85.1.176 GET admin/passwords.old - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 23
2021-08-03 08:55:08 45.85.1.176 GET admin/passwords.1 - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 29
2021-08-03 08:55:08 45.85.1.176 GET 4/passwords.3 - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 29
2021-08-03 08:55:08 45.85.1.176 GET passwords.3 - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 404 0 0 28


```
The line numbers in the above output made me believe that the log of the attack was present in one big cluster.

After some trial and error and messing around a bit I found out that he attack took place from line 12630 to line 13193

The question states that I needed to find if the attacker got a backup. We can see that most of the time the attacker was getting back the
404 HTTP resopnse. 

So taking all of that into consideration, I first output the required part of the log into a seperate file.
```
$ strings more.log | grep -n  'old/.htaccess.saved' -B0 -A563  >out.txt
```

Then I gused grep on the file to find all the logs that returned 200 Status code
```
strings out.txt| grep -i ' - 200 '
12752-2021-08-03 08:55:00 45.85.1.176 GET backup.zip - 443 - 200.13.84.124 Mozilla/5.0+(Windows+NT+5.1;+RE97czNjcjN0X19fYWdlbnR9;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/60.0.3112.90+Safari/537.36 - 200 0 0 25
```
Here, I found a base64 string
Decoding that gave me the flag
```
DO{s3cr3t___agent}
```
### Notes:
### Reference:
https://www.joeldare.com/wiki/linux:grep_a_range_of_lines
### Tags:
`Log` `Analysis` 
# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Log%20Analysis/Investigation/ques.png)

## Solution:

This challenge came along with `more.7z` file which when extracted gave me `more.log`.

Similar to [Ingress](https://0x41head.github.io/CTF-Writeups/book/DOA2021ctf/Log%20Analysis/Ingress/Ingress.html),I tried usign grep to find specific words in the log
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
Since the flag was the attacker IP I tried using `DO{200.13.84.124}` as a flag, but to no avail.

I couldn't really find anything else in the log file, so after trying for 45 minutes straight I pinged the creator of this challenge for a flag check. That's when he told me the IP was looking at was the target IP and not the attacker's IP

The attacker's IP was `45.85.1.176` and the flag was `DO{45.85.1.176}`

### Notes:
### Reference:
https://www.joeldare.com/wiki/linux:grep_a_range_of_lines
### Tags:
`Log` `Analysis` 
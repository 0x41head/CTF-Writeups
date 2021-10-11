# Problem Statement:
![q3](https://raw.githubusercontent.com/0x41head/CTF-Writeups/main/src/DeconstruCT.F/Forensics/TegRads/1.png)

## Solution:
In the challenge we are give a `pdf` file.

Opening it we see a chunk of text along with a black box.

 ![13](https://user-images.githubusercontent.com/53595853/135743082-754eb6de-c50e-44dd-9e88-4cec9dc03a1a.png)

Doing a select all and copy on this pdf, I got:
```
dsc{f0r3n51x_15_fun}
dsc{n0t_h3r3_31th3r}1
dsc{n1c3_try}
1 dsc{f00t_n0t3} would just be too obvious
```
None of these look like the flag.

I then decided to check the metadata of the pdf using exifdata
```
$ exiftool fdp.pdf
ExifTool Version Number         : 11.88
File Name                       : fdp.pdf
Directory                       : .
File Size                       : 48 kB
File Modification Date/Time     : 2021:10:01 20:10:46+05:30
File Access Date/Time           : 2021:10:01 20:10:46+05:30
File Inode Change Date/Time     : 2021:10:01 20:10:50+05:30
File Permissions                : rw-rw-r--
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.4
Linearized                      : No
Warning                         : Invalid xref table

```
There seems to be some invalid xref data.
I was not sure what it meant so I continued looking into the pdf a bit more.
Next I checked for all strings inside the pdf.

```
$ strings fdp.pdf
%PDF-1.4
%QDF-1.0
%% Original object ID: 8 0
1 0 obj
  /Metadata 3 0 R
  /Pages 5 0 R
  /Type /Catalog
endobj
%% Original object ID: 1 0
2 0 obj
  /Author (Leplin)
  /Keywords (third section should be right here)
  /Producer (YjRubjNkfQ==)
  /Subject (third section closeby)
  /Title (dscpdf challenge)
  /Creator (alexa)
endobj
%% Original object ID: 13 0
3 0 obj
  /Subtype /XML
  /Type /Metadata
  /Length 4 0 R
stream
<?xpacket begin='
' id='W5M0MpCehiHzreSzNTczkc9d'?>
<x:xmpmeta xmlns:x='adobe:ns:meta/' x:xmptk='Image::ExifTool 12.30'>
<rdf:RDF xmlns:rdf='http://www.w3.org/1999/02/22-rdf-syntax-ns#'>
 <rdf:Description rdf:about=''
  xmlns:dc='http://purl.org/dc/elements/1.1/'>
  <dc:subject>
   <rdf:Bag>
    <rdf:li>third section closeby</rdf:li>
   </rdf:Bag>
  </dc:subject>
  <dc:title>
   <rdf:Alt>
    <rdf:li xml:lang='x-default'>dscpdf challenge</rdf:li>
   </rdf:Alt>
  </dc:title>
 </rdf:Description>
 <rdf:Description rdf:about=''
  xmlns:pdf='http://ns.adobe.com/pdf/1.3/'>
  <pdf:Author>Leplin</pdf:Author>
  <pdf:Keywords>110000 1100110 1011111</pdf:Keywords>
 </rdf:Description>
</rdf:RDF>
</x:xmpmeta>
% Here's the first part of the flag:
% DONT ESCAPE FROM JAVASCRIPT
% `%64%73%63%7B%70%75%62%6C%31%63_`
<?xpacket end='w'?>
endstream
endobj
%QDF: ignore_newline
4 0 obj
3153
endobj
%% Original object ID: 7 0
5 0 obj
  /Count 1
  /Kids [
    6 0 R
  /Type /Pages
endobj
%% Page 1
%% Original object ID: 2 0
6 0 obj
  /Contents 7 0 R
  /MediaBox [
    0
    0
    612
    792
  /Parent 5 0 R
  /Resources <<
    /ExtGState <<
      /G3 9 0 R
      /G5 10 0 R
    >>
    /Font <<
      /F4 11 0 R
    >>
    /ProcSet [
      /PDF
      /Text
      /ImageB
      /ImageC
      /ImageI
    ]
  >>
  /StructParents 0
  /Type /Page
endobj
%% Contents for page 1
%% Original object ID: 6 0
7 0 obj
  /Length 8 0 R
stream
1 0 0 -1 0 792 cm
0 0 612 792 re
W* n
.75 0 0 .75 0 0 cm
1 1 1 RG 1 1 1 rg
/G3 gs
0 0 816 1056 re
0 0 612 792 re
W* n
.75 0 0 .75 72 72 cm
/G3 gs
0 0 145.057114 16.865234 re
0 0 612 72 re
W* n
.75 0 0 .75 72 36 cm
/G3 gs
/F4 6.6666665 Tf
1 0 0 -1 0 .21809912 Tm
0 -6.0351563 Td <0047> Tj
3.701889 0 Td <0056> Tj
3.328125 0 Td <0046> Tj
3.328125 0 Td <005e> Tj
2.2230835 0 Td <0049> Tj
1.8493195 0 Td <0013> Tj
3.701889 0 Td <0055> Tj
2.2165833 0 Td <0016> Tj
3.701889 0 Td <0051> Tj
3.701889 0 Td <0018> Tj
3.701889 0 Td <0014> Tj
3.701889 0 Td <005b> Tj
3.328125 0 Td <0042> Tj
3.701889 0 Td <0014> Tj
3.701889 0 Td <0018> Tj
3.701889 0 Td <0042> Tj
3.701889 0 Td <0049> Tj
1.8493195 0 Td <0058> Tj
3.701889 0 Td <0051> Tj
3.701889 0 Td <0060> Tj
0 0 612 792 re
W* n
.75 0 0 .75 0 72 cm
/G5 gs
96 841.5 m
288 841.5 l
.75 0 0 .75 72 72 cm
/G3 gs
/F4 14.666667 Tf
1 0 0 -1 0 .47981739 Tm
0 -13.2773438 Td <0047> Tj
8.1511078 0 Td <0056> Tj
7.328125 0 Td <0046> Tj
7.328125 0 Td <005e> Tj
4.8949585 0 Td <0051> Tj
8.1511078 0 Td <0013> Tj
8.1511078 0 Td <0057> Tj
4.0719757 0 Td <0042> Tj
8.1511078 0 Td <004b> Tj
8.1511078 0 Td <0016> Tj
8.1511078 0 Td <0055> Tj
4.8806458 0 Td <0016> Tj
8.1511078 0 Td <0042> Tj
8.1511078 0 Td <0016> Tj
8.1511078 0 Td <0014> Tj
8.1511078 0 Td <0057> Tj
4.0719757 0 Td <004b> Tj
8.1511078 0 Td <0016> Tj
8.1511078 0 Td <0055> Tj
4.8806458 0 Td <0060> Tj
.5961 0 0 RG .5961 0 0 rg
/F4 8.8000002 Tf
1 0 0 -1 140.164703 .22522783 Tm
0 -7.9664063 Td <0014> Tj
.75 0 0 .75 72 377.47156 cm
1 1 1 RG 1 1 1 rg
/G3 gs
/F4 14.666667 Tf
1 0 0 -1 0 .47981739 Tm
0 -13.2773438 Td <0047> Tj
8.1511078 0 Td <0056> Tj
7.328125 0 Td <0046> Tj
7.328125 0 Td <005e> Tj
4.8949585 0 Td <0051> Tj
8.1511078 0 Td <0014> Tj
8.1511078 0 Td <0046> Tj
7.328125 0 Td <0016> Tj
8.1511078 0 Td <0042> Tj
8.1511078 0 Td <0057> Tj
4.0719757 0 Td <0055> Tj
4.8806458 0 Td <005c> Tj
7.328125 0 Td <0060> Tj
.75 0 0 .75 72 708.50098 cm
/G3 gs
/F4 8 Tf
1 0 0 -1 0 .20475245 Tm
0 -7.2421875 Td <0014> Tj
/F4 13.333333 Tf
1 0 0 -1 8.1522064 .43619823 Tm
0 -12.0703125 Td <0047> Tj
7.4124756 0 Td <0056> Tj
6.6640625 0 Td <0046> Tj
6.6640625 0 Td <005e> Tj
4.4513855 0 Td <0049> Tj
3.7029877 0 Td <0013> Tj
7.4124756 0 Td <0013> Tj
7.4124756 0 Td <0057> Tj
3.7029877 0 Td <0042> Tj
7.4124756 0 Td <0051> Tj
7.4124756 0 Td <0013> Tj
7.4124756 0 Td <0057> Tj
3.7029877 0 Td <0016> Tj
7.4124756 0 Td <0060> Tj
4.4513855 0 Td <0003> Tj
3.7029877 0 Td <005a> Tj
9.6251526 0 Td <0052> Tj
7.4124756 0 Td <0058> Tj
7.4124756 0 Td <004f> Tj
2.9610901 0 Td <0047> Tj
7.4124756 0 Td <0003> Tj
3.7029877 0 Td <004d> Tj
2.9610901 0 Td <0058> Tj
7.4124756 0 Td <0056> Tj
6.6640625 0 Td <0057> Tj
3.7029877 0 Td <0003> Tj
3.7029877 0 Td <0045> Tj
7.4124756 0 Td <0048> Tj
7.4124756 0 Td <0003> Tj
3.7029877 0 Td <0057> Tj
3.7029877 0 Td <0052> Tj
7.4124756 0 Td <0052> Tj
7.4124756 0 Td <0003> Tj
3.7029877 0 Td <0052> Tj
7.4124756 0 Td <0045> Tj
7.4124756 0 Td <0059> Tj
6.6640625 0 Td <004c> Tj
2.9610901 0 Td <0052> Tj
7.4124756 0 Td <0058> Tj
7.4124756 0 Td <0056> Tj
endstream
endobj
8 0 obj
3137
endobj
%% Original object ID: 3 0
9 0 obj
  /BM /Normal
  /ca 1
endobj
%% Original object ID: 5 0
10 0 obj
  /BM /Normal
  /CA 1
  /LC 0
  /LJ 0
  /LW 1
  /ML 10
  /SA true
  /ca 1
endobj
%% Original object ID: 4 0
11 0 obj
  /BaseFont /ArialMT
  /DescendantFonts [
    12 0 R
  /Encoding /Identity-H
  /Subtype /Type0
  /ToUnicode 13 0 R
  /Type /Font
endobj
%% Original object ID: 11 0
12 0 obj
  /BaseFont /ArialMT
  /CIDSystemInfo <<
    /Ordering (Identity)
    /Registry (Adobe)
    /Supplement 0
  >>
  /CIDToGIDMap /Identity
  /DW 0
  /FontDescriptor 15 0 R
  /Subtype /CIDFontType2
  /Type /Font
  /W [
    0
    [
      750
      0
      0
      277.83203
    ]
    19
    69
    556.15234
    70
    [
      500
      556.15234
      556.15234
      277.83203
      0
      556.15234
    ]
    76
    79
    222.16797
    81
    82
    556.15234
    85
    [
      333.00781
      500
      277.83203
      556.15234
      500
      722.16797
      500
      500
      0
      333.98438
      0
      333.98438
    ]
endobj
// There are 5 pieces to the puzzle
%% Original object ID: 12 0
13 0 obj
  /Length 14 0 R
stream
/CIDInit /ProcSet findresource begin
12 dict begin
begincmap
/CIDSystemInfo
<<  /Registry (Adobe)
/Ordering (UCS)
/Supplement 0
>> def
/CMapName /Adobe-Identity-UCS def
/CMapType 2 def
1 begincodespacerange
<0000> <FFFF>
endcodespacerange
7 beginbfchar
<0003> <0020>
<0016> <0033>
<0018> <0035>
<0042> <005F>
<004F> <006C>
<005E> <007B>
<0060> <007D>
endbfchar
5 beginbfrange
<0013> <0014> <0030>
<0045> <0049> <0062>
<004B> <004D> <0068>
<0051> <0052> <006E>
<0055> <005C> <0072>
endbfrange
endcmap
CMapName currentdict /CMap defineresource pop
endstream
endobj
%QDF: ignore_newline
14 0 obj
endobj
%% Original object ID: 10 0
15 0 obj
  /Ascent 905.27344
  /CapHeight 715.82031
  /Descent -211.91406
  /Flags 4
  /FontBBox [
    -664.55078
    -324.70703
    2000
    1005.85938
  /FontFile2 16 0 R
  /FontName /ArialMT
  /ItalicAngle 0
  /StemV 45.898438
  /Type /FontDescriptor
endobj
%% Original object ID: 9 0
16 0 obj
  /Length1 28596
  /Length 17 0 R
stream
0GDEF
^GPOS
GSUB
0OS/2x
`VDMXP
cmap
cvt 
Tfpgm
ngasp
glyf
hdmx
        hhead
6hhea
$hmtxi/
loca2
maxp
 name
Dpost
 prep%
arab
 cyrl
 grek
 hebr
 latn
MONO
cyrl
,grek
 latn
kern
kern
kern
q       )       )
@CUTA@?>=<;:987543210/.-,+*)('&%$#"! 
,E#F` 
&#HH-,E#F#a 
&#HH-,E#F`
&#HH-,E#F#a
&#HH-,E#F`
&#HH-,E#F#a
&#HH-,
<-, E# 
ZQX# 
D#Y 
QX# 
MD#Y 
QX# 
D#Y!!-,  E
E`D-,
C#Ce
#D-, E
%Ead
PQXED
!!Y-,
Cc#b
+-, E
C`D-,
-, i
d#da\X
aY-,E
#D-,
-,-,
H-,KS \X
Y-, 
#DEe#E 
%`j 
        #B#h
j`a 
TX#!
#YaD
TX#!
#YaD-,
C#Ce
C#Ce
C#Ce
-,KRXED
!!Y-,
!!!!!Y
dQXEi
!!!Y-,
<-, 
**-,
**-,5-,v
aY:/
-,!!
b-,!
@/+Y
`-,!
b`#!-,
Ehe:
-,KS#KQZX E
!!Y-,KTX E
!!Y-,KS#KQZX8
!!Y-,KTX8
!!Y-,
Y-,KT
C\ZX8
!!Y-,
d#dad
`H F
!!Y-,
d#dad
`H F
!!Y-,KS#KQZX
!!Y-,KS#KQZX
!!Y-,KS#KQZ
C\ZX8
!!Y-,
C\ZX8
!!Y-,KRX
%Ia 
TX! C
@TX C
8YYYY!!!!-,F#F`
F# F
pE` 
C`BY
C`BY
C`BY
C`BY
C`BY
C`BYYYYY-,
CTXKS#KQZX8
!!!!Y-

%"%%
%!/ !
*&**
*%5$%
.*..
.);*'
3.33
3-A--
8288
81G11
jl2@
\]2@
WY2@
MQ2@
DI2@
142@
.B2@
',2@
@&CI2@ CI2@&:=2@ :=2
2@&z
2@ z
2@&lv2@ lv2@&dj2@ dj2@&Z_2@ Z_2@&OT2@ OT2
@+)*
AB2@
 "2@
*?2@
.:2oAH
9FD>
9FD>
9FD>
9FD>
9F`D>
9F`D+++++++++++
+++++++++++
2KSX
S \X
EDYX
>DYYK
VS \X
EDYX
 ERX
DYYK
S \X
EDYX
%ERX
%               DYYK
S \X
s$ED
$$EDYX
sERX
 DYYK
S \X
%%EDYX
DYYK
>S \X
EDYX
DYYK
VS \X
EDYX
DYYK
S \X
EDYX
DYY+++++++++++++++++++++++++++++++++++++++++eB++
;Yc\Ee#E`#Ee`#E`
cYEe#E 
&`bch 
Y#eD
c#D 
;\Ee#E 
&`bch 
\#eD
\ETX
\@eD
;@;E#aDY
GP47Ee#E`#Ee`#E`
4PEe#E 
&`bch 
P#eD
4#D 
G7Ee#E 
&`bch 
7#eD
7ETX
7@eD
G@GE#aDY
BYC\X
-A-A
+tusu
EiDEiDEiDsssstustu++++tu+++++sssssssssssssssssssssssss+++E
@aDst
?QZX
@`DY
?QZX
:QZX
@`DY
<QZX
`DY++++++++++++++++++u+++++++C\X
C\ZX
s++++++++ssss+++++
++++++
EiDsEiDsEiDstuEiDsEiDEiDEiDstEiDEiDs+++++s+
+s+tu++++++++++++++stus+stustu+++t++
CTX@
/+++
CTX@
/+++
/+++
s       @!#40
@ !#4 
+++]+
++]q+
88888
888YY+++++++++
#"'&
~|J]
!#40
!#40
]q++
+++++++]q+<M
++++++!#
56673
CTX@
U&/+
+210
s_ o 
s&@!#40&
!#4 
+]q+
32654&#"
32654&#"
'6632
#"&V
@!#40
!#4 
+]q+
8888
q]++Y++++++++++++++++
32654&#"
#"&U
++++++++++]qr<M
++++
++++++++]q
32654&#"
CTX@4
/++++
]210
+++++]q
++++++++]rKS#KQZX
++++++
&&#"
++++++]q++M
+++++++++++]q<
#"&&54
32654&#"
@       '*4
@$*4
++++++++]+M
q++++M
9/]<
]+++
!&'&#"
+++++++++++]++<
??<<<
910Cy@
#535476632
82RD
qk4FW
%       @364
@)464
++++++++]q+<
+++<
++++++++++++]q+
910Cy@
4&#"
BU      6
++++++++]qr<
??<?
9910
]rq+++++++++++++++++++++++++
++++++++]q<M
<10Cy@
]+++++++++++++
3265
+++++++++]qr++<
??10
]qr++++++++++++++++++3
@364
@,464
]q++++++++++<
+++<
]q+++++++++++++
+++<
?<??
910Cy@
+]q3
4&&#"
*kHs
EpM2}
$%40
@$%4
+++]+++++++++
+]]++++++++++
qC\X@   S
++++
7632
32654&#"
++++++++]q+<
6632
>i?[^>BB;^
'G?`r
":      J       D$V"e"|
'&$'$)6$Z
d&d(t#t$
@!'*4`2
BU $
+++++++
++++
+++++q+M
++++++++++
+++?
9/++]qr+
]qr+
910Cy@@'-
++++*+
+++++++++]q
]rq]
+++++++++
32654'&'.
54676632
&&#"
#"&?
{|x5%
OA8*
si|j
kreD=#
NGy(
+H{g
R\R7#
$3A|\Z
#&4
@S#&4
E       E`
+++++++++]q
+++<
]+++++++%
#"&&5
L<bl,
@364
@'464
+++++++]q+
]q+++++++++++<
??<99
910Cy@
+++!5
#"&&'&5
32665
HmO5s
1GQS
CTX@
@       "%4
@~(.4
 (.4
CTX@
@@@
q]++++++++++++
++++++++!
goTv
?????
++++++
CTX@
?????
99/+
U@      O
88888888YK
88YK
3QZX
88YK
8888888888YK
888YY10
9+++Y+++++]qr+++
+++q]
+++++++++
+++++++++++++++++++++++++++!
CTX@
????
CTX@
?<?<
99++
<Y10
"!9     @
9++++++++Y]q
+]++
]Y++++3
6773
G0B3
CTX@
 (04
 (04
CTX@
88YY10
9++++Y]q++
]Y++++++++++++++
32676767
;,<H
lA$0|V4
{@MG
*':&
i+ph
910++++
7633
#"'.
&&'9Ma 
        1H8&V8
W]nc
8b,@T
N5Tf=
Ekt-.
910++++
##5326547667&&54'&&##532
rMa 
        1H8&V8
`Xs^
8b,@T
5Ue=
endstream
endobj
%QDF: ignore_newline
17 0 obj
28596
endobj
xref
0 18
0000000000 65535 f
0000000052 00000 n
0000000151 00000 n
0000000368 00000 n
0000003632 00000 n
0000003680 00000 n
0000003789 00000 n
0000004176 00000 n
0000007368 00000 n
0000007416 00000 n
0000007487 00000 n
0000007611 00000 n
0000007795 00000 n
0000008481 00000 n
0000009113 00000 n
0000009162 00000 n
0000009461 00000 n
0000038153 00000 n
trailer <<
  /Info 2 0 R
  /Root 1 0 R
  /Size 18
  /ID [<314a855fe6d0acdead15d0318f8ddab2><314a855fe6d0acdead15d0318f8ddab2>]
startxref
38176
%%EOF
% Now you prolly tried ctrl+f but i wouldnt make it that easy, here ya go for slice #2 - (23958575899).toString(35) + String.fromCharCode(0x5F)
sk1/UT
Vaux
sk1/p4.txtUT
Vaux
R;l#up
n$M5d
sk1/UT
Vaux
sk1/p4.txtUT
Vaux

```

There seemed to be alot of useful stuff here.

For starters, and the end of the file there seems to be some JS code
Putting this code into a compiler online I got,

`d15pl4y_`

Next, at the top I saw what looked like a base64 string.

`  /Producer (YjRubjNkfQ==)`

decrypting it I got, what looks like the end of the flag

`b4nn3d}`

The line above ` /Producer (YjRubjNkfQ==)` said  `/Keywords (third section should be right here)`

So, I searched for all lines containg the word `keyword`

```
$ strings fdp.pdf| grep -i 'keyword'
  /Keywords (third section should be right here)
  <pdf:Keywords>110000 1100110 1011111</pdf:Keywords>

```
Here, I found a string in binary.

Converting it into ascii I got,

`0f_`

Looking further into the block of strings I also found this piece of text which looked like hex:

```
% Here's the first part of the flag:
% DONT ESCAPE FROM JAVASCRIPT
% `%64%73%63%7B%70%75%62%6C%31%63_`
```

Decrypting this to ascii I got
`
dsc{publ1c`

So far I had found four pieces of the flag.
However, the question stated that there were five pieces of the flag.

`// There are 5 pieces to the puzzle`

I noticed a common pattern between all strings I had already found. 
This was the fact that all the strings had a number indicating what part of the flag they belonged to.

Taking this theory into account,I started searching for the fourth part of the flag.

```
$ strings fdp.pdf| grep -i 'fourth' 
$ strings fdp.pdf| grep -i 'four' 
$ strings fdp.pdf| grep -i '4'   
%PDF-1.4
  /Length 4 0 R
% `%64%73%63%7B%70%75%62%6C%31%63_`
4 0 obj
      /F4 11 0 R
0 0 145.057114 16.865234 re
/F4 6.6666665 Tf
0 -6.0351563 Td <0047> Tj
3.328125 0 Td <0046> Tj
2.2230835 0 Td <0049> Tj
1.8493195 0 Td <0013> Tj
3.701889 0 Td <0014> Tj
3.328125 0 Td <0042> Tj
3.701889 0 Td <0014> Tj
3.701889 0 Td <0042> Tj
3.701889 0 Td <0049> Tj
1.8493195 0 Td <0058> Tj
96 841.5 m
288 841.5 l
/F4 14.666667 Tf
1 0 0 -1 0 .47981739 Tm
0 -13.2773438 Td <0047> Tj
7.328125 0 Td <0046> Tj
4.8949585 0 Td <0051> Tj
4.0719757 0 Td <0042> Tj
8.1511078 0 Td <004b> Tj
4.8806458 0 Td <0016> Tj
8.1511078 0 Td <0042> Tj
8.1511078 0 Td <0014> Tj
4.0719757 0 Td <004b> Tj
4.8806458 0 Td <0060> Tj
/F4 8.8000002 Tf
1 0 0 -1 140.164703 .22522783 Tm
0 -7.9664063 Td <0014> Tj
.75 0 0 .75 72 377.47156 cm
/F4 14.666667 Tf
1 0 0 -1 0 .47981739 Tm
0 -13.2773438 Td <0047> Tj
7.328125 0 Td <0046> Tj
4.8949585 0 Td <0051> Tj
8.1511078 0 Td <0014> Tj
8.1511078 0 Td <0046> Tj
8.1511078 0 Td <0042> Tj
4.0719757 0 Td <0055> Tj
4.8806458 0 Td <005c> Tj
/F4 8 Tf
1 0 0 -1 0 .20475245 Tm
0 -7.2421875 Td <0014> Tj
/F4 13.333333 Tf
1 0 0 -1 8.1522064 .43619823 Tm
0 -12.0703125 Td <0047> Tj
7.4124756 0 Td <0056> Tj
6.6640625 0 Td <0046> Tj
6.6640625 0 Td <005e> Tj
4.4513855 0 Td <0049> Tj
7.4124756 0 Td <0013> Tj
7.4124756 0 Td <0057> Tj
3.7029877 0 Td <0042> Tj
7.4124756 0 Td <0051> Tj
7.4124756 0 Td <0013> Tj
7.4124756 0 Td <0057> Tj
7.4124756 0 Td <0060> Tj
4.4513855 0 Td <0003> Tj
7.4124756 0 Td <0058> Tj
7.4124756 0 Td <004f> Tj
2.9610901 0 Td <0047> Tj
7.4124756 0 Td <0003> Tj
3.7029877 0 Td <004d> Tj
7.4124756 0 Td <0056> Tj
6.6640625 0 Td <0057> Tj
3.7029877 0 Td <0045> Tj
7.4124756 0 Td <0048> Tj
7.4124756 0 Td <0003> Tj
7.4124756 0 Td <0052> Tj
7.4124756 0 Td <0003> Tj
7.4124756 0 Td <0045> Tj
7.4124756 0 Td <0059> Tj
6.6640625 0 Td <004c> Tj
7.4124756 0 Td <0058> Tj
7.4124756 0 Td <0056> Tj
%% Original object ID: 4 0
    556.15234
      556.15234
      556.15234
      556.15234
    556.15234
      556.15234
      333.98438
      333.98438
  /Length 14 0 R
<0042> <005F>
<004F> <006C>
<0013> <0014> <0030>
<0045> <0049> <0062>
<004B> <004D> <0068>
14 0 obj
  /Ascent 905.27344
  /Descent -211.91406
  /Flags 4
    -664.55078
    -324.70703
  /StemV 45.898438
@CUTA@?>=<;:987543210/.-,+*)('&%$#"! 
142@
GP47Ee#E`#Ee`#E`
4PEe#E 
4#D 
s       @!#40
@ !#4 
!#40
!#40
s&@!#40&
!#4 
32654&#"
32654&#"
@!#40
!#4 
32654&#"
32654&#"
CTX@4
#"&&54
32654&#"
@       '*4
@$*4
#535476632
qk4FW
%       @364
@)464
4&#"
@364
@,464
4&&#"
$%40
@$%4
32654&#"
@!'*4`2
32654'&'.
54676632
#&4
@S#&4
@364
@'464
@       "%4
@~(.4
 (.4
 (04
 (04
lA$0|V4
##5326547667&&54'&&##532
0000004176 00000 n
0000007416 00000 n
0000007487 00000 n
0000008481 00000 n
0000009461 00000 n
  /ID [<314a855fe6d0acdead15d0318f8ddab2><314a855fe6d0acdead15d0318f8ddab2>]
sk1/p4.txtUT
sk1/p4.txtUT
```

At the end of the output of `strings fdp.pdf| grep -i '4'`I found what looked like some text file with the name of `p4`.

So I decided to check for embedded data in the pdf using binwalk.
```
$ binwalk -e fdp.pdf

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PDF document, version: "1.4"
48629         0xBDF5          Zip archive data, at least v1.0 to extract, name: sk1/
48691         0xBE33          Zip archive data, at least v2.0 to extract, compressed size: 95, uncompressed size: 108, name: sk1/p4.txt
49008         0xBF70          End of Zip archive, footer length: 22

```
And found `p4.txt` which had the following text.

```
Caesar wasn't smart enough. He got outsmarted by Brutus lmao.
The key is our creator
The result is fq3gq10n_
```

The keywords that struck out to me immediately were `key` and `Caeser` as the only cipher I knew, that was derived from `Caeser Cipher` and used a `key`, was 
`Vigenère Cipher `.

Decoding this using `alexa` as my key, I got `ff3ct10n_`

Combining everything I found, I retrived the flag.

### Notes:
### Reference:
### Tags:
`Forensics` , `pdf` 
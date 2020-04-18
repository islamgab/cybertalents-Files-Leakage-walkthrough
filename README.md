[{ islamgab }](http://facebook.com/islam.jabir)
### Writeups

## Description
* **Challenge Name:** Files Leakage
* **Points:** 100
* **Level:** medium


## Tools
* GNU strings 2.31.1
* [deepsound2john](https://github.com/magnumripper/JohnTheRipper/blob/bleeding-jumbo/run/deepsound2john.py)
* shntool
* stegolsb wavsteg -r -i
* DeepSound v2.0
* Wireshark 2.6.7 https://www.wireshark.org/docs/relnotes/wireshark-2.6.7.html
* Foremost 1.5.7 http://foremost.sourceforge.net/

## Writeup

***File contents***
```
Pdf Files:

- 3911-Exhibit-AB-20170128-26.pdf
- DarkSeaSkies_1_0_CONOP.pdf
- DarkSeaSkies_1_0_URD.pdf
- deobfuscate.pdf
- Deobfuscation is in NP.pdf
- DerStarke_v1_4_DOC.pdf
- Experiences in Malware Binary Deobfuscation.pdf

Wav File:

- 23329117.WAV
```

All file have marked "E5" Symbole as deleted file from "KINGSTON" USB flash disk


i created a wordlist from all file for challenge

```bash
$ for i in $(ls); do strings $i | awk length"$1<7" >> wordlist_len7.txt; done
```
then i found tool deepsound to john

```bash
$ deepsound2john 23329117_Fixed > hash.txt
$
$ john --wordlist=wordlist_len8.txt hash.txt
$
```

Get Pass *@dh00m@*

and get flag file content this


```
uuuuuuuuuuuuuuuu4zzzzzzzzzzzzzzz
yyyyyyyyycjjjjjjjjjjjjjjjjjjjjjj
ssssssssssssssssssssssssssssssem
iiiiiiiiii9vvvvvvvvvvvvvvvvvvvvv
zzzzzzzzzzzzzzzzzzzzzzzz8zzzzzzz
ooo1wwwwwwwwwwwwwwwwwwwwwwwwwwww
mmmm6ppppppppppppppppppppppppppp
iiiiiiiiiiiiiiiiiiiiicuuuuuuuuuu
rrrrrrrr1yyyyyyyyyyyyyyyyyyyyyyy
sssss6uuuuuuuuuuuuuuuuuuuuuuuuuu
yyyyyyyyyyyyyyyyyyyyyyyfzzzzzzzz
i6zzzzzzzzzzzzzzzzzzzzzzzzzzzzzz
kkkkkk2vvvvvvvvvvvvvvvvvvvvvvvvv
oofiiiiiiiiiiiiiiiiiiiiiiiiiiiii
tttttttttttttttttttttttttessssss
jjjjjjjjjjjjjjjjjjjjjjjjjjjjjcqq
sssssssssss1llllllllllllllllllll
jjjjjjjjjjjjjjjjjjjjjjjjjjjjjjj9
uuuuuuuuuuuuuuuuuuuuuuuuuu8mmmmm
iiiiiii3iiiiiiiiiiiiiiiiiiiiiiii
nnnnnnnnnnnnnnnnnn7rrrrrrrrrrrrr
tttttttttttttttttellllllllllllll
ssssssssssssssssssssssssssscjjjj
ttttttttttttttt5yyyyyyyyyyyyyyyy
oooooooooooooemmmmmmmmmmmmmmmmmm
nnnnnnnnnnnnnnnnnnnnnnammmmmmmmm
fuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu
nnnnnnnnnnnnnnnnnnnnnnnnnnnnakkk
oooooooooooooooooooo0ppppppppppp
nnnnnnnnnnnn2ooooooooooooooooooo
mmmmmmmmmmmmmm8wwwwwwwwwwwwwwwww
jjjjjjjjjjjjjjjjjjj9ssssssssssss
```


i will left here to think where is flag
thanks

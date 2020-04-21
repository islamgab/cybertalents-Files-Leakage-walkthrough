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

***Pcap File contents***
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



that`s a first method for get pass
i created a wordlist from all file for challenge and for pcap also

```bash
$ for i in $(ls); do strings $i | awk length"$1<5" >> wordlist_len5.txt; done
$ for i in $(ls); do strings $i | awk length"$1<6" >> wordlist_len6.txt; done
$ for i in $(ls); do strings $i | awk length"$1<7" >> wordlist_len7.txt; done
$ for i in $(ls); do strings $i | awk length"$1<8" >> wordlist_len8.txt; done
$ for i in $(ls); do strings $i | awk length"$1<9" >> wordlist_len9.txt; done

cat * > wordlist_len5-9.txt


```
then i found tool deepsound to john

```bash
$ deepsound2john 23329117_Fixed > hash.txt
$ john --wordlist=wordlist_len5-9.txt hash.txt # **Make sure that wordlist UTF-8**
```

***Advanced Method to get pass***

first thing take look to https://en.wikipedia.org/wiki/Design_of_the_FAT_file_system

<img src="https://github.com/islamgab/Files_Leakage/blob/master/VFAT_directory_entries.png" width="400">

and look for "VFAT long file names" image up

****All file have marked "E5" Symbole as deleted file from "KINGSTON" USB flash disk****

<img src="https://github.com/islamgab/Files_Leakage/blob/master/01.png" width="400">

****0xe5**** mean file deleted in ****Frame 34**** in ****OFFSET 0290**** this offset Ref for Section in ****Frame 935****

```
filename : @dh00m@.txt
content: @dh00m@
# before deleted from flash memory
filename: [0xe5]dh00m@.txt
contenet : @dh00m@ << content not changed becouse may be want to restore it

```
That's make sense as this is a password


Get Pass **@dh00m@**
and get flag file content this

```
uuuuuuuuuuuuuuuu4zzzzzzzzzzzzzzz
yyyyyyyyycjjjjjjjjjjjjjjjjjjjjjj
ssssssssssssssssssssssssssssssem
iiiiiiiiii9vvvvvvvvvvvvvvvvvvvvv
zzzzzzzzzzzzzzzzzzzzzzzz8zzzzzzz
ooo1wwwwwwwwwwwwwwwwwwwwwwwwwwww
...
...
nnnnnnnnnnnn2ooooooooooooooooooo
mmmmmmmmmmmmmm8wwwwwwwwwwwwwwwww
jjjjjjjjjjjjjjjjjjj9ssssssssssss
```

```
uuuuuuuuuuuuuuuu[4]zzzzzzzzzzzzzzz
yyyyyyyyy[c]jjjjjjjjjjjjjjjjjjjjjj
ssssssssssssssssssssssssssssss[e]m
iiiiiiiiii[9]vvvvvvvvvvvvvvvvvvvvv
zzzzzzzzzzzzzzzzzzzzzzzz[8]zzzzzzz
ooo[1]wwwwwwwwwwwwwwwwwwwwwwwwwwww
mmmm[6]ppppppppppppppppppppppppppp
iiiiiiiiiiiiiiiiiiiiicuuuuuuuuuu
rrrrrrrr1yyyyyyyyyyyyyyyyyyyyyyy
...
...
...
nnnnnnnnnnnn2ooooooooooooooooooo
mmmmmmmmmmmmmm8wwwwwwwwwwwwwwwww
jjjjjjjjjjjjjjjjjjj9ssssssssssss
```
```
f6f166231c912e854e790caf8e8cace9
```

##Flag = f6f166231c912e854e790caf8e8cace9

Thank you

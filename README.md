[{ islamgab }](http://facebook.com/islam.jabir)
### Writeups

**Challenge Name:** Files Leakage

**Category:** Digital Forensics

**Level:** medium

**Points:** 100

**Challenge Description:** A CIA Agent Leaked some files, but can you hear what is beyond the storm ?

**Answer:** To-Do

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

Get Pass *@dhoom@*



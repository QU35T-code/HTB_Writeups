# Shell

We find a `password backup` in `hex`.

```bash
www-data@curling:/home/floris$ cat password_backup 
00000000: 425a 6839 3141 5926 5359 819b bb48 0000  BZh91AY&SY...H..
00000010: 17ff fffc 41cf 05f9 5029 6176 61cc 3a34  ....A...P)ava.:4
00000020: 4edc cccc 6e11 5400 23ab 4025 f802 1960  N...n.T.#.@%...`
00000030: 2018 0ca0 0092 1c7a 8340 0000 0000 0000   ......z.@......
00000040: 0680 6988 3468 6469 89a6 d439 ea68 c800  ..i.4hdi...9.h..
00000050: 000f 51a0 0064 681a 069e a190 0000 0034  ..Q..dh........4
00000060: 6900 0781 3501 6e18 c2d7 8c98 874a 13a0  i...5.n......J..
00000070: 0868 ae19 c02a b0c1 7d79 2ec2 3c7e 9d78  .h...*..}y..<~.x
00000080: f53e 0809 f073 5654 c27a 4886 dfa2 e931  .>...sVT.zH....1
00000090: c856 921b 1221 3385 6046 a2dd c173 0d22  .V...!3.`F...s."
000000a0: b996 6ed4 0cdb 8737 6a3a 58ea 6411 5290  ..n....7j:X.d.R.
000000b0: ad6b b12f 0813 8120 8205 a5f5 2970 c503  .k./... ....)p..
000000c0: 37db ab3b e000 ef85 f439 a414 8850 1843  7..;.....9...P.C
000000d0: 8259 be50 0986 1e48 42d5 13ea 1c2a 098c  .Y.P...HB....*..
000000e0: 8a47 ab1d 20a7 5540 72ff 1772 4538 5090  .G.. .U@r..rE8P.
000000f0: 819b bb48                                ...H
```

Let's reverse the `hex password` with `xxd`.

```bash
www-data@curling:/tmp$ xxd -r password_backup > backup
www-data@curling:/tmp$ file backup 
backup: bzip2 compressed data, block size = 900k
www-data@curling:/tmp$ mv backup backup.bz2
www-data@curling:/tmp$ bzip2 -d backup.bz2
www-data@curling:/tmp$ file backup 
backup: gzip compressed data, was "password", last modified: Tue May 22 19:16:20 2018, from Unix
www-data@curling:/tmp$ mv backup backup.gz
www-data@curling:/tmp$ gzip -d backup.gz
www-data@curling:/tmp$ file backup 
backup: bzip2 compressed data, block size = 900k
www-data@curling:/tmp$ mv backup backup.bz2
www-data@curling:/tmp$ bzip2 -d backup.bz2
www-data@curling:/tmp$ file backup 
backup: POSIX tar archive (GNU)
www-data@curling:/tmp$ mv backup backup.tar
www-data@curling:/tmp$ tar xvf backup.tar 
password.txt
www-data@curling:/tmp$ cat password.txt 
5d<wdCbdZu)|hChXll
```

We can log as `floris`.

```bash
$ su floris
Password: 5d<wdCbdZu)|hChXll
floris@curling:/home$
```

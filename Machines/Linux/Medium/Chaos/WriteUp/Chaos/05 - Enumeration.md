# NMAP

## Tcp

Basic nmap scan.

```sql
# Nmap 7.91 scan initiated Sun May 16 19:10:59 2021 as: nmap -sC -sV -oA nmap/chaos 10.10.10.120
Nmap scan report for 10.10.10.120
Host is up (0.037s latency).
Not shown: 994 closed ports
PORT      STATE SERVICE  VERSION
80/tcp    open  http     Apache httpd 2.4.34 ((Ubuntu))
|_http-server-header: Apache/2.4.34 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
110/tcp   open  pop3     Dovecot pop3d
|_pop3-capabilities: SASL PIPELINING STLS CAPA UIDL RESP-CODES AUTH-RESP-CODE TOP
| ssl-cert: Subject: commonName=chaos
| Subject Alternative Name: DNS:chaos
| Not valid before: 2018-10-28T10:01:49
|_Not valid after:  2028-10-25T10:01:49
|_ssl-date: TLS randomness does not represent time
143/tcp   open  imap     Dovecot imapd (Ubuntu)
|_imap-capabilities: listed have capabilities IMAP4rev1 more LOGINDISABLEDA0001 post-login LOGIN-REFERRALS SASL-IR STARTTLS IDLE OK Pre-login ID LITERAL+ ENABLE
| ssl-cert: Subject: commonName=chaos
| Subject Alternative Name: DNS:chaos
| Not valid before: 2018-10-28T10:01:49
|_Not valid after:  2028-10-25T10:01:49
|_ssl-date: TLS randomness does not represent time
993/tcp   open  ssl/imap Dovecot imapd (Ubuntu)
|_imap-capabilities: listed have capabilities IMAP4rev1 AUTH=PLAINA0001 more LOGIN-REFERRALS post-login IDLE ID OK Pre-login SASL-IR LITERAL+ ENABLE
| ssl-cert: Subject: commonName=chaos
| Subject Alternative Name: DNS:chaos
| Not valid before: 2018-10-28T10:01:49
|_Not valid after:  2028-10-25T10:01:49
|_ssl-date: TLS randomness does not represent time
995/tcp   open  ssl/pop3 Dovecot pop3d
|_pop3-capabilities: USER PIPELINING SASL(PLAIN) CAPA UIDL RESP-CODES AUTH-RESP-CODE TOP
| ssl-cert: Subject: commonName=chaos
| Subject Alternative Name: DNS:chaos
| Not valid before: 2018-10-28T10:01:49
|_Not valid after:  2028-10-25T10:01:49
|_ssl-date: TLS randomness does not represent time
10000/tcp open  http     MiniServ 1.890 (Webmin httpd)
|_http-title: Site doesn't have a title (text/html; Charset=iso-8859-1).
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sun May 16 19:11:43 2021 -- 1 IP address (1 host up) scanned in 44.30 seconds
```

# Gobuster

## Http (80)

We can find `/wp` directory thanks to gobuster command.
It's a  `wordpress CMS` ?

```bash
$ gobuster dir -u http://chaos/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,txt,bak -o gobuster-root.txt
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://chaos/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              php,txt,bak
[+] Timeout:                 10s
===============================================================
2021/05/16 19:24:37 Starting gobuster in directory enumeration mode
===============================================================
/wp                   (Status: 301) [Size: 295] [--> http://chaos/wp/]
/javascript           (Status: 301) [Size: 303] [--> http://chaos/javascript/]
```

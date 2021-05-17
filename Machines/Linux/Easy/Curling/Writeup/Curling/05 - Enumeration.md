# NMAP

## TCP

Basic nmap scan.

```sql
Starting Nmap 7.91 ( https://nmap.org ) at 2021-05-17 13:26 CDT
Nmap scan report for 10.10.10.150
Host is up (0.036s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8a:d1:69:b4:90:20:3e:a7:b6:54:01:eb:68:30:3a:ca (RSA)
|   256 9f:0b:c2:b2:0b:ad:8f:a1:4e:0b:f6:33:79:ef:fb:43 (ECDSA)
|_  256 c1:2a:35:44:30:0c:5b:56:6a:3f:a5:cc:64:66:d9:a9 (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-generator: Joomla! - Open Source Content Management
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Home
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 8.69 seconds
```

# Gobuster

We can emumerate directory and files with gobuster.

```sql
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.10.150
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              php,txt,bak
[+] Timeout:                 10s
===============================================================
2021/05/17 13:28:15 Starting gobuster in directory enumeration mode
===============================================================
/index.php            (Status: 200) [Size: 14264]
/media                (Status: 301) [Size: 312] [--> http://10.10.10.150/media/]
/templates            (Status: 301) [Size: 316] [--> http://10.10.10.150/templates/]
/images               (Status: 301) [Size: 313] [--> http://10.10.10.150/images/]   
/modules              (Status: 301) [Size: 314] [--> http://10.10.10.150/modules/]  
/bin                  (Status: 301) [Size: 310] [--> http://10.10.10.150/bin/]      
/plugins              (Status: 301) [Size: 314] [--> http://10.10.10.150/plugins/]  
/includes             (Status: 301) [Size: 315] [--> http://10.10.10.150/includes/] 
/language             (Status: 301) [Size: 315] [--> http://10.10.10.150/language/] 
/README.txt           (Status: 200) [Size: 4872]                                    
/components           (Status: 301) [Size: 317] [--> http://10.10.10.150/components/]
/cache                (Status: 301) [Size: 312] [--> http://10.10.10.150/cache/]     
/libraries            (Status: 301) [Size: 316] [--> http://10.10.10.150/libraries/] 
/tmp                  (Status: 301) [Size: 310] [--> http://10.10.10.150/tmp/]       
/LICENSE.txt          (Status: 200) [Size: 18092]                                    
/layouts              (Status: 301) [Size: 314] [--> http://10.10.10.150/layouts/]   
/secret.txt           (Status: 200) [Size: 17]                                       
/administrator        (Status: 301) [Size: 320] [--> http://10.10.10.150/administrator/]
/configuration.php    (Status: 200) [Size: 0]
/htaccess.txt         (Status: 200) [Size: 3005]
/cli                  (Status: 301) [Size: 310] [--> http://10.10.10.150/cli/]
```

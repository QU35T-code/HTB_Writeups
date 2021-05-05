# Preview

![[Pasted image 20210505141306.png]]

List of existing pages and folders with gobuster.

```sql
$ gobuster dir -u http://academy.htb/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt,bak -o gobuster/gobuster-root.txt
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://academy.htb/
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              bak,php,html,txt
[+] Timeout:                 10s
===============================================================
2021/05/05 14:16:58 Starting gobuster in directory enumeration mode
===============================================================
/index.php            (Status: 200) [Size: 2117]
/images               (Status: 301) [Size: 311] [--> http://academy.htb/images/]
/home.php             (Status: 302) [Size: 55034] [--> login.php]               
/login.php            (Status: 200) [Size: 2627]                                
/register.php         (Status: 200) [Size: 3003]                                
/admin.php            (Status: 200) [Size: 2633]                                
/config.php           (Status: 200) [Size: 0]
```

We create an account on http://academy.htb/register.php, then we intercept the request and we notice a `roleid` parameter. Let's change it to 1.

![[Pasted image 20210505142433.png]]

Changing the `roleid` parameter create an admin account instead of a user account.
We can connect to the admin page : http://academy.htb/admin.php

![[Pasted image 20210505142225.png]]

We obtain a subdomain name of the website : `dev-staging-01.academy.htb`
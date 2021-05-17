# Attachments

We can find an online tool to decode the message : https://github.com/happygirlzt/Cryptography/blob/master/encrypt.py

```python
#!/usr/bin/env python3

# Knowledge:
# AES: Advanced Encryption Standard
# Symmetric Cipher
# 16 byte block size: each part of the encrypted data is
# encrypted 16 bytes, it must be full, so padding is required.
# The keys can be 128, 192 or 256 bits long
# IV: stands for initialization vector

import os
from Crypto.Cipher import AES
from Crypto.Hash import SHA256
from Crypto import Random

def encrypt(key, filename):
    chunksize = 64*1024
    outputFile = filename + "_enc"
    filesize = str(os.path.getsize(filename)).zfill(16)
    IV = Random.new().read(16)

    encryptor = AES.new(key, AES.MODE_CBC, IV)

    with open(filename, 'rb') as infile:
        with open(outputFile, 'wb') as outfile:
            outfile.write(filesize.encode('utf-8'))
            outfile.write(IV)

            while True:
                chunk = infile.read(chunksize)

                if len(chunk) == 0:
                    break
                elif len(chunk) % 16 != 0:
                    chunk += b' ' * (16 - (len(chunk) % 16))

                outfile.write(encryptor.encrypt(chunk))

def decrypt(key, filename):
    chunksize = 64*1024
    outputFile = filename + "_dec"

    with open(filename, 'rb') as infile:
        filesize = int(infile.read(16))
        IV = infile.read(16)

        decryptor = AES.new(key, AES.MODE_CBC, IV)

        with open(outputFile, 'wb') as outfile:
            while True:
                chunk = infile.read(chunksize)

                if len(chunk) == 0:
                    break

                outfile.write(decryptor.decrypt(chunk))
            outfile.truncate(filesize)

def getKey(password):
    hasher = SHA256.new(password.encode('utf-8'))
    return hasher.digest()

def Main():
    choice = input("Would you like to (E)ncrypt of (D)ecrypt?: ").upper()

    if choice == 'E':
        filename = input("File to encrypt: ")
        password = input("Password: ")
        encrypt(getKey(password), filename)
        print("Done.")

    elif choice == 'D':
        filename = input("File to decrypt: ")
        password = input("Password: ")
        decrypt(getKey(password), filename)
        print("Done.")

    else:
        print("No option selected, closing...")

if __name__ == "__main__":
    Main()
```

Let's run it.

```sql
$ python3 decrypt.py 
Would you like to (E)ncrypt of (D)ecrypt?: D
File to decrypt: msg.txt
Password: sahay
Done.
```

And show the message. He is encoded in `base64` format. I'm using `CyberChef` to decode the message : https://gchq.github.io/CyberChef/

```sql
$ cat msg.txt_dec 
SGlpIFNhaGF5CgpQbGVhc2UgY2hlY2sgb3VyIG5ldyBzZXJ2aWNlIHdoaWNoIGNyZWF0ZSBwZGYKCnAucyAtIEFzIHlvdSB0b2xkIG1lIHRvIGVuY3J5cHQgaW1wb3J0YW50IG1zZywgaSBkaWQgOikKCmh0dHA6Ly9jaGFvcy5odGIvSjAwX3cxbGxfZjFOZF9uMDdIMW45X0gzcjMKClRoYW5rcywKQXl1c2gK
```

![alt text](cyberchef.png)

We find a `pdf` generator page in construction...

http://chaos.htb/J00_w1ll_f1Nd_n07H1n9_H3r3

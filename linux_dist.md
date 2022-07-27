# upgrade routine
```bash
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo reboot
```

# show my release
`lsb_release -a`

# upgrade old release
locate file: `/etc/apt/sources.list`  
old release are at: ` http://old-releases.ubuntu.com`

# release upgrade
`sudo do-release-upgrade`

# legacy release upgrade
http://old-releases.ubuntu.com/ubuntu/dists/  
https://wiki.ubuntu.com/Releases  
https://help.ubuntu.com/community/EOLUpgrades  

```bash
# Downloads the upgrader, check the link above for the URL of the file for your release
wget http://archive.ubuntu.com/ubuntu/dists/focal-updates/main/dist-upgrader-all/current/focal.tar.gz
# Extract it into a new directory
mkdir upgrader
tar -xaf focal.tar.gz -C upgrader
cd upgrader
# Run the executable, the name changes based on the release
 sudo env RELEASE_UPGRADE_MODE=server  ./focal --frontend=DistUpgradeViewText
```

# pip upgrade to other python version
```bash
py3env
wget https://bootstrap.pypa.io/get-pip.py
python get-pip.py
```

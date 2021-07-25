# Raspbian notes

## General
### Check free space
> df -h


## APT

### Install a package with APT
> sudo apt install [name]

### Uninstall a package with APT
> sudo apt remove [name]

### Searching for software
> apt-cache search [name]

### Location of downloaded package files (.deb files) 

> /var/cache/apt/archives

### Remove downloaded package files 

> sudo apt clean

### Update your system's package list
> sudo apt-get update

### Upgrade all your installed packages to their latest versions 
> sudo apt-get full-upgrade

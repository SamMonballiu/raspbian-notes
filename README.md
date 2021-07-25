# raspbian-notes

## Check free space
> df -h

Be aware that downloaded package files (.deb files) are kept in 

> /var/cache/apt/archives

## Remove downloaded package files 

> sudo apt clean

## Update your system's package list
> sudo apt-get update

## Upgrade all your installed packages to their latest versions 
> sudo apt-get full-upgrade

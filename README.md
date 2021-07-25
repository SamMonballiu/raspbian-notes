# Raspbian notes

## config.txt
The Raspberry Pi uses a configuration file instead of the BIOS you would expect to find on a conventional PC. The system configuration parameters, which would traditionally be edited and stored using a BIOS, are stored instead in an optional text file named 
> config.txt

This is read by the GPU before the ARM CPU and Linux are initialised. It must therefore be located on the first (boot) partition of your SD card, alongside bootcode.bin and start.elf. This file is normally accessible as /boot/config.txt from Linux, and must be edited as root. 

There is an 80 character line length limit to entries, any characters past this limit will be ignored.

[source](https://www.raspberrypi.org/documentation/configuration/config-txt/README.md)

## General
### Check free space
```
df -h
```


## APT

### Install a package with APT
```
sudo apt install [name]
```

### Uninstall a package with APT
```
sudo apt remove [name]
```

### Searching for software
```
apt-cache search [name]
```

### Location of downloaded package files (.deb files) 

```
/var/cache/apt/archives
```

### Remove downloaded package files 

```
sudo apt clean
```

### Update your system's package list
```
sudo apt-get update
```

### Upgrade all your installed packages to their latest versions 
```
sudo apt-get full-upgrade
```

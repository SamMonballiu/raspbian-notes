# Raspbian notes

## config.txt
The Raspberry Pi uses a configuration file instead of the BIOS you would expect to find on a conventional PC. The system configuration parameters, which would traditionally be edited and stored using a BIOS, are stored instead in an optional text file named 
> config.txt

This is read by the GPU before the ARM CPU and Linux are initialised. It must therefore be located on the first (boot) partition of your SD card, alongside bootcode.bin and start.elf. This file is normally accessible as /boot/config.txt from Linux, and must be edited as root. 

There is an 80 character line length limit to entries, any characters past this limit will be ignored.

[source](https://www.raspberrypi.org/documentation/configuration/config-txt/README.md)

## General

### Check installed Raspbian version
```
cat /etc/os-release
```

### Pi 4 won't boot without HDMI plugged in
Use sudo raspi-config to set a forced screen resolution. (Choose anything other than monitor default).

The reason is that by default (RPi4), if no screen is connected at boot then a display device is not created. Without a display device the GUI desktop does not start so any program that requires GUI will not start. Other RPi models did not have that issue because they would fall back to composite mode if no HDMI was connected. The RPi4 has composite mode disabled by default so no display device is created.
Setting a resolution mode with raspi-config or the GUI config tool or manual edits to config.txt as mentioned above, will force a display device on boot even without the HDMI connected as long as you don't choose the monitor default setting.

### Check free space
```
df -h
```

### Check disk usage
```
ncdu -x (q to quit)
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

## Samba
### Install
``` 
sudo apt-get install samba samba-common-bin
```

### Edit smb.conf
```
sudo nano /etc/samba/smb.conf
```

```
[nameofshare]
path = /home/pi/
writeable=Yes
create mask=0777
directory mask=0777
public=yes
guest=yes
```

### Restart Samba service
```
sudo systemctl restart smbd
```

## NodeJs
Let’s update our package repository to use the latest version of Node which is Node 16.5.0 by using the setup_16.x script from NodeSource.
```
$ curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
```
In addition to updating your package repository, the setup script that runs in the previous command also invokes a sudo apt update command as one of its final steps.  Once again, the  sudo apt update command does not actually update any software on the system, but will download the latest package lists from the software repositories so that Raspbian will be aware of all new software available along with dependencies.

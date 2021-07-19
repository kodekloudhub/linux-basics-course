# Lab - Linux Runlevels and Filesystem Hierarchy 
     
- Access Hands-On Labs here [Hands-On Labs](https://kodekloud.com/topic/lab-linux-kernel-modules-boot-and-filetypes/)

To run commands that need **`sudo`**(super-user) privilages. Run **`sudo`**
```
$ sudo ls /root
```

To check the **`init process`** (systemd or sysV) used by the system
```
$ sudo ls -l /sbin/init
```

To check **`default systemd target`** (eg. graphical.target or multi-user.target) set in the system
```
$ sudo systemctl get-default
```

To change the systemd target to **`multi-user.target`**
```
$ sudo systemctl set-default multi-user.target
```

To check what type of file is **`firefox.deb`** which is located at /root
```
$ sudo file /root/firefox.deb
```

To check what type of file is **`sample_script.sh`** which is located at /root
```
$ sudo file /root/sample_script.sh
```

You were asked to install a new **`third-party IDE`** in the system. Which directory  is the recommended choice for the installation?
```
Third-party software is usually installed under **`/opt`**
```

Which directory contains the files related to the block devices that can be seen when running the **`lsblk`** command?
```
Block Device or Device Node files are located under **`/dev`** directory
```

What is the name of the **`vendor`** for the **`Ethernet Controller`** used in this system?
```
Use: sudo lshw and lookup the vendor for Ethernet Controller under the network section.   
     $ sudo lshw
```






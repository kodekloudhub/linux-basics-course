# Lab - RPM and YUM

- Access Hands-On Labs here [Hands-On Labs](https://kodekloud.com/topic/lab-yum-and-rpm/)

Which package managers would you use on centos machine
```
Centos makes use of RPM and YUM
```

Use an **`rpm`** command and find out the exact package name for **`wget`** installed in this server
```
$ rpm -qa |grep wget
```

To install a package for **`firefox`** browser that has been downloaded under **`/home/bob`** in the system. Caution: It might fail due to failed dependencies
```
$ sudo rpm -ivh /home/bob/firefox-68.6.0-1.el7.centos.x86_64.rpm
```

To install a package for **`firefox`** browser along with its dependencies
```
$ sudo yum install firefox -y
```

To check how many software repositories are configured for YUM in the system
```
$ sudo yum repolist
```

To check which package provides **`tcpdump`**  command
```
$ sudo yum provides tcpdump
```



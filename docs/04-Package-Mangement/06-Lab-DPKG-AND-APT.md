# Lab - DPKG and APT

- Access Hands-On Labs here [Hands-On Labs](https://kodekloud.com/topic/lab-dpkg-and-apt-2/)

Package managers that you use on a debian based distro
```
Debain distros use dpkg.
```

To install a package for **`firefox`** browser which has been downloaded at /root/firefox.deb. The dependencies might fail.
```
$ sudo dpkg -i /root/firefox.deb
```

To install a package using **`APT`**
```
$ sudo apt install firefox
```

Lets now locate the package to install Chromium browser in the system. Use **`apt search`** functionality to locate the correct package name. The browser has the description of: Chromium web browser, open-source version of Chrome
```
$ sudo apt search chromium-browser
```

To install the **`chromium-browser`**
```
sudo apt install -y chromium-browser
```

To remove the **`firefox`** browser from the system.
```
$ sudo apt remove firefox
```

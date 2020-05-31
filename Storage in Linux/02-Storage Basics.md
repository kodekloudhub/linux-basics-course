# Storage Basics

- In this lecture we will learn about Disk Partitions. 
- We will look at the File Systems such as EXT series and NFS.
- External Storage Devices such as DAS,NAS, and SAN.
- LVM in Action.

  ![Disk](../images/disk.PNG)
  
  #### List all Block devices
  
  - Block devices are special files that refer to or represent a device (which could be anything from a hard drive to a USB drive). So naturally, there are command line tools that help you with your block devices-related work.

     ```
    [~]$ lsblk 
     ```

     ```
     [~]$ ls -l /dev/ | grep "^b"
     ```
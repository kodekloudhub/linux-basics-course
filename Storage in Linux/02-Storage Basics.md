# Storage Basics

- In this lecture we will learn about Disk Partitions. 
- We will look at the File Systems such as EXT series and NFS.
- External Storage Devices such as DAS,NAS, and SAN.
- LVM in Action.

  ![Disk](../images/disk.PNG)
  
  #### List all Block devices
  
  - Block devices are special files that refer to or represent a device (which could be anything from a hard drive to a USB drive). So naturally, there are command line tools that help you with your block devices-related work.
  - Major Number is used to identigy the type of block device, value 8 represent a SCSI device starts with SD.
  - Minor Number is uset to distuinguish individual, physical or logical devices.

     ```
     [~]$ lsblk 
     ```

     ```
     [~]$ ls -l /dev/ | grep "^b"
     ```

  - To Print,Create and Delete the parition table use **`fdisk -l`** command 
 
     ```
     [~]$ sudo fdisk -l /dev/sda
     ```

  #### Partition Types - 
  
  ![Part](../images/partition.PNG)

  - PRIMARY - Use to Boot an Operating System.
  - EXTENDED - Can host logical partitions but cannot be used on its own.
  - LOGICAL - Created within an extended partition.

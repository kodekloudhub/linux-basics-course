# Working with Hardware

In this section, we will look at how linux works with the hardware resources available to the system and how to make use of kernel modules
- We will look at how linux identifies and manages hardware devices attached to the system
- We will then see ways to list and get detailed information about these devices from the command line.

Lets take an example of **`USB Disk`** be used in the system.
- As soon as the **`USB device`** is attached to the system a corresponding device driver which is part of the kernel space detects the stage change and generates an event. 
- This event which is called **`uevents`** is then sent to the **`User Space`** device manager daemon called **`udev`**. 
- The **`udev`** service is then responsible for dynamically creating a device node associated with the newly attached USB drive in the **`/dev/`** filesystem. 
- Once the process is complete, the newly attached disk should be visible under **`/dev/`** filesystem.

![working-with-hardware](../../images/working-with-hardware.PNG)

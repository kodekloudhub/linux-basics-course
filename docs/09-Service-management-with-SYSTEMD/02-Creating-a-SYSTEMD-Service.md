# Creating your own SYSTEMD Service

- Take me to the [Tutorial](https://kodekloud.com/topic/creating-a-systemd-service/)

In this lecture we will learn how to create a SYSTEMD Service.
- All the major distributions, such as Rhel, CentOS, Fedora, Ubuntu, Debian and Archlinux, adopted systemd as their init system.
- Systemd is a Linux initialization system and service manager that includes features like on-demand starting of daemons, mount and automount point maintenance etc.
- Systemd also provides a logging daemon and other tools and utilities to help with common system administration tasks.

#### What is a service unit? 

- A file with the .service suffix contains information about a process which is managed by systemd. It is composed by three main sections:

  #### 1.Unit

  - The **`Unit`** section of a .service file contains the description of the unit itself, and information about its behavior and its dependencies: (to work correctly a service can depend on another one). Here we discuss some of the most relevant options which can be used in this section
  - First of all we have the **`Description`** option. By using this option we can provide a description of the unit. The description will then appear, for example, when calling the systemctl command, which returns an overview of the status of systemd.
  - Secondly, we have **`Documentation`** option. By using this option we can get the details of the service and documentation related to it.
  - By using the **`After`** option, we can state that our unit should be started after the units we provide in the form of a space-separated list.

    ```
    [~]$ cat /etc/systemd/system/project-mercury.service
    [Unit]
    Description=Python Django for Project Mercury
    Documentation=http://wiki.caleston-dev.ca/mercury
    After=postgresql.service
    ```


  #### 2.Service

  - In the **`Service`** section of a service unit, we can specify things as the command to be executed when the service is started, or the type of the service itself.

    ```
    [Service]
    ExecStart=/usr/bin/project-mercury.sh
    User=project_mercury
    Restart=on-failure
    RestartSec=10
    ```

  #### 3.Install

  - This **`Install`** section contains information about the installation of the unit

    ```
    [Install]
    WantedBy=graphical.target
    ```

#### How to Start the Service now ?

- The system to detect the changes you have done in the file, we need to reload the daemon and start the service.

  ```
  [~]$ systemctl daemon-reload

  [~]$ systemctl start project-mercury.service
  ```
# RPM and YUM Package Managers

In this section, we will take a look at **`RPM`** and **`YUM`** package managers in detail.
- RPM
- YUM

## RPM (Redhat Package Manager)

This package manager is used in RHEL as well as other linux distributions but these re the most common ones. The File extensions for packages manage by RPM is **`.RPM`**

[!rpm](../../images/rpm.PNG]

#### Working with RPM

RPM has five basic modes of operations. Each of these modes can be run using **`rpm`** command followed by a specific command **`options`**. Despite of this, RPM doesn't resolve dependencies on its own. This is why we make use of a higher level of package manager called **`YUM`**.
1. Installing
1. Uninstalling
1. Upgrade
1. Query
1. Verfiying

   ![rpm-modes](../../images/rpm-modes.PNG)

## YUM (Yellowdog Updater Modifier)

YUM is a free and opensource package manager.
- Works on RPM based Linux systems
- Works with Software repositories which are essentially a collection of packages and provides package independency management on RPM based distro. The repository information is stored in **`/etc/yum.repos.d/`** and repository files will have the **`.repo`** extension.
- Acts as a high level package manager but under the hood it still depeneds on **`RPM`** to manage packages on the linux systems.
- Unlike RPM, YUM handles package dependencies very well (Automatic Dependency Resolution). It is able to install any dependencies packages to get the base package install on the linux system.

  [!yum](../../images/yum.PNG]





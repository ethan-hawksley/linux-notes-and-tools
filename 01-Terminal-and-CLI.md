Sections 1-12

### 19/03/2026
CentOS Stream & Ubuntu are two major distributions.
CentOS Stream supports SELinux properly unlike Ubuntu, and it is downstream from RHEL.

Using Oracle Virtualbox for virtualisation of the operating system.
For following the course, using Rocky Linux 9 instead of CentOS. It is very similar but more stable and well supported by the Virtualbox custom drivers due to an older kernel version.

### 24/03/2026
epel-release is an additional repository that enables access to more packages on Rocky Linux.

sudo dnf install epel-release
sudo dnf install gcc kernel-devel kernel-headers make bzip2 perl

Installs plenty of packages necessary for compiling and installing the VirtualBox drivers.

### 28/03/2026

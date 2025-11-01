***

# Understanding the Linux File System

This guide provides a quick overview of what the root directory (`/`) in Linux looks like, how to navigate it, and what each folder is used for. It mimics what you’d see in a real terminal environment.

***

## Root Directory Overview

```
user@linux:~$ cd /
user@linux:/$ ls
bin   boot  dev  etc  home  lib  media  mnt  opt  proc  
root  run   sbin  srv  sys  tmp  usr  var
```

The root (`/`) directory is the top of the Linux file system. Everything starts here.

***

## Directory Breakdown

### /bin  — Essential User Commands
```
user@linux:/$ ls bin
bash  cat  cp  ls  mkdir  mv  pwd  rm  nano  tar
```
Stores basic command-line tools and executables needed by all users.  
Examples: shell binaries (`bash`), file management tools (`cp`, `mv`), and utilities (`ls`, `cat`, `pwd`).

***

### /boot  — Boot Files
```
user@linux:/$ ls boot
grub  initrd.img  vmlinuz  System.map
```
Contains the files needed to boot Linux, like the kernel and bootloader configurations.

***

### /dev  — Device Files
```
user@linux:/$ ls dev
sda  sda1  tty  null  random  urandom
```
Each item represents a hardware or system device as a file — disks, terminals, and input/output devices.

***

### /etc  — Configuration Files
```
user@linux:/$ ls etc
passwd  hosts  fstab  ssh  network  systemd
```
Holds configuration files and startup scripts for the entire system, network, and installed services.

***

### /home  — User Directories
```
user@linux:/$ ls home
alex  priya  rahul
```
Each user has a personal folder here for their files, settings, and downloads.

***

### /lib  — Shared Libraries
```
user@linux:/$ ls lib
modules  x86_64-linux-gnu  firmware
```
Contains essential system libraries and kernel modules used by programs in `/bin` and `/sbin`.

***

### /media  — Removable Media
```
user@linux:/$ ls media
usb  dvd
```
Used for automatically mounting removable media such as USB drives or optical discs.

***

### /mnt  — Temporary Mount Points
```
user@linux:/$ ls mnt
backup  temp_mount
```
Serves as a manual mount point for system administrators to temporarily attach filesystems.

***

### /opt  — Optional Software
```
user@linux:/$ ls opt
google  vscode  jetbrains
```
Holds third-party and manually installed software packages.

***

### /proc  — Process Information
```
user@linux:/$ ls proc
1  2  3  cpuinfo  meminfo  self  uptime
```
A virtual directory containing runtime system and process information directly from the kernel.

***

### /root  — Root User Home
```
user@linux:/$ ls root
.bashrc  scripts  system_logs
```
Home folder for the system administrator (root user).

***

### /run  — Runtime Data
```
user@linux:/$ ls run
systemd  sshd.pid  lock  user
```
Stores temporary runtime files like process IDs (PIDs), sockets, and locks. Cleared at reboot.

***

### /sbin  — System Binaries
```
user@linux:/$ ls sbin
fsck  reboot  shutdown  ifconfig  fdisk
```
Contains important system administration tools for managing storage, processes, and networking.

***

### /srv  — Service Data
```
user@linux:/$ ls srv
ftp  www
```
Holds data for hosting services such as web servers (Apache, Nginx) or FTP.

***

### /sys  — Kernel Interface
```
user@linux:/$ ls sys
block  bus  class  devices  firmware  module
```
A virtual interface to the kernel and device tree used to view and configure system hardware.

***

### /tmp  — Temporary Files
```
user@linux:/$ ls tmp
temp.log  config_cache  install.sh
```
Used by applications for storing temporary files. Cleared periodically or on reboot.

***

### /usr  — User Applications and Tools
```
user@linux:/$ ls usr
bin  lib  local  share  include
```
Contains user-installed software, libraries, and documentation. Most user-level programs live here.

***

### /var  — Variable Data
```
user@linux:/$ ls var
cache  log  mail  run  spool
```
Holds data that changes often like logs, caches, backups, and mail queues.

***
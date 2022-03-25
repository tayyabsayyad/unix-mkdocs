---
title: Unix / Linux File System 
include_in_preview: false
---

In this lession we will learn about the file system of the Unix 

In Unix/Linux everything is organized as file. Unix/Linux follows a Filesystem Hierarchy Standard which defines how the directories in the Unix should be organized.

Lets go to root directory 
```
$ cd /
```

Now here in root if you do pwd then you should be able to see following 

```
$ pwd
$ /

```

Now here if you list files you should get following directories 

```
$ ls
bin   cdrom  etc   lib    lib64   lost+found  mnt  proc  run   snap  sys  usr
boot  dev    home  lib32  libx32  media       opt  root  sbin  srv   tmp  va
```
We can also use the tree command with depth option set to 1 using -L option to see the directories in the / as shown below

```
dbit@Tayyabali:/$ tree -L 1
.
├── bin -> usr/bin
├── boot
├── cdrom
├── dev
├── etc
├── home
├── lib -> usr/lib
├── lib32 -> usr/lib32
├── lib64 -> usr/lib64
├── libx32 -> usr/libx32
├── lost+found
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin -> usr/sbin
├── snap
├── srv
├── sys
├── tmp
├── usr
└── var

24 directories, 0 files
```

Now lets go through all these directories and their usage in the Unix envirnment

### /

This is on the top of the directory root, from here everything starts, we can go to this root by simply changing to using ```cd / ```

### /boot 

Lets see in the boot directory 
```
$ /boot ls
config-5.13.0-27-generic      memtest86+.bin
config-5.13.0-28-generic      memtest86+.elf
config-5.13.0-30-generic      memtest86+_multiboot.bin
efi                           System.map-5.13.0-27-generic
grub                          System.map-5.13.0-28-generic
initrd.img                    System.map-5.13.0-30-generic
initrd.img-5.13.0-27-generic  vmlinuz
initrd.img-5.13.0-28-generic  vmlinuz-5.13.0-27-generic
initrd.img-5.13.0-30-generic  vmlinuz-5.13.0-28-generic
initrd.img.old                vmlinuz-5.13.0-30-generic
lost+found                    vmlinuz.old

```

This directory stores 
    + Boot files are used to boot the computer, usually kernel files, temporary file system
    + These files belong to grub boot loader
    + Usually needed before the user programs start executing
    + 

### /bin

Lets move to /bin and see whats inside this directory 

```
$ cd bin/
$ ls
'['                                   mcomp
 aa-enabled                           mcookie
 aa-exec                              mcopy
 aclocal                              md5sum
 aclocal-1.16                         md5sum.textutils
 aconnect                             mdel
 acpi_listen                          mdeltree
 add-apt-repository                   mdig
 addpart                              mdir

```

/bin contains the binary executable files which are commonly used.

### /dev

```
$ cd /dev/
$ ls
acpi_thermal_rel  i2c-7         null       tty21  tty6       uhid
autofs            i2c-8         nvme0      tty22  tty60      uinput
block             i2c-9         nvme0n1    tty23  tty61      urandom
btrfs-control     initctl       nvme0n1p1  tty24  tty62      userio
bus               input         nvme0n1p2  tty25  tty63      v4l

```

In this directory we get all device files. In Linux based system all devices are considered as a files.

### /etc

```
$ cd /etc/
$ ls
acpi                           hostid               polkit-1
adduser.conf                   hostname             popularity-contest.conf
alsa                           hosts                ppp
alternatives                   hosts.allow          profile
anacrontab                     hosts.deny           profile.d
ansible                        hp                   protocols
apache2                        ifplugd              pulse

```

All files are under this directory are the configuration files. You can change the variables in these file to configure the setting of the entire system. 

### /home

```
$ cd /home/
$ ls
dbit  lost+found  ubuntu

```

This directory is home for all users home directory.  As you can see above we have `dbit` and `ubuntu` home directories for dbit and ubuntu users. lost + found is directory which stores the files which are not referenced or files not saved and system crashed becouse of power failure or any other kind of problems.

### /lib
```
$ cd /lib
$ ls
accountsservice                           libpdal_plugin_writer_sqlite.so.10
apg                                       libpdal_plugin_writer_sqlite.so.9
apparmor                                  libpdal_util.so.10
apt                                       libpdal_util.so.9
```

/lib contains the libraries used by the system. You wil find .so file extensitions if these files, these are dynamically linked libraries. 


### /media

```
$ cd /media/
$ ls
dbit
```
Here you will find the externally mounted deviced like hard disks, CDs etc 

### /mnt

This is also same as /media but here we mount file system temporary like network file systems 

### /opt
```
$ cd /opt/
$ ls
google  openboard  zoom
```

Here we have all the softwares which are additionally installed like databases.

### /sbin
```
$ cd /sbin
$ ls
aa-remove-unknown      grub-macbless                pppdump
aa-status              grub-mkconfig                pppoe-discovery
aa-teardown            grub-mkdevicemap             pppstats
escapesrc              mkntfs                       useradd
faillock               mkswap                       userdel
fatlabel               ModemManager                 usermod
fdformat               modinfo                      uuidd
fdisk                  modprobe                     validlocale
filefrag               mount.fuse                   vcstime
```

/sbin stores binay files like /bin but here you will get all admin commands not commom user commands.

### /tmp

```
$ cd /tmp/
$ ls
config-err-CjFGnT
hsperfdata_dbit
insync1000.sock
mkdocs_6ym74aw8
pyright-7430-VeDfGK0ubjhI
pyright-7430-ZjS2QpXL5DkR
python-languageserver-cancellation
snap.snap-store
snap.telegram-desktop
```

Here all the applications store their tempopary files. Usually these file gets deleted when your system is rebooted.


### /usr

```
$ cd /usr/
$ ls
bin    include  lib32  libexec  local  share
games  lib      lib64  libx32   sbin   src
```

Usually this directory contains the user programs, documentations and libraries that take good amount of space. On server we need to make it little larger. 

### /proc

```
$ cd /proc/
$ ls
1      1649   2      217   41    6330  7314  8668           execdomains
10     166    20     2195  414   6331  7364  8689           fb
1075   1661   2004   2197  415   6332  7430  871            filesystems
1076   1665   20089  22    419   6333  7449  8723           fs
11     1669   2010   224   42    6334  7476  874            interrupts
1115   1672   20203  225   422   6335  761   8743           iomem

```


###  /snap 

/snap stores files and folders installed using snap

Information of this directory is created dynamically by the operating system. It contains the information about the running processes and it also containts the information of the system like file system, interrupts etc 

Each number here is representing the process and its information.


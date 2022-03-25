---
title: Package Management 
include_in_preview: false
---

### Package Management Introduction

On any Linux platform we need a good packagement manager. Using Graphical Interface we can install, remove softwares.

There are many command line package managers, based on the linux distributions you may have any of the following package manager.

+ dpkg - Debian Package Manager for debian system. Using dpkg you can install, remove, store and get information about .deb packages.
+ apt - Advance packageing Tool using on Ubuntu and its derivatives like Link Mint etc
+ aptitude - Used on Debian, you need to install it additionally and use it
+ Synaptic Package Manager - Can be installed additionally and used its graphical package manager
+ DNF – Dandified Yum Used on rpm based system, modern package manager on fedora and red hat based system.
+ Pacman Package Manager – for Arch Linux and its deriatives 

Lets see one apt package manager which is used on Ubuntu based system and how we can manage the packages using this manager.

### Apt Package Manager

1. Install package 

```sudo apt install vlc```

2. Find dependancy of package

``` sudo apt depends vlc```

3.  Search for package 

``` sudo apt search kazam```
``` apt-cache search kazam ```

4. Get details of the package 
    
``` sudo apt show kazam```

5. Checking for broken packages 

``` sudo apt --fix-missing update```

6. Install broken packages 
    
```sudo apt install -f ```

7. Remove software package

``` sudo apt remove vlc```

8. Remove package and configuration 

``` apt-get --purge remove vlc ```

9. Remove no longer needed packages 

``` sudo apt-get autoremove ```

10. Update and Upgrade the system

``` 
sudo apt update
sudo apt upgrade 
```    

You will get have similar operations in other package management systems also.


Read more about other package management systems 

1. https://docs.fedoraproject.org/en-US/quick-docs/dnf/
2. https://wiki.archlinux.org/title/pacman
3. https://wiki.manjaro.org/index.php/Pamac

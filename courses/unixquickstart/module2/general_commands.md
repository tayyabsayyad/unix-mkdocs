---
title: Execution of Unix General Purpose Utility Commands 
include_in_preview: false
---

Execution of Unix General Purpose Utility Commands

Comand line is the primary and mostly used way to interact with the Linux systems

We use 

### echo Command 

echo command in unix is used to display text on screen. echo is also used for other purposes like creating file or listing the files from the directory and displaying the value of the variables. 

Some of the examples of the echo commands are as follows.

$ command -options 

the ```$``` is the default command line prompt which says its a normal user session.

if you switch to the root user it will change to ```#```

```
echo hi
echo "Hello"
a = 10
echo $a
```
We define variable a and assign value 10 to it. Using echo then wee can display its value.

### Fun with command line 

You can install some of the command line output formatting tools like cowsay, figlet etc and decorate the output in very unique and fun way.

Install these tools on ubuntu using following commands

```
$ sudo apt install cowsay
$ sudo apt install fortune
$ sudo apt install figlet
$ sudo apt install lolcat
```

You can then try following examples and try with different options

```
dbit@Tayyabali:~$ cowsay Hello
 _______
< Hello >
 -------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

Cowsay basically generates  an ASCII picture of a cow saying something provided by the user as shown above.

```
dbit@Tayyabali:~$ fortune 
Q:	Why is Christmas just like a day at the office?
A:	You do all of the work and the fat guy in the suit
	gets all the credit.

dbit@Tayyabali:~$ fortune 
Tempt not a desperate man.
		-- William Shakespeare, "Romeo and Juliet"

```

fortune will basically give you anything random text from the files , which is fun and interesting to read

```
dbit@Tayyabali:~$ figlet DBIT
 ____  ____ ___ _____ 
|  _ \| __ )_ _|_   _|
| | | |  _ \| |  | |  
| |_| | |_) | |  | |  
|____/|____/___| |_|  

```

Figlet will display the given text into large text which is made out of other screen characters.


```
echo Hello | lolcat 
Hello
```
lolcat will display the text in rainbow colors. 

Here in the above example we are passing the output of the echo command to the lolcat to display in rainbow colors

You can try following examples on your linux system and observer the outputs and play around it.

```
$ echo "This is a banner" | figlet | lolcat
```
![Banner ](cowsay2.png)

```
$ fortune | cowsay | lolcat
```
![Fortune ](cowsay1.png)


```
$ echo "Nice way to show output " | cowsay -f dragon-and-cow | lolcat
```
![ Dragon ](cowsay3.png)



### clear  

Using clear command you can clear the screen content. You can also use Ctl + l to do the same task.


### exit  

`exit` can be used for 

1. to get out of the terminal 

2. to exit from the ssh session 

3. to exit from the user login from the command line 


### date  

Use data in terminal or in shell programming to fetch the date or to calculate arthimatic operations on date

Some of the examples of teh date are given as follows 

```
date
date 2022

```

### uptime

Uptime command gives you information about your system like when it started, how long it is running etc

```
dbit@Tayyabali:~$ uptime
16:13:53 up  7:32,  2 users,  load average: 0.79, 0.41, 0.28

```

As you ca see in the above example, first column shows the curent time, second show hw long the system is running in hrs and minutes, 2 users are logged in and system load for the last 1, 5 and 15 minutes

Use -p to print information in pretty format 

```
dbit@Tayyabali:~$ uptime -p
up 7 hours, 35 minutes
```

To find out when your system started you can use -s option

```
dbit@Tayyabali:~$ uptime -s
2022-02-23 08:40:54
```

It shows system started at 23rd Feb 2022 and at 8:40:54 am 


### cal

cal command like date show the entire Calendar 

Execute following commands on your system and check the output


```
dbit@Tayyabali:~$ cal
   February 2022      
Su Mo Tu We Th Fr Sa  
       1  2  3  4  5  
 6  7  8  9 10 11 12  
13 14 15 16 17 18 19  
20 21 22 23 24 25 26  
27 28 
```

only ```cal``` will print curent months calendar 

You can specify month and year or only year also.

```
dbit@Tayyabali:~$ cal  March 2022
     March 2022       
Su Mo Tu We Th Fr Sa  
       1  2  3  4  5  
 6  7  8  9 10 11 12  
13 14 15 16 17 18 19  
20 21 22 23 24 25 26  
27 28 29 30 31
```
### tty

Lets see first what tty command gives us 

```
dbit@Tayyabali:~$ tty
/dev/pts/1
```

tty is basically teletype which is a standard file name using which we are connected to standard input. If you open another terminal and check it will give you output as /dev/pts/2 which is second file. You can see below as you open more terminals corresponding files are created under /dev/pts directory. 

```
dbit@Tayyabali:/dev/pts$ ls
0  1  2  3  ptmx
```
On most of the distribution you can open multiple terminal screen, mostly 6 are supported. You can use following key combinations to login on these termials 

```
CTRL + ALT + F1 – Lockscreen
CTRL + ALT + F2 – Desktop Environment
CTRL + ALT + F3 – TTY3
CTRL + ALT + F4 – TTY4
CTRL + ALT + F5 – TT5
CTRL + ALT + F6 – TTY6
```

You can switch between these terminals and have simultinous sessions also.


### man

man is nothing but mannual help on Linux. Its online help which you can use on terminal. 

Syntax is as follows 

```
man [options] [section] [command]
```

Manuanl of Linux system is organised as into following category 


 1  -->  Executable programs or shell commands
 
 2  --> System calls 
 
 3  -->  Library calls 

 4  --> Special files 
 
 5  --> File formats and conventions, e.g. /etc/passwd
 
 6  --> Games
 
 7  --> Miscellaneous (including  macro  packages  and  conventions),  e.g.man(7), groff(7)
 
 8  -->  System administration commands (usually only for root)
 
 9  --> Kernel routines [Non standard]

You can find all thesse details by using 

```
dbit@Tayyabali:~$ man man

```

LLets try some examples


```
dbit@Tayyabali:~$ man ls
```

To come out of this mannual you have to simple press ```q``` button

Without the any option man will give you full description of the command, its syntax, options and some of the examples of the command.


Lets see other options also

``` man -k ``` :  Display information of commands using pattern search in all sections 



``` man (1..9) command ``` : Display information from the specific section 


Lets see example output of above commands 

```
dbit@Tayyabali:~$ man -k echo
echo (1)             - display a line of text
l2ping (1)           - Send L2CAP echo request and receive answer
lessecho (1)         - expand metacharacters
pam_echo (8)         - PAM module for printing text messages
ping (8)             - send ICMP ECHO_REQUEST to network hosts
ping4 (8)            - send ICMP ECHO_REQUEST to network hosts
ping6 (8)            - send ICMP ECHO_REQUEST to network hosts
xmessage (1)         - display a message or query in a window (X-based /bin/echo)
```



```
dbit@Tayyabali:~$ man 5 sleep
No manual entry for sleep in section 2
dbit@Tayyabali:~$ man 1 sleep
``` 

As you can see above sleep is defined in sectiion 1 so last command will give you some output and tohet will 

### which

Before we see ``` which ``` command we will see a system envirnmental variable which is ```PATH```.

If we do ```echo $PATH``` then we get following paths where the bash will try to 

```
dbit@Tayyabali:~$ echo $PATH
/home/dbit/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

```
Whatever you see in the output is paths from which the commands also called as binary files will get executed. 

Lets see from where the ls and pwd commands gets executed.

```
dbit@Tayyabali:~$ which ls pwd
/usr/bin/ls
/usr/bin/pwd

dbit@Tayyabali:~$ /usr/bin/pwd
/home/dbit

```

We can also use full path of the command to execute it. 


### history

History command is usefull to see past executed commands, useually we use it with grep command to find the specific commands as shown below 

```
dbit@Tayyabali:~$ history | head 

```

Using above you can see top 10 results from the command history 

```
dbit@Tayyabali:~$ history | grep "sudo apt "
  476  sudo apt update
  477  sudo apt upgrade
  480  sudo apt install zsh
  493  sudo apt install zsh
  494  sudo apt autoremove
  495  sudo apt install zsh

```

Above example is showing searching sudo apt from the history of commands.

```
dbit@Tayyabali:~$ history 5
 1338  history | more
 1339  history 
 1340  history | grep "sudo apt "
 1341  !
 1342  history 5
```

You can also see recent 5 commands executed from the history 

```
dbit@Tayyabali:~$ 1340!

```

You can execute the commnd from the history using its event number as shown above, 1340! will execute ``` history | grep "sudo apt "``` command.


### id

id command ins Linux is used to display the ids of user and groupd. In Linux every user has its onw id numbers as shown below. You can specify the options to see ids of specific user or groups also.

```
bit@Tayyabali:~$ id
uid=1000(dbit) gid=1000(dbit) groups=1000(dbit),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),132(lxd),133(sambashare),136(libvirt),998(docker)

dbit@Tayyabali:~$ id dbit
uid=1000(dbit) gid=1000(dbit) groups=1000(dbit),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),120(lpadmin),132(lxd),133(sambashare),136(libvirt),998(docker)

dbit@Tayyabali:~$ id -u dbit
1000

dbit@Tayyabali:~$ id -u ubuntu
1001

dbit@Tayyabali:~$ id -u root
0

dbit@Tayyabali:~$ id -g root
0

dbit@Tayyabali:~$ id -g dbit
1000

```


As you can see, above, id has given us by default all id user belongs to, you can also specify the user name also using -u or group using -g 


### pwd

pwd command is used to find out which directory curently you are in. 

```
dbit@Tayyabali:~$ pwd
/home/dbit
```

### whoami


In multiuser envirnment it is possible that many users are logged in on the server so to find out with which user name you have logged in you can use whoami command.

```
dbit@Tayyabali:~$ whoami
dbit

dbit@Tayyabali:~$ su ubuntu 
Password: 
ubuntu@Tayyabali:/home/dbit$ whoami
ubuntu

ubuntu@Tayyabali:/home/dbit$ su root
Password: 
rroot@Tayyabali:/home/dbit# whoami
root

```

You can see above when you switch the user to ubuntu whoami will show you your user is changed. Observe for root login also. 

### ping

Ping command in used to check the connectivty from your system to other system or server. 

```
ubuntu@Tayyabali:~$ ping www.google.com
PING www.google.com (142.250.192.4) 56(84) bytes of data.
64 bytes from bom12s14-in-f4.1e100.net (142.250.192.4): icmp_seq=1 ttl=120 time=5.93 ms
64 bytes from bom12s14-in-f4.1e100.net (142.250.192.4): icmp_seq=2 ttl=120 time=8.42 ms
^C
--- www.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 5.934/7.176/8.419/1.242 ms
```


You have to use Ctrl + c to stop the running output. AS you can see we have got some response from the google server.

WE have transmitted 2 packets and we received 2 is response. If the server is not up or we are not connected to internet we will have all packets lost as shown below


```
dbit@Tayyabali:~$ ping www.google.com
ping: www.google.com: Name or service not known

```

You can also use -c option to specify how many packets to send and then stop 

```
dbit@Tayyabali:~$ ping -c 2 www.google.com

```

### ifconfig

We can use ifconfig to configire or see the details of the network interface details.

```

dbit@Tayyabali:~$ ifconfig
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:76:ee:3b:5f  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 84:a9:38:76:f7:a9  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2074  bytes 232530 (232.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2074  bytes 232530 (232.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        ether 52:54:00:95:c8:20  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp0s20f3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.103  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::bd0f:8a:2f4f:ca39  prefixlen 64  scopeid 0x20<link>
        ether a8:64:f1:b4:6a:22  txqueuelen 1000  (Ethernet)
        RX packets 29150  bytes 24867594 (24.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20552  bytes 4898578 (4.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

AS you can see default ifconfig with no options gives you all network interface details lile. its flags. maximum transsfer units. ipv4 and 6, its mac address etc 

You can filter it using name of the interface as shown below 

```
dbit@Tayyabali:~$ ifconfig docker0

```

You can perform folloing with the ifconfig 

```
dbit@Tayyabali:~$ ifconfig docker0 up 
SIOCSIFFLAGS: Operation not permitted

dbit@Tayyabali:~$ sudo ifconfig docker0 up 
[sudo] password for dbit: 

dbit@Tayyabali:~$ sudo ifconfig docker0 down
```

please note You need sudo permission to use above commands


You can change ip address of interface as shown below

```
dbit@Tayyabali:~$ ifconfig docker0
docker0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:76:ee:3b:5f  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

dbit@Tayyabali:~$ sudo ifconfig docker0 192.168.1.10
dbit@Tayyabali:~$ ifconfig docker0
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
        ether 02:42:76:ee:3b:5f  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

Similarly you can also set network mask, brodcast and hardware address as shown below 

```
dbit@Tayyabali:~$ ifconfig docker0 hw ether AA:BB:CC:DD:EE:FF
dbit@Tayyabali:~$ ifconfig docker0 172.16.25.125 netmask 255.255.255.224 broadcast 172.16.25.63
```

Note : I have used docker0 interface in the example you can choose any other interface availabe in your system. Please note if you know the concepts of the networking then only change ip and masks otherwise you will mess with your system.



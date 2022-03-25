---
title: Process Management 
include_in_preview: false
---


# Introduction to Process Management 

Processes on computer systems are nothing but the applications or programs which are running. 

In this lesson we will learn how to see those processes, manage processes i.e kill, change priorities etc 

Lets start with the ```ps``` command 


### ps 

ps gives you the information of all the current processes running in the system 

lets see some of the examples

```
dbit@Tayyabali:~$ ps
    PID TTY          TIME CMD
  29600 pts/1    00:00:00 bash
  29609 pts/1    00:00:00 ps
```

As you can see it displays Process ID (PID), Terminal (TTY) from which its running and time(TIME) since process has been running CMD is nothing but  command which started this process.


To see all the processes started by all users you can use -A option. You can also use -e option to do the same job as -A

```
dbit@Tayyabali:~$ ps -A
    PID TTY          TIME CMD
      1 ?        00:00:02 systemd
      2 ?        00:00:00 kthreadd
      3 ?        00:00:00 rcu_gp
      4 ?        00:00:00 rcu_par_gp
      6 ?        00:00:00 kworker/0:0H-events_highpri
      9 ?        00:00:00 mm_percpu_wq

```

As you can notice PID 1 is for system processes which started the OS itself

You can also use ps -ax to see all the processes running. This is BSD format, it will also show the state of the process

```
dbit@Tayyabali:~$ ps -ax
    PID TTY      STAT   TIME COMMAND
      1 ?        Ss     0:02 /sbin/init splash
      2 ?        S      0:00 [kthreadd]
      3 ?        I<     0:00 [rcu_gp]
      4 ?        I<     0:00 [rcu_par_gp]
      6 ?        I<     0:00 [kworker/0:0H-events_highpri]

```

To see more information of process you can also use ps aux which will give you information about user who started it, how much is memory consumption etc 

You can get more information about various advanced options using man command 


You can following command 

List processes by user 

```
ps -u user   
```

Display certain columns 

```
ps -e -o pid,uname,pcpu,pmem,comm

```

Display how much time process is running, run these command and find out meaning of each option we have specified 

```
ps -e -o pid,comm,etime

```

### pstree

This command is useful if you find out the processes relationships, You can clearly see the parent and child processes.


```
dbit@Tayyabali:~$ pstree
systemd─┬─ModemManager───2*[{ModemManager}]
        ├─NetworkManager───2*[{NetworkManager}]
        ├─accounts-daemon───2*[{accounts-daemon}]
        ├─acpid
        ├─avahi-daemon───avahi-daemon
        ├─bluetoothd
        ├─boltd───2*[{boltd}]
        ├─colord───2*[{colord}]
        ├─containerd───14*[{containerd}]

```

You can use various options like  ```ps -t``` to display threads information, ```ps -p``` to display the process ids.

You can also see the owners of the processes using -u option.

If you want to process tree of a specific user then use ```ps username  ```.


### nice and renice 

Nice command allows you to change the priority of the process. Every process have a scheduling priority in the system. Using the nice command you can change the scheduling priority of the process.

Simple way to check the nice value of the process is to use top or htop command as shown below

```
top - 13:36:36 up  4:36,  1 user,  load average: 0.71, 1.03, 0.90
Tasks: 344 total,   1 running, 343 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.6 us,  0.7 sy,  0.0 ni, 96.5 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15702.4 total,   5945.5 free,   3563.7 used,   6193.3 buff/cache
MiB Swap:  37275.0 total,  37275.0 free,      0.0 used.  11011.6 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                               
  33697 dbit      20  0   24.4g 157768  99700 S  16.6   1.0   1:07.02 chrome                                                                
   1891 dbit      20  0  5481220 329456 112620 S   6.3   2.0   9:35.99 gnome-shell                                                           
   1756 dbit      20  0   627652 112860  70404 S   4.6   0.7   7:21.56 Xorg                                                                  
  28603

```
As you can see in fourth column nice value is 0 for process 33697 process ID 

You can also check NI value using ```ps -l```

```
dbit@Tayyabali:~$ ps -l
F S   UID     PID    PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 S  1000   30108   28603  0  80   0 -  4911 do_wai pts/2    00:00:00 bash
4 R  1000   37432   30108  0  80   0 -  5013 -      pts/2    00:00:00 ps
```
Highest priority process can have -20 and lowest can have +19, default priority fr user created process is 0

You can check default nice value set for you using simple ```nice``` command also as shown below 

```
dbit@Tayyabali:~$ nice 
0
```

You can set the nice value as shown below 

```
dbit@Tayyabali:~$ nice -10 firefox 
```
Firefox process will be started with 10 nice value you can verify it using 

```
dbit@Tayyabali:~$ ps -l
F S   UID     PID    PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 S  1000   21012   21004  0  80   0 -  2753 do_wai pts/0    00:00:00 bash
4 S  1000   21019   21012  4  90  10 - 871423 poll_s pts/0   00:00:06 firefox
4 S  1000   21088   21019  0  90  10 - 49607 poll_s pts/0    00:00:00 Socket Process
4 S  1000   21121   21019  0  90  10 - 608625 poll_s pts/0   00:00:01 Privileged Cont
4 S  1000   21197   21019  0  90  10 - 607810 poll_s pts/0   00:00:00 WebExtensions
4 S  1000   21261   21019  0  90  10 - 598673 poll_s pts/0   00:00:00 Web Content
4 S  1000   21264   21019  0  90  10 - 598673 poll_s pts/0   00:00:00 Web Content
4 S  1000   21268   21019  0  90  10 - 598673 poll_s pts/0   00:00:00 Web Content
4 R  1000   21650   21012  0  80   0 -  2854 -      pts/0    00:00:00 ps
```
You can start the process with a specified priority but what if you want to change the priority of already running process, to do this we use renice command 

```
renice: failed to set priority for 21954 (process ID): Permission denied
dbit@Tayyabali:~$ sudo renice -n -10 -p 21954
[sudo] password for dbit: 
21954 (process ID) old priority 10, new priority -10

```
Note you need sudoers permission to use this command 

-n is to specify the priority and -p is specify the process id of the running process. 

### kill 

Kill command is siply used to terminate the running processes. You need to know the process id to kill the process. 

Using ps aux and filtering it easily find out the process ID or you can also make use of pidof command with application name to find out pid of process 

as shown below 

```
dbit@Tayyabali:~$ pidof firefox 
24002 23998 23995 23922 23874 23845 23778

dbit@Tayyabali:~$ pidof gedit
24182

dbit@Tayyabali:~$ pidof chrome
24198 24061 22974 22959 22944 22915 22873 22859 22835 22819 22805 22783 22756 22739 22733 22728 22709 22696 22679 22664 22651 22630 22577 22557 4126 3989 3976 3956 3812 3801 3799 3777 3773 3772 3756
```

Finding PID Using grep and filter 

```
dbit@Tayyabali:~$ ps au | grep "chrome"
dbit       24436  0.0  0.0   8908   720 pts/0    S+   06:27   0:00 grep --color=auto chrome

dbit@Tayyabali:~$ ps au | grep "gedit"
dbit       24481  0.0  0.0   8908   656 pts/0    S+   06:28   0:00 grep --color=auto gedit
```

To kill simply use kill and PID 

```
dbit@Tayyabali:~$ pidof gedit
24182

dbit@Tayyabali:~$ kill 24182
```
### pkill

pkill works similar to kill but it takes the name of the progrma instead of the process id 

```
dbit@Tayyabali:~$ pkill gedit

```

### killall

killall like other kill commands will kill all the process matching the name of the processes

```
dbit@Tayyabali:~$ killall chrome
```

Note kill commands kills only one process whereass killall kills multiple processes

### xkill

xkill is used to kill the graphical applications 

when run on the terminal it allows you to select the window and kill it using the mouse. 

### bg, fg and jobs 

bg command is used to send the job in the background 
fg is to get the job in the foreground and 
jobs will display all the jobs which are currently running in the background 


Lets do some experiments 

Step 1 : Start applications or processes from the terminal

```
dbit@Tayyabali:~$ gedit

```

It will open gedit application but in the foreground. The teminal is occupied so lets stop the application using ```Ctr + Z``` and then
execute the bg command to put it in the background 

as shown below 

```
dbit@Tayyabali:~$ gedit
^Z
[1]+  Stopped                 gedit

dbit@Tayyabali:~$ bg
[1]+ gedit &

dbit@Tayyabali:~$ jobs
[1]+  Running                 gedit &
```

You can see the [1] job is running in the background 

similarly we can put the firefox in the background and then we use jobs command to see how many jons are running in the background

  ```
  dbit@Tayyabali:~$ firefox
ATTENTION: default value of option mesa_glthread overridden by environment.
^Z
[2]+  Stopped                 firefox

dbit@Tayyabali:~$ bg
[2]+ firefox &


dbit@Tayyabali:~$ jobs
[1]-  Running                 gedit &
[2]+  Running                 firefox &

  ```

You can now bring the any application using the number into foreground

using following command

```
dbit@Tayyabali:~$ fg 1
gedit
```


### pgrep

pgrep command is used to find the process Id matching the supplied name 

following are the some of the examples 

```
dbit@Tayyabali:~$ pgrep firefox 
38270
dbit@Tayyabali:~$ pgrep code
4224
4232
4233
4235
4262
4272
4291
4330
4352
4373
4426
4472
dbit@Tayyabali:~$ pgrep terminal
38719
```

We can also use the -u option to specify the user whose processes we care interested in 

```
dbit@Tayyabali:~$ pgrep -u dbit terminal
38719
```


---
title: Memory Management 
include_in_preview: false
---

In this lesson you will learn following memory management commands

+ **free**  - To check RAM status 
+ **proc/meminfo** - Detailed RAM status 
+ top  - Process Management 
+ htop - Advanced Process Management 
+ df - 
+ du
+ vmstat
+ demidecode
+ sar
+ pagesize 
  

### free command 

Free command is used to find out how much RAM is free and how much is used. It displays physical, swap, cache and buffers status 

you can use following options to customize the display 

- b - to display output in bytes
- k - to display in kilobytes 
- m - to display in mebibytes
- g - to display in gibibytes 

You can also use the -s option to display results for given seconds apart

Example1 : Display memory status in megabtes

```
➜  ~ free -m     
              total        used        free      shared  buff/cache   available
Mem:          15702        3442        8185         970        4073       10965
Swap:         37274           0       37274

```

Meaning of each column 

+ total : Total full available RAM memory size
+ used :  Amount of RAM currently used by the processes
+ free : Free memory i.e. Available - Used 
+ shared : memory used in tmpfs to for creating the virtual memory
+ buff/cache : Memory used by cache and kernel buffers 
+ available : memory available to run more applications 

Example2: Display memory status in every second in gegabytes format

```
$ free -g -s 1

➜  ~ free -g -s 1
              total        used        free      shared  buff/cache   available
Mem:             15           3           8           0           3          10
Swap:            36           0          36

```


## /proc/meminfo 

Under /proc directory we have meminfo file, this file give lot of information about your systems RAM memory.

You can use cat or nano to display the content of this file. Actually this file is created in the memory by OS to give all the information about the system.


Sample output of meminfo file is shown below

```
➜  ~ cat /proc/meminfo 
MemTotal:       16079272 kB
MemFree:         8352544 kB
MemAvailable:   11210548 kB
Buffers:          194212 kB
Cached:          3848588 kB
SwapCached:            0 kB

Active:          1229996 kB
Inactive:        5143856 kB
Active(anon):      17496 kB
Inactive(anon):  3320736 kB
Active(file):    1212500 kB
Inactive(file):  1823120 kB
Unevictable:      768512 kB
Mlocked:              64 kB

SwapTotal:      38169596 kB
SwapFree:       38169596 kB
Dirty:               404 kB
Writeback:           240 kB
AnonPages:       3099708 kB
Mapped:          1117128 kB

. . . 

```

We will not go through all the attributes of the above file, you need to know th concepts of Operating System to understand the menaing of all the attributes.

In this file you will get total RAM size, total swap memory, consumed, free, available to use, memory page mappings, virtual memory allocations, dirty pages, swapped memory etc.

For more information you can visit : https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/s2-proc-meminfo

### top

top is used to display the process running in the system. When you run the top command you get following output

![top command ](top.png)

Top displays following information on first few lines 

+ Current time and sinceh when system booted 
+ Total numers of users logged in 
+ system load over 1,5 and 15 min 
+ How many tasks/processes are running and their states 
+ CPU utilization and their categories of usage as shown following 
    + us, user    : time running un-niced user processes
    + sy, system  : time running kernel processes
    + ni, nice    : time running niced user processes
    + id, idle    : time spent in the kernel idle handler
    + wa, IO-wait : time waiting for I/O completion
    + hi : time spent servicing hardware interrupts
    + si : time spent servicing software interrupts
    + st : time stolen from this vm by the hypervisor
+ Physical Memory usage information like total, free, used and buff/cache 
+ Swap memory usage information like total, free, used and avail


As you can see in the output, get following information in the colums

+ PID - Process identifier 
+ USER - User who started or Owner of process 
+ PRI - Process priority for kernel
+ NI - Process priority set by user or root 
+ VIRT - Vrtual memory consumed by process 
+ RES - Physical memory consumed by the process 
+ SHR - Shared memory consumed by the process 
+ S - State of the process 
+ CPU% - % CPU utilization by the process 
+ MEM% - % of Memory consumption by the process 
+ TIME+ - time since the process started the execution 
+ Command - Command path which started the execution of the process 


Process states : 

+  D = uninterruptible sleep
+  I = idle
+  R = running
+  S = sleeping
+  T = stopped by job control signal
+  t = stopped by debugger during trace
+  Z = zombie


### htop

![htop command ](htop.png)

Htop is advanced process monitoring command siliar to top but it gives more advanced interactive features. 

Htop has similar colum out put as top command along with this is shows information about the individual cpu utilizations on top.

You can use the keyboard to do various additional operations like 

+ Use arrow keys to scroll through processes like left, right, home etc
+ Use function keys to search, filter, sort, change priority and kill processes.


### df 

### du

### vmstat

### demidecode

### sar

### pagesize 
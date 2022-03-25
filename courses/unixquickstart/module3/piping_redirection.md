---
title: Piping and Redirection in Unix 
include_in_preview: false
---

### Redirection in Linux using <,> and >> 

In Linux there are three data streams from which we get and send data, they are 
1. Standard input which is keyboard (STDIN)
2. Standard output which is display (STDOUT)
3. Standard Error which is displayed on STDOUT only

We can use redirection operators to redirect standard output to files. Similary we can also change the standard input to file so the input will be take from the files

Lets see redirections with examples

```
dbit@Tayyabali:~/videmo$ ls 
diploma1  diploma2  file1  his  secondfile

dbit@Tayyabali:~/videmo$ ls > files_in_videmo

dbit@Tayyabali:~/videmo$ cat files_in_videmo 
diploma1
diploma2
file1
files_in_videmo
his
secondfile

```

We use ls to display files which are by default displayed on the screen, using > redirection operator we then redirect the output to file ```files_in_videmo```. So insted of displaying it on screen its transfered to file.

Lets see now another example when we take input from the file and not from keyboard.

wc command is best example where we can give input from the file    

```
dbit@Tayyabali:~/videmo$ wc -l < files_in_videmo 
6
```
Above command displays the line numbers from the files_in_videmo file

You can use >> operator to append the text in output redirection. > will override file 


Lets now see how to redirect the standard error from display screen to the file 

```
dbit@Tayyabali:~/videmo$ ls /de
ls: cannot access '/de': No such file or directory

dbit@Tayyabali:~/videmo$ ls /de 2> errormsg

dbit@Tayyabali:~/videmo$ cat errormsg 
ls: cannot access '/de': No such file or directory
```

In many cases we get error messages on the screen and they are annoying so we can redirect them to the file or log or many to black hole where they are iqnored and absorbed.

In above example we get error /de file or director cannot access, we use file descriptors number 2 to redirect error to the erromsg file and then wehen we display we get error message is got displayed in the file.

Please note when ther is no error, file wont have anything and it will be overwritten each time you run the command as shown below 

```
dbit@Tayyabali:~/videmo$ ls  2> errormsg
diploma1  diploma2  errormsg  file1  files_in_videmo  his  ip  ping  secondfile  wc
dbit@Tayyabali:~/videmo$ cat errormsg
```

+ 0 file descriptor is used for input 
+ 1 is used for output 
+ 2 is file descriptor for the error 

We can also use these numbers to redirect as shown below 

```
dbit@Tayyabali:~/videmo$ ls 1>file_list

dbit@Tayyabali:~/videmo$ cat file_list 
diploma1
diploma2
errormsg
file1
file_list
files_in_videmo
his
ip
ping
secondfile
wc
```

### Pipe is Linux 

Pipe represented using ```|``` symbol is used to give the output of one command to give as input to next command. Its one of the very powefull feature in the Linux command line


lets see with example

```
dbit@Tayyabali:~/videmo$ ls | grep "file"
file1
file_list
files
files_in_videmo
file_with_f_starting
secondfile
```

Using pipe we passed the output of ls to grep which will search for the file names which contains file in it and displays on the screen

Lets se more advanced example using tee command 

```
dbit@Tayyabali:~/videmo$ ls | grep "file" | tee  file_with_f_starting 
file1
file_list
files
files_in_videmo
file_with_f_starting
secondfile

dbit@Tayyabali:~/videmo$ cat file_with_f_starting 
file1
file_list
files
files_in_videmo
file_with_f_starting
secondfile
```

Here we pass out put of ls command to grep for pattern search and then redirect output to  to standard output and also to file. 

tee command is used to pass output to standard display and to file at once. 


# Interesting examples of piping and redirection


Find ip addresses of starting with 192

```
dbit@Tayyabali:~/videmo$ ifconfig | grep 192
        inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
        inet 192.168.1.103  netmask 255.255.255.0  broadcast 192.168.1.255

```


Above command will count the number of files in a given directory, to count recursively use -R option


```
dbit@Tayyabali:~/videmo$ ls | wc -l
13
```

Sorting files with size 

```
dbit@Tayyabali:~/videmo$ du -a ~/videmo/ | sort -n -r | head -n 5
84	/home/dbit/videmo/
24	/home/dbit/videmo/his
12	/home/dbit/videmo/.file1.swp
12	/home/dbit/videmo/.demo1.txt.swp
4	/home/dbit/videmo/wc
```
In above example 

+ du will estimate file space usage
+ sort will sort out the output of du command
+ head will only show top 20 largest file in ~/videmo/


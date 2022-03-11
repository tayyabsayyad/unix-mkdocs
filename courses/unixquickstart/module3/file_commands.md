---
title: File Management Commands  
include_in_preview: false
---

Execution of File System Management Commands


### ls 

We can use ls command to list the files and directories 

Its syntax is 

```ls [options] file ```

You can specify options and also pass directories or any specifc files you want to list

les see examples 

```
dbit@Tayyabali:~$ ls
MentorMenteeSystem   demoGit     idea-IC            
```

You can use various flags to customize the listing 

+ -r - to reverse the listing alphabetically 
+ -l - to list files in long format as shown below 
+ -t - sort by modification time, newest first

You can also combine these options flag as ```ls -lr ```

Lets see the long listing of the files using ls -l 

```
dbit@Tayyabali:~$ ls -l
total 16072
drwxrwxr-x  8 dbit dbit     4096 Feb 10 16:22  MentorMenteeSystem
```

The information can be broken down into ten fields as shown below. Let us consider the Desktop directory.

`drwxrwxr-x  8 dbit dbit     4096 Feb 10 16:22  MentorMenteeSystem`

|Detail | Description|
|:---:| ---|
|d | file type|
|rwx | owner's mode of access(permission)|
|r-x | group's mode of access(permission)|
|r-x | other's mode of access(permission)|
|8 | number of hard links|
|dbit | owner of the file|
|dbit | group of the file|
|4096 | size of the file in bytes|
|Feb 10 16:22  | last modified time stamp|
|MentorMenteeSystem | Name of File/Dir |


`**d**rwxrwxr-x  8 dbit dbit     4096 Feb 10 16:22  MentorMenteeSystem`

The first field **file type** can be of the following types:

|Detail | FileType | Description|
|:---:|:---: | ---|
| d | Directory | A file used to store other files.|
| - | Regular file | Includes readable files, images files, binary files, and compressed files.|
| l | Symbolic link | Points to another file.|
| s | Socket | Allows for communication between processes.(duplex)|
| p | Pipe | Allows for communication between processes executed under different user names and permission.(unidirectional)|
| b | Block file | Used to communicate with hardware.(read/write data in blocks)|
| c | Character file | Used to communicate with hardware.(read/write data character by character)|

<br>
d**rwxrwxr-x**  8 dbit dbit     4096 Feb 10 16:22  MentorMenteeSystem
<br>

The next nine set of characters indicate the **permissions/mode of access** o the file. There are three different types of permissions as shown below
Permission | Effect on file | Effects on directory


| Permisson | Use | Description|
|:---:|:---: | ---|
| Read ( r ) | Allows for file contents to be read or copied. | Without execute permission on the directory, allows for a non-detailed listing of files. With execute permission, ls -l can provide a detailed listing.
|Write ( w ) | Allows for contents to be modified or overwritten. Allows for files to be added or removed from a directory. | For this permission to work, the directory must also have execute permission.
|Execute( x) | Allows for a file to be run as a process, although script files require read permission, as well. | Allows a user to change to the directory if parent directories have write permission as well.

The nine characters can be broken down into sets of three. They correspond to the owner of the file, the group that own's the file and others(excluding the owner and the group)

In case of the Desktop directory, the owner has read, write and execute permission, the group which owns the directory has read and execute permission & the others have read and execute permission.

----------------------------------------------------------------------------
drwxrwxr-x  **8** dbit dbit     4096 Feb 10 16:22  MentorMenteeSystem

    The next field indicates the number of hard links to the file.

----------------------------------------------------------------------------
drwxrwxr-x  8 **dbit** dbit     4096 Feb 10 16:22  MentorMenteeSystem

    The next field indicates the owner of the file.

----------------------------------------------------------------------------
drwxrwxr-x  8 dbit **dbit**     4096 Feb 10 16:22  MentorMenteeSystem

    The next field indicates the group that owns the file.

----------------------------------------------------------------------------

drwxrwxr-x  8 dbit dbit     **4096** Feb 10 16:22  MentorMenteeSystem

    The field that follows is the size of the file in bytes.

----------------------------------------------------------------------------
drwxrwxr-x  8 dbit dbit      4096    *Feb 10 16:22**  MentorMenteeSystem


    The next field is the last modified date of thee file.

----------------------------------------------------------------------------

drwxrwxr-x  8 dbit dbit      4096    Feb 10 16:22  **MentorMenteeSystem**  

    The last field  is the name of file/directory.

----------------------------------------------------------------------------

### cd 

cd command is used to change the working directory some of the examples how we can change the directory are given below

Example 1 : 

```
dbit@Tayyabali:~$ cd ~ 

dbit@Tayyabali:~$ cd / 

dbit@Tayyabali:/$

dbit@Tayyabali:~$ cd 
```

We use ```~``` called as ```tild``` to directly switch from any directory to home directory. 

We can also use only cd command to go to home dirctory 


Example 2 : We can use the absolute path to go to the directory

```
dbit@Tayyabali:~$ cd /home/dbit
```



Example 3 : cd .. is is used to traverse one level up to the directory. If you reach to / then no effect of this command 


```
dbit@Tayyabali:~$ cd ..
```


Example 4 : Switch back to last working directory

```
dbit@Tayyabali:~$ cd /
dbit@Tayyabali:/$ cd -
/home/dbit
dbit@Tayyabali:~$
```

### pwd 

pwd command is used to display the directory in which you are currently working 

```
dbit@Tayyabali:~$ pwd
/home/dbit
dbit@Tayyabali:~$ cd /
dbit@Tayyabali:/$ pwd
/
dbit@Tayyabali:/$
```
### cat 

Cat command is used for many purposes we see through examples

##### cat to display content of file data on standard output 
    ```
    dbit@Tayyabali:~$ cat filename

    ```
    
##### cat to display multiple files data on standard display 

    ```
    dbit@Tayyabali:~$ cat file1
    This is file 1 

    dbit@Tayyabali:~$ cat file2
    This is file 2

    dbit@Tayyabali:~$ cat file1 file2
    This is file 1 
    This is file 

    ```
##### cat to create files

Using cat you can create file also as follows 

```
dbit@Tayyabali:~$ cat > file3
This is file 3
Use Ctr + d to end the input 


dbit@Tayyabali:~$ cat file3
This is file 3
Use Ctr + d to end the input

```
You can use Ctrl + d to stop input to file. First block of code above is input process.


If the content of the cat is long then you can also use it with ```more``` and ```less``` commands using pipes 

Using cat you can also display the line numbers in the output as follows 

```
dbit@Tayyabali:~$ cat -n file3
     1	This is file 3
     2	Use Ctr + d to end the input
```

You also use redirection operators and sort operation with cat as follows 

```
dbit@Tayyabali:~$ cat file1 > file3
dbit@Tayyabali:~$ cat file3
This is file 1
```
In above example file1 content is overwritten in file3 
If you want to append then use >> operator 


### mkdir 

mkdir is used to create directories, you can use various options to create subdirectries also or you can also create multiple directories using patterns also.


Examples 

Create a single directory 

```
dbit@Tayyabali:~$ mkdir unixlab
dbit@Tayyabali:~$ cd unixlab/
dbit@Tayyabali:~/unixlab$ pwd
/home/dbit/unixlab
```

Create muliple directories at once 

```
dbit@Tayyabali:~/unixlab$ mkdir {module1,module2,module3}
dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3
```

Create parent directories if not exist while creating subdirectory

```
dbit@Tayyabali:~$ mkdir -p unixlab/module5/mod5sub
dbit@Tayyabali:~$ cd unixlab/
dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3  module5
```

Notice unixlab directory was already their so it did not create new one. it only created module5

```
dbit@Tayyabali:~$ mkdir -p unixlab/module6/mod6sub
dbit@Tayyabali:~$ ls unixlab/module6/
mod6sub

```

In above example module6 directory was not available so it got created and then mod6sub was created.


### rmdir 

rmdir is used to remove **empty** directories 

```
dbit@Tayyabali:~/unixlab$ rmdir module5
dbit@Tayyabali:~/unixlab$ rmdir module6
rmdir: failed to remove 'module6': Directory not empty

```

You can we were able to remove module5 but not the module6 because its not empty

You can also remove multiple directories at once if they all are empty using following command 

``` $ rmdir dir1 dir2 dir3```

### rm 

rm command can be used to remove files and directories. Here it willl also remove the subdirectories also with special option

Some of the options which we can use with the rm are 

1. -f: Forcefull removal of all files/directorie
2. -i: confirmation before deletion, safe option to delete files
3. -r: recursively delete all files and directories (Use carefully )
4. -d: remove empty directories only 

Lets see some of the examples 

Using rm -r 

```
dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3  module6  unixlab

dbit@Tayyabali:~/unixlab$ rm unixlab/
rm: cannot remove 'unixlab/': Is a directory

dbit@Tayyabali:~/unixlab$ rm -r unixlab/

dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3  module6
dbit@Tayyabali:~/unixlab$
```

We list directories first, then we try to remove unixlab directories it gives error saying its directory, so to remove directory we use -r option.

```
dbit@Tayyabali:~/unixlab$ touch abc 

dbit@Tayyabali:~/unixlab$ ls
abc  module1  module2  module3  module6

dbit@Tayyabali:~/unixlab$ rm abc

dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3  module6

```
In above example we create the empty file using touch command and then we remove it using rm command 

Below is the example where we using -i and r together to remove the files and directories recursiverly and interactively 

```
dbit@Tayyabali:~/unixlab$ rm -ri module6 
rm: descend into directory 'module6'? y  
rm: remove directory 'module6/mod6sub'? y
rm: remove directory 'module6'? y
dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3
```

Removing empty directories using -d 

```
dbit@Tayyabali:~/unixlab$ rm -d module1

dbit@Tayyabali:~/unixlab$ cd module2
dbit@Tayyabali:~/unixlab/module2$ touch abc
dbit@Tayyabali:~/unixlab/module2$ cd ..
dbit@Tayyabali:~/unixlab$ rm -d module2
rm: cannot remove 'module2': Directory not empty
```

### cp 

cp command is used to copy files and directories 

the syntax of cp is as follows 

```
cp [options] source destination

```

Example 1 : Copy files from one dir to other 

We have following files and directories 

```
dbit@Tayyabali:~/unixlab$ tree
.
├── module1
│   └── mod1file
├── module2
└── module3

3 directories, 1 file
```

lets copy file frm module1 to module2

```
dbit@Tayyabali:~/unixlab$ cp module1/mod1file module2/
dbit@Tayyabali:~/unixlab$ tree
.
├── module1
│   └── mod1file
├── module2
│   └── mod1file
└── module3

```

you can also copy multiple files from different directories to a target directory. 

```
dbit@Tayyabali:~/unixlab$ tree
.
├── module1
│   ├── file2
│   ├── file3
│   └── mod1file
├── module2
│   ├── mod1file
│   └── mod2file
└── module3

3 directories, 5 files

```

Lets say we want to copy file2 from module1 and modfile2file to module3 

```
dbit@Tayyabali:~/unixlab$ cp module1/file2 module2/mod2file module3/
dbit@Tayyabali:~/unixlab$ tree
.
├── module1
│   ├── file2
│   ├── file3
│   └── mod1file
├── module2
│   ├── mod1file
│   └── mod2file
└── module3
    ├── file2
    └── mod2file

3 directories, 7 files

```

Observe the changes in the above output 

To copy the entire directory you can use -r, lets copy module1 directory to module3

```
dbit@Tayyabali:~/unixlab$ cp module1/ module3
cp: -r not specified; omitting directory 'module1/'

dbit@Tayyabali:~/unixlab$ cp -r module1/ module3
dbit@Tayyabali:~/unixlab$ tree
.
├── module1
│   ├── file2
│   ├── file3
│   └── mod1file
├── module2
│   ├── mod1file
│   └── mod2file
└── module3
    ├── file2
    ├── mod2file
    └── module1
        ├── file2
        ├── file3
        └── mod1file

4 directories, 10 files
dbit
```

If you dont specify the -r it will give you above error 

Some of the interesting options you must try 

1. Use -i to copy files interactively 
2. Use -n to avoide overwriting the files on the destination
3. Use -u to only copy is source file is newer than the destination file
4. Use -p to preserver the timestamp and ownership of the files 
5. Use -v to see the progress of copy operation 


### mv 

mv command is used to move files and directories from source to destination. 
This command can also be used to rename the file or directory 

If the destination is different place then it is moved otherwise it is renamed.

```
dbit@Tayyabali:~/unixlab$ ls
module1  module2  module3
dbit@Tayyabali:~/unixlab$ mv module1 module_one
dbit@Tayyabali:~/unixlab$ ls 
module2  module3  module_one

```
We have changed the name of the module1 directory to module_one 

lets now move module_one to module3 directory

```

dbit@Tayyabali:~/unixlab$ mv module_one/ module3
dbit@Tayyabali:~/unixlab$ ls 
module2  module3
dbit@Tayyabali:~/unixlab$ tree
.
├── module2
│   ├── mod1file
│   └── mod2file
└── module3
    ├── file2
    ├── mod2file
    ├── module1
    │   ├── file2
    │   ├── file3
    │   └── mod1file
    └── module_one
        ├── file2
        ├── file3
        └── mod1file

4 directories, 10 files

```

### wc 

wc command is nothing but word count command. It is used to count the number of lines words and characters 

We can use following options to modify the output as per our requirements

-c print the byte counts
-m chars print the character counts
-l lines print the newline counts
-w print the word counts

Lets see the examples of above options 

```
dbit@Tayyabali:~/unixlab$ cat wcdemo 
This is wc demo 
I am on the second line 
wc is used for word count 

dbit@Tayyabali:~/unixlab$ wc wcdemo 
 3 16 69 wcdemo

dbit@Tayyabali:~/unixlab$ wc -c wcdemo 
69 wcdemo

dbit@Tayyabali:~/unixlab$ wc -l wcdemo 
3 wcdemo

```

The output indicates 3 - lines, 16 - words and 69 characters  




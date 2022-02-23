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

### pwd 

### cat 

### mkdir 

### rmdir 

### rm 

### cp 

### mv 

### chmod 

### wc 

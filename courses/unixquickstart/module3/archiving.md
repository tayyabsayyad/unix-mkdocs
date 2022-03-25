---
title: Archiving 
include_in_preview: false
---

Command used for the archiving files 

### gzip

gzip is a file format and a software application used for file compression and decompression

Lets compress one file 

```
dbit@Tayyabali:~/zipdemo$ gzip a 
dbit@Tayyabali:~/zipdemo$ ls 
a.gz  b  c  d  zip_files.zip
```

Notice a.gz archive is created 


You can also compress multiple files together as show follow 

```
dbit@Tayyabali:~/zipdemo$ gzip a b c d 
dbit@Tayyabali:~/zipdemo$ ls 
a.gz  b.gz  c.gz  d.gz

```

To decompress gz files we use 

```
dbit@Tayyabali:~/zipdemo$ gzip -d a.gz 
dbit@Tayyabali:~/zipdemo$ ls
a  b.gz  c.gz  d.gz

```









### bzip2


bzip2 command in Linux is used to compress and decompress the files i.e. it helps in binding the files into a single file which takes less storage space as the original file use to take





### zip and unzip


Zip syntax is 

``` zip [options] zipfileName Files_To_Zip_List```

Lets create zipdemo directory and then create 4 files and add then to zip file

```
dbit@Tayyabali:~$ mkdir zipdemo

dbit@Tayyabali:~$ cd zipdemo/

dbit@Tayyabali:~/zipdemo$ touch a b c d 

dbit@Tayyabali:~/zipdemo$ ls
a  b  c  d

dbit@Tayyabali:~/zipdemo$ zip zip_files a b c d 
adding: a (stored 0%)
adding: b (stored 0%)
adding: c (stored 0%)
adding: d (stored 0%)

dbit@Tayyabali:~/zipdemo$ ls
a  b  c  d  zip_files.zip
```

To unzip simple use the command unzip, Please note before extracting, I have deleting a,b,c and files from zipdemo directory


```
dbit@Tayyabali:~/zipdemo$ unzip  zip_files.zip 
Archive:  zip_files.zip
extracting: a                       
extracting: b                       
extracting: c                       
extracting: d                       
dbit@Tayyabali:~/zipdemo$ ls
a  b  c  d  zip_files.zip
```


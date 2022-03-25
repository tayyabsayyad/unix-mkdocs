---
title: User Management Commands 
include_in_preview: false
---

Execution of User Management Commands 

Linux is multi-user operating system, when we work on servers its always the case where its access is given to many users with certain permissions.

Permissions of users can be like whether he can access certain directories or services.

In this lesson we will learn how to do user management.

To perform user management activites you will need access to the root permissions or at least sudo permissions are needed to your user which you are logged in with. 

Lets start with simple commands and then go the advanced 

### who 

We can use who command to check who all are logged on to the Laniux Server/ Desktop. 

```
ubuntu@ip-172-31-1-49:~$ who
ubuntu   pts/0        2022-02-23 05:43 (15.206.23.229)
```

We get following output from the command

1. User name who loged in i.e in our case is ubuntu 
2. How users are joined in i.e directly on server or from remote computer. If user is joined from remote computer then its pts/0 else it will be shown as like tty or :0  
3. Time when the user is logged in 
4. From which remote IP address user has joined 

Following example show two loggins from the same computer 

```
ubuntu@ip-172-31-1-49:~$ who
ubuntu   pts/0        2022-02-23 05:50 (15.206.23.229)
ubuntu   pts/1        2022-02-23 05:50 (15.206.23.229)
```
### whoami

Most of time you have multiple user access to the system. What if you want to by which user name you have logged in on the system.

So basically you check your user name on the already logged in system.

On server when we check whoami then we get it as ubuntu which is a user name with whom we have logged in on the server.


```
ubuntu@ip-172-31-1-49:~$ whoami
ubuntu
```


Now lets move to command which is mostly used when doing admin tasks.

### su

su is switch user command. Using this you can switch to other user on the terminal. On a give Linux system there might be many users accounts, you can swithc to other user account without need to logout from your existing account. 

Example below shows how we are able to switch from dbit user to ubuntu user. 

```
dbit@Tayyabali:~$ su ubuntu 
Password: 
ubuntu@Tayyabali:/home/dbit$
```

As you can see on the command prompt 

For this to work you should have the other users login access permission.

Notice the prompt ```dbit@Tayyabali``` gets changed to 
As you can see we had logged in user dbit account on Tayyabali Computer. 
when we switch to ubuntu user our promt gets changed to ```ubuntu@Tayyabali```

To log out from ubuntu user simple use ```exit``` command.

We can also use the su command with -c option to run a command with given users previllege. You can try that with as shown following syntex

su –c [command] [other_user]

Lets execute whoami command using above syntex

```
dbit@Tayyabali:~$ su -c whoami ubuntu
Password: 
ubuntu

```

As you can see the output commands are executing with ```ubuntu``` users previleges.


### sudo 

sudo command (SuperUser DO) in Linux allows you to get temporary previlages and run the commands. 

You can use the ```sudo``` before the command and execute it as shwon below


```
ubuntu@Tayyabali:~$ sudo ls
[sudo] password for ubuntu: 
ubuntu is not in the sudoers file.  This incident will be reported.
```
We have executed the sudo ls command under the user ```ubuntu```. Since this user is not added in the sudoers file his user cant execute commands with sudo.

To add user to sudoers group you can use any of the following,

1. Using user mode command ```sudo usermod -a -G sudo <user>```
2. Using the gpasswd ``` sudo gpasswd -a <user> sudo```
3. Using visudo ``` sudo visudo```

Once you add the ubuntu user to sudoers group then ubuntu user can execute the commands with sudo as shown below 

```
ubuntu@Tayyabali:~$ sudo ls
Desktop  Documents  Downloads  Music  Pictures	Public	Templates  Videos

```

### login 

login command is used to login into the system. On Ubuntu system you need to be root user to login from terminal. 
When you login if username is not provided it will ask the username and password.

Lets see example of login 

```
dbit@Tayyabali:~$ login
login: Cannot possibly work without effective root
```

When you are logged in with regular user it will give such error messages

Using the sudo su root we switch to root user, you can also use only ```su root```. 

```
dbit@Tayyabali:~$ sudo su root
[sudo] password for dbit: 
root@Tayyabali:/home/dbit# 
```

Once you login using root notice the prompt is changed to ```#```

Now lets try login command 

```
root@Tayyabali:/home/dbit# cd 
root@Tayyabali:~# login 
Tayyabali login: dbit
Password: 
Welcome to Ubuntu 20.04.4 LTS (GNU/Linux 5.13.0-30-generic x86_64)

```

If you dont specfy user ten it will ask you user name along with password also.

To logout simple use ```exit``` command or logout command. 


### passwd

passwd commmand is used to change the password on command line 

With this command root user can change password of anyuser, and all other users can change only their password.

Lets change password as follows 

```
ubuntu@Tayyabali:~$ passwd 
Changing password for ubuntu.
Current password: 
New password: 
Retype new password: 
Password unchanged
New password: 
Retype new password: 
passwd: password updated successfully
```

Note here if we type the same password, system will ask again for new password. 

Normally in many Linux systems root password is not set by default, you can set root password using following command 

```
dbit@Tayyabali:~$ sudo passwd
[sudo] password for dbit: 
New password: 
Retype new password: 
passwd: password updated successfully

```

If you want to change password for another user then you can use following command

```
dbit@Tayyabali:~$ sudo passwd ubuntu
New password: 
Retype new password: 
passwd: password updated successfully
```

Lets see some of the other usages of ```passwd``` command 

To check users information 

```
dbit@Tayyabali:~$ sudo passwd -S ubuntu
ubuntu P 02/23/2022 0 99999 7 -1
```
Lets see whats shown in the above output 

+ ubuntu - user name
+ P - Field indicates if the user account has a locked password (L), has
           no password (NP), or has a usable password (P)
+ 02/23/2022 - This field is showing when the password was changed last time 
+ Min, Max age for the password and warning period, and inactivity period

Please Note you need sudo permissions to run most of the user management commands 

To check all users information 

```
dbit@Tayyabali:~$ sudo passwd -Sa
root P 02/23/2022 0 99999 7 -1
daemon L 08/19/2021 0 99999 7 -1
......

```

You can delete users password using -d option

```
dbit@Tayyabali:~$ sudo passwd -d ubuntu
passwd: password expiry information changed.
```

Using -e option you immediately force user to change password on next login

```
ubuntu@Tayyabali:/home/dbit$ sudo passwd -e ubuntu
passwd: password expiry information changed.
ubuntu@Tayyabali:/home/dbit$ exit
exit

dbit@Tayyabali:~$ su ubuntu 
You are required to change your password immediately (administrator enforced)
New password: 
Retype new password: 
You must choose a longer password
New password: 
Retype new password:    

```
As you can see above we have forced ubuntu user to change the password as soon as he logs in 

Lock and unlock users password as shown below 

```
dbit@Tayyabali:~$ sudo passwd -l ubuntu 
passwd: password expiry information changed.
dbit@Tayyabali:~$ su ubuntu
Password: 
su: Authentication failure
dbit@Tayyabali:~$ sudo passwd -u ubuntu 
passwd: password expiry information changed.
dbit@Tayyabali:~$ su ubuntu 
Password: 

```
When you lock the password users wont be able to login

You can set inactive days for password using ```passwd -i 10 ubuntu ```
Users password will get expired after 10 days if not changed 

### useradd


### adduser 

adduser is userfriendly way to add the user to the system. Only root user or sudoers can ass the users into the syste.

```
dbit@Tayyabali:~$ sudo adduser ubuntu2
Adding user `ubuntu2' ...
Adding new group `ubuntu2' (1002) ...
Adding new user `ubuntu2' (1002) with group `ubuntu2' ...
The home directory `/home/ubuntu2' already exists.  Not copying from `/etc/skel'.
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for ubuntu2
Enter the new value, or press ENTER for the default
	Full Name []: Ubuntu2
	Room Number []: 
	Work Phone []: 
	Home Phone []: 
	Other []: 
Is the information correct? [Y/n] Y
```

### userdel

To remove user from the system we can use userdel command, It will not delete the users files and data 

```
dbit@Tayyabali:~$ sudo deluser ubuntu2
Removing user `ubuntu2' ...
Warning: group `ubuntu2' has no more members.
Done.
```
To delete home and user data use following command 

```
sudo deluser --remove-home username
```

### usermod

Using usermode command you can do following 

1. Change home directory of the user 
2. Lock and unlock the user and 
3. Expire password of users 
4. Edit groups
5. Change the login name 
6. Set password for the user 
7. Assign shell to a user 
8. Change the id of the user 

Examples 



### groupadd

### groupmod

### groupdel

### gpasswd

### chown

### chage

### chgrp

### chfn

Using the chfn you can change the realname of the user and its related information also

# Purpose  
Take note of Linux Directory Structure  

# Table of Contents  
[Linux Directory Structure](#linux-directory-structure)  


# Linux Directory Structure  
[Linux Directory Structure Explained for Beginners July 11, 2019](https://linuxhandbook.com/linux-directory-structure/?fbclid=IwAR223NcVaIIJ8uR42hKo02Uj4Mi7Z8b4sB7ce3dCCfMuV1Pz_fuDk1IucPs)  

## /bin – Binaries  
```
The ‘/bin’ directly contains the executable files of many basic shell commands like ls, cp, cd etc. Mostly the programs are in binary format here and accessible by all the users in the Linux system.
```
[all the users in the Linux system](https://linuxhandbook.com/linux-list-users/)  

## /dev – Device files  
```
This directory only contains special files, including those relating to the devices. 
These are virtual files, not physically on the disk.

Some interesting examples of these files are:

    /dev/null: can be sent to destroy any file or string
    /dev/zero: contains an infinite sequence of 0
    /dev/random: contains an infinite sequence of random values
```

## /etc – Configuration files  
```
The /etc directory contains the core configuration files of the system, use primarily by the administrator and services, such as the password file and networking files.

If you need to make changes in system configuration (for example changing the hostname), 
this is where you’ll find the respective files.
```

## /lib – Shared libraries  
```

Libraries are basically codes that can be used by the executable binaries. 
The /lib directory holds the libraries needed by the binaries in /bin and /sbin directories.

Libraries needed by the binaries in the /usr/bin and /usr/sbin are located in the directory /usr/lib.
```

## /sbin – System binaries  
```
This is similar to the /bin directory. 
The only difference is that is contains the binaries that can only be run by root or a sudo user. 
You can think of the ‘s’ in ‘sbin’ as super or sudo.
```

![alt tag](https://i2.wp.com/linuxhandbook.com/wp-content/uploads/linux-system-directoies-poster.png?resize=724%2C1024&ssl=1)  


# Troubleshooting


# Reference


* []()  
![alt tag]()  

# h1 size

## h2 size

### h3 size

#### h4 size

##### h5 size

*strong*strong  
**strong**strong  

> quote  
> quote

- [ ] checklist1
- [x] checklist2

* 1
* 2
* 3

- 1
- 2
- 3

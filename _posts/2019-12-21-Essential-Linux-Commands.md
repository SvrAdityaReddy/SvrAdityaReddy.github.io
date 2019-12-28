---
title: Essential-Linux-Commands
comments: true
# other options
---

In this post we will see essential commands, I think which are very useful for developers in Linux.

### Changing User

Here we use ***su*** command to change user in Linux. See [man page for su](http://man7.org/linux/man-pages/man1/su.1.html) for more details 

```bash

$ su - userName

```

### Environment variables

We use use ***env*** command to see the environment variables. See [man page for env](http://man7.org/linux/man-pages/man1/env.1.html) for more details

```bash

$ env

```

### Changing Directory

We use ***cd*** command to change directory. See [man page for cd](http://man7.org/linux/man-pages/man1/cd.1p.html) for more details

#### To change to home directory of current user

```bash

$ cd ~

```

#### To change to previous working directory

The following command use _OLDPWD_ environment variable to know the previous working directory. 

```bash

$ cd -

```

#### To change to root directory

```bash

$ cd /

```

### Transfer Folder/Files from one Host to other Host

Here we use _**scp**_ command to transfer files across hosts. See [man page for scp](http://man7.org/linux/man-pages/man1/scp.1.html) for more details

#### scp command to copy a file

```bash

$ scp user1@host1IPAddr:absolutePath1/fileName user2@host2IPAddr:absolutePath2

```

#### scp command to copy all files in a folder

```bash

$ scp user1@host1IPAddr:absolutePath1/* user2@host2IPAddr:absolutePath2

```

#### scp command to copy folder

```bash

$ scp -r user1@host1IPAddr:absolutePath1 user2@host2IPAddr:absolutePath2

```

### Finding locations of a file 

Here we use _**find**_ command to find the location/path where a file exists. See [man page for find](http://man7.org/linux/man-pages/man1/find.1.html) for more details

#### find command to find a file from root folder 

```bash

$ find -name fileName /

```

#### find command to find a file from current folder 

```bash

$ find -name fileName .

```

### Search for a string recursively in all files and show it's occurences in files with line numbers

Here we use ***grep*** command to search for a string recursively in all files and show it's occurences in files with line numbers.
See [man page for grep](http://man7.org/linux/man-pages/man1/grep.1p.html) for more details

```bash

$ grep -rn "word_to_search" /path

```

### Finding which executable current environment referring to

Here we use ***which*** command to find the location of the executable used in current environment. ***which*** command looks for **PATH** variable to find the location of the executable used in current environment. See [man page for which](https://linux.die.net/man/1/which) for more details

```bash

$ which python

```

### Finding location of executable

Here we use ***whereis*** command to find the locations of the executable used. ***where*** command looks for ***common Linux locations***, **PATH**, **MANPATH** variable to find the locations of the executable. See [man page for whereis](http://man7.org/linux/man-pages/man1/whereis.1.html) for more details

```bash

$ whereis python

```

### Get details of Linux distribution

Here we use ***lsb_release*** command to details of Linux distribution like version. See [man page for lsb_release](http://manpages.ubuntu.com/manpages/bionic/man1/lsb_release.1.html) for more details

```bash

$ lsb_release -a                                                                                                                  
No LSB modules are available.                                                                                                                          
Distributor ID: Ubuntu                                                                                                                                 
Description:    Ubuntu 18.04.3 LTS                                                                                                                     
Release:        18.04                                                                                                                                  
Codename:       bionic

```

### Get File Information like type, 32 bit/64 bit, processor architecture, stripped/unstripped

Here we use ***file*** command to get file Information like type, 32 bit/64 bit, processor architecture, stripped (like removal of debug symbols)/unstripped. See [man page for file](http://man7.org/linux/man-pages/man1/file.1.html) for more details

```bash

$ file libc-2.23.so
libc-2.23.so: ELF 64-bit LSB shared object, x86-64, version 1 (GNU/Linux), dynamically linked, interpreter /lib64/l, BuildID[sha1]=1ca54a6e0d76188105b12e49fe6b8019bf08803a, for GNU/Linux 2.6.32, stripped

```

```bash

$ file libc-2.23.so
libc-2.23.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (GNU/Linux), dynamically linked, interpreter /lib/ld-, BuildID[sha1]=9a6b57c7a4f93d7e54e61bccb7df996c8bc58141, for GNU/Linux 2.6.32, stripped

```

### Get the processes using a file

Here we use ***lsof*** to know the processes using a file. See [man page for lsof](http://man7.org/linux/man-pages/man8/lsof.8.html) for more details

```bash

$ lsof /lib/x86_64-linux-gnu/libc-2.23.so
COMMAND    PID       USER  FD   TYPE DEVICE SIZE/OFF   NODE NAME
systemd      1       root mem    REG  253,1  1868984 528009 /lib/x86_64-linux-gnu/libc-2.23.so
systemd-u  283       root mem    REG  253,1  1868984 528009 /lib/x86_64-linux-gnu/libc-2.23.so
dhclient   662       root mem    REG  253,1  1868984 528009 /lib/x86_64-linux-gnu/libc-2.23.so

```

### To know dependent shared objects

Here we use ***readelf*** to know the dependent shared objects of a shared object or executable. See [man page for readelf](http://man7.org/linux/man-pages/man1/readelf.1.html) for more details

```bash

$ readelf -d /bin/ls | grep NEEDED
 0x0000000000000001 (NEEDED)             Shared library: [libselinux.so.1]
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]

```

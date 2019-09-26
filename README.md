# Purpose
Take note of Linux CLI

# Table of Content
[ps command](#ps-command)  
[top command](#top-command)  
[du df command](#what-is-the-difference-between-du-and-df-in-linux)  
[IP/default gateway/DNS Setting](#ipdefault-gatewaydns-setting)  
[Ubunut 如何使用 tracert ?](#ubunut-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-tracert-)  
[WIFI 固定IP 參數設定](#wifi-%E5%9B%BA%E5%AE%9Aip-%E5%8F%83%E6%95%B8%E8%A8%AD%E5%AE%9A)  
[How to Use "Script" Command To Record Linux Terminal Session](#how-to-use-script-command-to-record-linux-terminal-session)  
[cannot create temp file for here-document: No space left on device](#cannot-create-temp-file-for-here-document-no-space-left-on-device)  
[make, make clean and make V=s](#make-make-clean-and-make-vs)
[Bash script and /bin/bash^M: bad interpreter: No such file or directory](#)

[Reference](#reference)  

# List CPU and MEM resouce occupation rate ranking
* [Linux 用 ps 與 top 指令找出最耗費 CPU 與記憶體資源的程式 2016/12/22](https://blog.gtwang.org/linux/ps-top-find-processes-by-cpu-memory-usage/)

## ps command
```
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
```
-e 參數是代表輸出所有行程的資訊，而 -o 參數則是用來指定輸出欄位用的，
* pid：行程 ID（process ID）。
* ppid：父行程 ID（parent process ID）。
* cmd：程式名稱。
* %mem：記憶體使用量（百分比）。
* %cpu：CPU 使用量（百分比）。
而 --sort 參數則是指定排序的依據欄位，預設會依照數值由小到大排序

![alt tag](https://i.imgur.com/sFCCN6O.jpg)

## top command
```
top -b -o +%MEM | head -n 17
```
其中 -b 參數是 batch 模式的意思，
而 -o 參數則是設定以記憶體用量來排序行程，
最後面的 head -n 17 則是篩選 top 輸出的文字內容，只保留前 17 行

![alt tag](https://i.imgur.com/ubNQfjN.jpg)

如果程式當掉無法關閉的話，就可以使用 kill 或 killall 這類的指令，中止不正常程式的執行，由於上面的報表中都有每個程式的 PID，
所以使用 PID 來中止特定的程式是最直接的方式。

# What is the difference between DU and DF in Linux?
* [What is the difference between DU and DF in Linux?](https://www.quora.com/What-is-the-difference-between-DU-and-DF-in-Linux)
> Disk Usage. It walks through directory tree and counts the sum size of all files therein. It may not output exact information due to the possibility of unreadable files, hard links in directory tree, etc. It will show information about the specific directory requested. Think, 
*"How much disk space is being used by these files?"*

> Disk Free. Looks at disk used blocks directly in file system metadata. Because of this it returns much faster that du but can only show info about the entire disk/partition. Think, 
*"How much free disk space do I have?"*

![alt tag](https://i.imgur.com/Sd3Icdm.jpg)

# IP/default gateway/DNS Setting
* 1 修改 IP address
```
(先用
# ifconfig -a⋯⋯
看系統可用的網路 device, 假如是 eth0 的話)

及時生效:
# ifconfig eht0 192.168.0.20 netmask 255.255.255.0
啟動時生效:
# vi /etc/sysconfig/netowrk-scripts/ifcfg-eth0
DEVICE=eth0
BOOTPROTO=none
BROADCAST=192.168.0.255
IPADDR=192.168.0.30 <== 改成新 IP
NETMASK=255.255.255.0 <== 改為新的 netmask
GATEWAY=192.168.0.254 <== 改為新的 gateway
```

* 2 修改 default gateway
```
及時生效
# route add default gw 192.168.0.1
啟動生效:
# vi /etc/sysconfig/network-scripts/ifcfg-eth0
GATEWAY=192.168.0.254
```

* 3 修改 DNS
```

# vi /etc/resolv.conf (修改後可及時生效, 重新啟動也有效)
search
nameserver 168.95.1.1
```  

* 4 重新啟動網路服務
```
# /etc/init.d/network restart
```
# Ubunut 如何使用 tracert ?   
[Ubunut 如何使用 tracert ? 2009-11-01](https://www.arthurtoday.com/2009/11/tracert-in-linux.html)  
```
如果使用 traceroute 指令，就要另外安裝才行，安裝的指令如下，而用法則是和 Windows 的 tracert 一模一樣的，只要在 traceroute 指令的後面跟著網址或 IP 位址即可。

sudo apt-get install traceroute 
```
# WIFI 固定IP 參數設定  
[[linux] WIFI 固定IP 參數設定 9月 15, 2013](http://timfan1121.blogspot.com/2013/09/linux-wifi-ip.html)  
```
以下是我的WIFI設定方式路徑是/etc/network/interfaces

auto lo

iface lo inet loopback
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet static
address 192.168.20.186
netmask 255.255.255.0
getway 192.168.20.1
wpa-ssid "you ssid"
wpa-psk "87654321"

iface default inet dhcp
```

# How to Use "Script" Command To Record Linux Terminal Session  
[How to Use "Script" Command To Record Linux Terminal Session June 14, 2017](https://linoxide.com/linux-command/script-command-recorder/)  

## 1. Record your terminal session  
```
# script shell_record1
Script started, file is shell_record1
```
It indicates that a file shell_record1 is created. Let's check the file 

```
# ls -l shell_*
-rw-r--r-- 1 root root 0 Jun 9 17:50 shell_record1
```

After completion of your task, you can enter exit or Ctrl-d to close down the script session and save the file.  
```
# exit
exit
Script done, file is shell_record1
```

## 2. Check the content of a recorded terminal session  
```
# cat shell_record1 
Script started on Fri 09 Jun 2017 06:23:41 PM UTC
[root@centos-01 ~]# date
Fri Jun 9 18:23:46 UTC 2017
[root@centos-01 ~]# uname -a
Linux centos-01 3.10.0-514.16.1.el7.x86_64 #1 SMP Wed Apr 12 15:04:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
[root@centos-01 ~]# whoami
root
[root@centos-01 ~]# pwd
/root
[root@centos-01 ~]# exit
exit

Script done on Fri 09 Jun 2017 06:25:11 PM UTC
```

## 3. Record several terminal session  
It means you want to record the next steps into the existing file machma_record without deleting its previous content; to do this you will use script -a command to append the new output to the file.  
```
# script -a machma_record
Script started, file is machma_record
```

## 4. Replay a linux terminal session  
To do it, you have to use --timing option of script command when you will start the record. 
```
# script --timing=file_time shell_record1
Script started, file is shell_record1
```

```
# exit
exit
Script done, file is shell_record1
```
Let's see check the content of file_time  
```
# cat file_time 
0.807440 49
0.030061 1
116.131648 1
0.226914 1
0.033997 1
```

# cannot create temp file for here-document: No space left on device
![alt tag](https://i.imgur.com/r6RNU8g.jpg)

[cannot create temp file for here-document: No space left on device ](https://stackoverflow.com/questions/48852381/cannot-create-temp-file-for-here-document-no-space-left-on-device/48861589)  
```
Please try to use commands to resolve your issue:

root@****:~# lsblk

```

[ubuntu “No space left on device” but there is tons of space Mar 12, 2016](https://stackoverflow.com/questions/18706398/ubuntu-no-space-left-on-device-but-there-is-tons-of-space)  
```
ubuntu@ip-10-0-2-108:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1       99G  6.5G   88G   7% /
udev            3.7G  8.0K  3.7G   1% /dev
tmpfs           1.5G  184K  1.5G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.7G     0  3.7G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/xvdb       414G  199M  393G   1% /mnt
overflow        1.0M  1.0M     0 100% /tmp
```

```
ubuntu@ip-10-0-2-108:~$ df -i
Filesystem       Inodes IUsed    IFree IUse% Mounted on
/dev/xvda1      6553600 94227  6459373    2% /
udev             951353   393   950960    1% /dev
tmpfs            953649   274   953375    1% /run
none             953649     3   953646    1% /run/lock
none             953649     1   953648    1% /run/shm
none             953649     1   953648    1% /run/user
/dev/xvdb      27525120    11 27525109    1% /mnt
overflow         953649    12   953637    1% /tmp
```

```
It's possible that you've run out of memory or some space elsewhere and it prompted the system to mount an overflow filesystem, and for whatever reason, it's not going away.

Try unmounting the overflow partition:
umount /tmp

OR

umount overflow
```

# make, make clean and make V=s  
[make 及 make clean 的作用 Jun 12, 2018](https://www.opencli.com/linux/make-make-clean)  

```
# ./configure
# make
# make install 
```

```
make
一般上, make 是 make all 的簡寫，它根據 makefile 的規則，將 C/C++ 檔案編譯成 .o 檔案，然後進一步產生可執行檔。
```

```
make clean
如果之前曾經編譯過，make clean 可以將之前產生的可執行檔及其他檔案刪除, 有時發現重新編譯出來的檔案沒有更新, 可以先執行 make clean。
```
[why openwrt use "V=s" in command line Aug 31, 2014](https://stackoverflow.com/questions/25578451/why-openwrt-use-v-s-in-command-line)  
```
Troubleshooting

First get more information on the problem using the make option "make V=s".
```

# How to Kill a Process from the Command Line  
[How to Kill a Process from the Command Line May 15, 2018](https://www.linux.com/tutorials/how-kill-process-command-line/)  
## Locating the process  
```
There are two commands I use to locate a process: top and ps. Top is a tool every administrator should get to know. With top, you get a full listing of currently running process. From the command line, issue top to see a list of your running processes (Figure 1).
```
![alt tag](https://lcom.static.linuxfound.org/sites/lcom/files/killa.jpg)  

```
ps aux | grep chrome
```
```
The aux options are as follows:

    a = show processes for all users

    u = display the process’s user/owner

    x = also show processes not attached to a terminal

```
## Killing the process  
```
Now we come to the task of killing the process. We have two pieces of information that will help us kill the errant process:

    Process name

    Process ID

Which you use will determine the command used for termination. There are two commands used to kill a process:

    kill – Kill a process by ID

    killall – Kill a process by name

```

![alt tag](https://lcom.static.linuxfound.org/sites/lcom/files/killc.jpg)  

Signal Name | Single Value | Effect
------------------------------------ | --------------------------------------------- | ---------------------------------------------
SIGHUP | 1 | Hangup
SIGINT | 2 | Interrupt from keyboard
SIGKILL | 9 | Kill signal
SIGTERM | 15 | Termination signal
SIGSTOP | 17, 19, 23 | Stop the process

## How to kill a daemon process in linux?  
[How to kill a daemon process in linux? Jul 13, 2016](https://askubuntu.com/questions/797957/how-to-kill-a-daemon-process-in-linux)  
```
I figured it out. To see the processes, I used:

ps -ef | grep a.out

After this I used kill -9 pid to kill those processes.
```
# Bash script and /bin/bash^M: bad interpreter: No such file or directory  
[Not able to execute a .sh file: /bin/bash^M: bad interpreter Jun 7, 2013](https://askubuntu.com/questions/304999/not-able-to-execute-a-sh-file-bin-bashm-bad-interpreter)  
```
The script indicates that it must be executed by a shell located at /bin/bash^M. There is no such file: it's called /bin/bash.

The ^M is a carriage return character. Linux uses the line feed character to mark the end of a line, whereas Windows uses the two-character sequence CR LF. Your file has Windows line endings, which is confusing Linux.

Remove the spurious CR characters. You can do it with the following command:
```
```
sed -i -e 's/\r$//' create_mgw_3shelf_6xIPNI1P.sh
```
[Bash script and /bin/bash^M: bad interpreter: No such file or directory Apr 20, 2015](https://stackoverflow.com/questions/14219092/bash-script-and-bin-bashm-bad-interpreter-no-such-file-or-directory)  
```
Try running dos2unix on the script:

http://dos2unix.sourceforge.net/

Or just rewrite the script in your Unix env using vi and test.

Unix uses different line endings so can't read the file you created on Windows. Hence it is seeing ^M as an illegal character.

If you want to write a file on Windows and then port over, make sure your editor is set to create files in UNIX format.

In notepad++ in the bottom right of the screen, it tells you the document format. By default, it will say Dos\Windows. To change it go to

    settings->preferences
    new document / default directory tab
    select the format as unix and close
    create a new document
```

# Reference
* [ROS 軟路由PPPOE設置 2018-11-17](https://kknews.cc/other/p9pyov8.html)


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

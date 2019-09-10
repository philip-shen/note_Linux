# Purpose
Take note of Linux on VMware

# Table of Content
[Install SSH Server](#install-ssh-server)  
[How to connect wireless network adapter to VMWare workstation?](#how-to-connect-wireless-network-adapter-to-vmware-workstation)  

[Configure networks](#configure-networks)  
[Add a virtual network adapter](#add-a-virtual-network-adapter)  
[Configure bridged networking](#configure-bridged-networking)  
[Configure NAT networking](#configure-nat-networking)  
[Configure host-only networking](https://github.com/philip-shen/note_Linux/tree/master/VMware#configure-host-only-networking)  

[VMware網路連線](#vmware%E7%B6%B2%E8%B7%AF%E9%80%A3%E7%B7%9A)  

[[ESXI5.5] VM擴大磁碟空間](#esxi55-vm%E6%93%B4%E5%A4%A7%E7%A3%81%E7%A2%9F%E7%A9%BA%E9%96%93)
[選擇要擴容的VM](#%E9%81%B8%E6%93%87%E8%A6%81%E6%93%B4%E5%AE%B9%E7%9A%84vm)  
[修改容量](#%E4%BF%AE%E6%94%B9%E5%AE%B9%E9%87%8F)  
[建立分割區](#%E5%BB%BA%E7%AB%8B%E5%88%86%E5%89%B2%E5%8D%80)  
[加入](#%E5%8A%A0%E5%85%A5)  

[Reference](#reference)  

# VMware related stuffs  

# Install SSH Server  
```
1.安裝 OpenSSH Server 
sudo apt-get install openssh-server
或
sudo aptitude install openssh-server

2.取消 root 的登入權限
這是基於安全的考量， 一般都不會設定讓 root 可以連進來， 不然，駭客就會很方便的哩 ！ 首先，打開在 /etc/ssh/sshd_config 的 SSH 設定檔，然後，找到下面這一行，把它的 yes 改成 no 之後，就把它存檔起來。

＃PermitRootLogin Yes
或是
PermitRootLogin No

3.設定可以連線的主機

打開 /etc/hosts.allow 檔，把允許的主機 IP 加進來， 以阿舍想要讓 192.168.1.88 這台機器可以連進來為例，就輸入下面這樣的一行,然後就存檔起來。
sshd:192.168.1.88:allow

再來， 再打開 /etc/hosts.deny 檔，把下面這一行給加進去，這樣其它的主機都會被設為拒絕連線，所以，這台主機就只有上面設定的 192.168.1.88 那一台可以連進來了哩。
sshd:all:deny

4.重啟 SSH Server
用下面的指令來重啟 SSH Server 之後，就算安裝設定完成了哩 !
sudo /etc/init.d/ssh restart
```
# Configure networks
## Add a virtual network adapter  
* [Add a virtual network adapter ](https://geek-university.com/vmware-player/add-a-virtual-network-adapter/)  
- Bridged: Connected directly to the physical network – a virtual machine is connected to the network by using the network adapter on the host system. This networking configuration is often the easiest way to give your virtual machine access to the network.  
- NAT: Used to share the host’s IP address – a virtual machine does not have its own IP address on the external network. Instead, a separate private network is set up on the host system and a virtual machine gets an IP address on this private network from the virtual DHCP server. The virtual machine and the host system share a single network identity that is not visible on the external network. When the virtual machine sends a request to access a network resource, it appears to the network resource as if the request is coming from the host system.  
- Host-only: A private network shared with the host – a network that is completely contained within the host computer is created. This networking configuration provides a network connection between the virtual machine and the host system by using a virtual network adapter that is visible on the host operating system.  
![alt tag](https://geek-university.com/wp-content/images/vmware-player/network_adapter_type.jpg?x66712)

## Configure bridged networking  
* [Configure bridged networking ](https://geek-university.com/vmware-player/configure-bridged-networking/)  
If you use the virtual machine on a laptop, check the Replicate physical network connection state checkbox. This option causes the IP address to be renewed when you move from one wired or wireless network to another.  
![alt tag](https://geek-university.com/wp-content/images/vmware-player/bridged_networking_configuration.jpg?x66712)

## Configure NAT networking  
* [Configure NAT networking ](https://geek-university.com/vmware-player/configure-nat-networking/)  

In NAT (Network Address Translation) networking, a virtual machine does not have its own IP address on the external network. Instead, a separate private network is set up on the host system and a virtual machine gets its IP address on this private network from the virtual DHCP server. The virtual machine and the host system share a single network identity that is not visible on the external network. When the virtual machine sends a request to access a network resource, it appears to the network resource as if the request is coming from the host system.  
A NAT network (VMnet8) is set up for you when you install VMware Player. The host system has a virtual network adapter on the NAT network that enables the host system and virtual machines to communicate. The NAT device passes network data between virtual machines and the external network, identifies incoming data packets intended for each virtual machine, and sends them to the appropriate destination.  

![alt tag](https://geek-university.com/wp-content/images/vmware-player/nat_configuration.jpg?x66712)

## Configure host-only networking  
* [Configure host-only networking ](https://geek-university.com/vmware-player/configure-host-only-networking/)  

In host-only networking, a network completely contained within the host computer is created. This networking configuration provides a network connection between the virtual machine and the host system by using a virtual network adapter that is visible on the host operating system. The virtual DHCP server provides IP addresses on the host-only network.  
A host-only network (VMnet1) is set up for you when you install VMware Player. In the default configuration, a virtual machine is isolated and cannot connect to the Internet.  

![alt tag](https://geek-university.com/wp-content/images/vmware-player/host_only_networking_configuration.jpg?x66712)

# Ethernet device not managed 

# How to connect wireless network adapter to VMWare workstation?  
* [How to connect wireless network adapter to VMWare workstation? Nov 13, 2011](https://stackoverflow.com/questions/4601762/how-to-connect-wireless-network-adapter-to-vmware-workstation) 

Workstation doesn't have a wireless NIC type, so direct wireless hardware access is out. If you just want to access through the extant host wireless connection, bridging is your answer.

I think the only way to get a wireless NIC dedicated to the VM would be using a USB wireless NIC as a USB-passthrough device on the VM. When you have Workstation running and a USB device plugged in, it should give you an option to change whether that device is connected to the host or to the VM.

# VMware網路連線
[VMware網路連線](http://oblivious9.pixnet.net/blog/post/177362092-vmware%E7%B6%B2%E8%B7%AF%E9%80%A3%E7%B7%9A)
![alt tag](https://pic.pimg.tw/oblivious9/1447998264-2950343439.png)  
![alt tag](https://pic.pimg.tw/oblivious9/1447998264-794726665.png)  

# [ESXI5.5] VM擴大磁碟空間  
[[ESXI5.5] VM擴大磁碟空間 May 8, 2017](http://n.sfs.tw/content/index/11043)  
## 選擇要擴容的VM  
![alt tag](http://n.sfs.tw/uploads/content/170508090961/P9335528.png)  

## 修改容量  
![alt tag](http://n.sfs.tw/uploads/content/170508090961/P300_P8599518.png)  

## 建立分割區 
```
原本的容量是40GB，並不會因為你擴容而改變

# df -h
檔案系統             容量  已用  可用 已用% 掛載點
/dev/mapper/cl-root   37G 1021M   36G    3% /
devtmpfs             2.4G     0  2.4G    0% /dev
tmpfs                2.4G     0  2.4G    0% /dev/shm
tmpfs                2.4G  8.5M  2.4G    1% /run
tmpfs                2.4G     0  2.4G    0% /sys/fs/cgroup
/dev/sda1           1014M  139M  876M   14% /boot
tmpfs                480M     0  480M    0% /run/user/0
```

```
要手動調整，查看

# fdisk -l

Disk /dev/sda: 161.1 GB, 161061273600 bytes, 314572800 sectors  <==sda全部空間
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O 大小 (最小/最佳化)：512 位元組 / 512 位元組
Disk label type: dos
磁碟識別碼：0x000e95e2

所用裝置 開機      開始         結束      區塊   識別號  系統
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM

Disk /dev/mapper/cl-root: 39.7 GB, 39720058880 bytes, 77578240 sectors  <==目前區塊空間
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O 大小 (最小/最佳化)：512 位元組 / 512 位元組

Disk /dev/mapper/cl-swap: 2147 MB, 2147483648 bytes, 4194304 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O 大小 (最小/最佳化)：512 位元組 / 512 位元組
```

```
先建立主要磁區(Linux LVM磁區)

# fdisk /dev/sda
```

```
命令 (m 以獲得說明)：p

Disk /dev/sda: 161.1 GB, 161061273600 bytes, 314572800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O 大小 (最小/最佳化)：512 位元組 / 512 位元組
Disk label type: dos
磁碟識別碼：0x000e95e2

所用裝置 開機      開始         結束      區塊   識別號  系統
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM
```

```
預設會有 sda1, sda2
```

```
命令 (m 以獲得說明)：n
Partition type:
   p   primary (2 primary, 0 extended, 2 free)
   e   extended
Select (default p): p
分割區編號 (3,4, default 3): 3
起初 sector (83886080-314572799, 預設 83886080)：<按ENTER>
使用預設值 83886080
最後 sector, +sectors 或 +大小{K,M,G} (83886080-314572799, 預設 314572799)：<按ENTER>
使用預設值 314572799
Partition 3 of type Linux and of size 110 GiB is set

命令 (m 以獲得說明)：t
分割區編號 (1-3, default 3): 3
Hex code (type L to list all codes): 8e <可按L查看partition type，輸入8e後按ENTER>
Changed type of partition 'Linux' to 'Linux LVM'


命令 (m 以獲得說明)：w
分割表已變更！

呼叫 ioctl() 以重新讀取分割表。WARNING: Re-reading the partition table failed with error 16: 裝置或系統資源忙碌中.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
同步磁碟。
```

```
查看是否建立成功

# fdisk -l

Disk /dev/sda: 161.1 GB, 161061273600 bytes, 314572800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O 大小 (最小/最佳化)：512 位元組 / 512 位元組
Disk label type: dos
磁碟識別碼：0x000e95e2

所用裝置 開機      開始         結束      區塊   識別號  系統
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM
/dev/sda3        83886080   314572799   115343360   8e  Linux LVM

重開機
```

## 加入  
```
把裝置加入物理容積(Physical Volume)中

# pvcreate /dev/sda3
  Physical volume "/dev/sda3" successfully created.
```

```
查看我的容積群(Volume Group)，注意我的VG name是"cl"而不是" VolGroup00"

# vgdisplay
  --- Volume group ---
  VG Name               cl
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               39.00 GiB
  PE Size               4.00 MiB
  Total PE              9983
  Alloc PE / Size       9982 / 38.99 GiB
  Free  PE / Size       1 / 4.00 MiB
  VG UUID               j2Krvn-2RNI-RtVt-BcId-fkPX-SZ1l-2j3XCu
```

```
延伸物理容積到容積群

# vgextend cl /dev/sda3
  Volume group "cl" successfully extended
```

```
再查看我的物理容積

# vgdisplay cl
  --- Volume group ---
  VG Name               cl
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               148.99 GiB
  PE Size               4.00 MiB
  Total PE              38142
  Alloc PE / Size       9982 / 38.99 GiB
  Free  PE / Size       28160 / 110.00 GiB
  VG UUID               j2Krvn-2RNI-RtVt-BcId-fkPX-SZ1l-2j3XCu

紅字部分注意一下，目前有多的110GB容積閒置
```

```
延伸邏輯容積，110G是我要延伸的大小

# lvextend -L+110G /dev/cl/root
  Size of logical volume cl/root changed from 36.99 GiB (9470 extents) to 146.99 GiB (37630 extents).
  Logical volume cl/root successfully resized.
```

```
動態增加容積，依系統不同試看下面幾個指令

# ext2online /dev/cl/root
-bash: ext2online：命令找不到

# resize2fs /dev/cl/root
resize2fs 1.42.9 (28-Dec-2013)
resize2fs: Bad magic number in super-block while trying to open /dev/cl/root
Couldn't find valid filesystem superblock.

# xfs_growfs /dev/cl/root
meta-data=/dev/mapper/cl-root    isize=512    agcount=4, agsize=2424320 blks
         =                       sectsz=512   attr=2, projid32bit=1
         =                       crc=1        finobt=0 spinodes=0
data     =                       bsize=4096   blocks=9697280, imaxpct=25
         =                       sunit=0      swidth=0 blks
naming   =version 2              bsize=4096   ascii-ci=0 ftype=1
log      =internal               bsize=4096   blocks=4735, version=2
         =                       sectsz=512   sunit=0 blks, lazy-count=1
realtime =none                   extsz=4096   blocks=0, rtextents=0
data blocks changed from 9697280 to 38533120
```

```
查看
# df -h
檔案系統             容量  已用  可用 已用% 掛載點
/dev/mapper/cl-root  147G 1022M  146G    1% /
```

```
重開機，完成擴容
```


[Extending a logical volume in a virtual machine running Red Hat or Cent OS (1006371) 11/25/2016](https://kb.vmware.com/s/article/1006371)  
[Linux中VMware虛擬機器硬碟空間擴大方法 2018-10-02](https://www.itread01.com/p/215363.html)  

# Reference
* [VMware Workstation 12 Player安裝Ubuntu 15.04 (一) 20150909](https://blog.xuite.net/yh96301/blog/341981056-VMware+Workstation+12+Player%E5%AE%89%E8%A3%9DUbuntu+15.04+%28%E4%B8%80%29)  
* [VMware Workstation 12 Player安裝Ubuntu 15.04 (二) 20150910](https://blog.xuite.net/yh96301/blog/341981594)  
* [ Ubuntu 安裝與設定 ssh server 6月 26, 2012 ](https://www.ewdna.com/2012/06/ubuntu-ssh-server.html)  
* [Ubuntu 安裝和啟用 SSH 登入 2010-08-22 ](https://www.arthurtoday.com/2010/08/ubuntu-ssh.html)  
* [Ubuntu 用 SSH + 憑證登入遠端主機  2009-11-01](https://www.arthurtoday.com/2009/11/ssh-linux-client.html)  
* [Ethernet device not managed ](https://askubuntu.com/questions/882806/ethernet-device-not-managed)  
* [Error editing connection Unable to find a connection with UUID ('null') Feb 16, 2017](https://askubuntu.com/questions/688556/error-editing-connection-unable-to-find-a-connection-with-uuid-null)  

* [VMwareのIPv6 NATを使ってみたら、IPv4 onlyホストにつながらなくなる(from Windows 10 VM) 2016-12-19](https://qiita.com/ip6/items/af4677e9afe9661b521d)  

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

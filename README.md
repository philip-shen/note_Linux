# Purpose
Take note of Linux CLI

# Table of Content
[ps command](#ps-command)  
[top command](#top-command)  
[du df command](#what-is-the-difference-between-du-and-df-in-linux)  
[IP/default gateway/DNS Setting](#ipdefault-gatewaydns-setting)  
[Ubunut 如何使用 tracert ?](#ubunut-%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8-tracert-)  

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

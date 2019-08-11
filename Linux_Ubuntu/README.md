# Purpose
Take note of Ubuntu stuffs

# Table of Content
[ubuntu 16.04 Networking Setting](#ubuntu-1604-networking-setting)  
[網卡改名為 eth0](#%E7%B6%B2%E5%8D%A1%E6%94%B9%E5%90%8D%E7%82%BA-eth0)  
[Ubuntu IPv6網路設定](#ubuntu-ipv6%E7%B6%B2%E8%B7%AF%E8%A8%AD%E5%AE%9A)  
[IPv6 Setting SLAAC DHCPv6](#ipv6-setting-slaac-dhcpv6)
[IPv6 - Set Up An IPv6 LAN with Linux](#ipv6---set-up-an-ipv6-lan-with-linux)

[VMware Workstation 12.x + ubuntu 16.04 + NAT 不 work](#vmware-workstation-12x--ubuntu-1604--nat-%E4%B8%8D-work)  
[Ubuntu 16.04開機直接進入文字模式 ](#ubuntu-1604%E9%96%8B%E6%A9%9F%E7%9B%B4%E6%8E%A5%E9%80%B2%E5%85%A5%E6%96%87%E5%AD%97%E6%A8%A1%E5%BC%8F)  

# ubuntu 16.04 Networking Setting  
[ubuntu 12.04 LTS desktop 64位元版本 – 網路設定  一月 9, 2014](https://andersonwang.wordpress.com/2014/01/09/ubuntu-12-04-lts-desktop-64%E4%BD%8D%E5%85%83%E7%89%88%E6%9C%AC-%E7%B6%B2%E8%B7%AF%E8%A8%AD%E5%AE%9A/)  
剛剛安裝完，此時應該是 DHCP Client  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb78.png?w=644&h=399&zoom=2)  

eth0 改成 static IP  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb79.png?w=644&h=364&zoom=2)  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb80.png?w=644&h=396&zoom=2)  

設定 IP Alias，在設定檔新增加一段  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb81.png?w=644&h=481&zoom=2)  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb82.png?w=644&h=412&zoom=2)  

也可以將 eth0 設定成為 DHCP Client，再加上 IP Alias  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb83.png?w=644&h=340&zoom=2)  
![alt tag](https://andersonwang.files.wordpress.com/2014/01/image_thumb84.png?w=644&h=415&zoom=2)  

# 網卡改名為 eth0   
[ubuntu 16.04，將網卡改回 eth0 九月 1, 2017](https://andersonwang.wordpress.com/2017/09/01/ubuntu-16-04%EF%BC%8C%E5%B0%87%E7%B6%B2%E5%8D%A1%E6%94%B9%E5%9B%9E-eth0/)  

執行 dmesg 檢查一下  
![alt tag](https://andersonwang.files.wordpress.com/2017/08/image_thumb12.png?w=644&h=97&zoom=2)  

修改 /etc/default/grub  
找到 GRUB_CMDLINE_LINUX 那一行，改成 GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0″  
![alt tag](https://andersonwang.files.wordpress.com/2017/08/image_thumb13.png?w=644&h=433&zoom=2)  

產生新的 grub 設定檔
grub-mkconfig -o /boot/grub/grub.cfg  
![alt tag](https://andersonwang.files.wordpress.com/2017/08/image_thumb14.png?w=644&h=127&zoom=2)  

網卡設定檔 /etc/network/interfaces 也要修改  
![alt tag](https://andersonwang.files.wordpress.com/2017/08/image_thumb15.png?w=644&h=228&zoom=2)  

重新開機試試看  
![alt tag](https://andersonwang.files.wordpress.com/2017/08/image_thumb16.png?w=644&h=420&zoom=2)

# Ubuntu IPv6網路設定     
[Ubuntu IPv6網路設定 2017年 11月 29日](http://www.wkb.idv.tw/moodle/mod/page/view.php?id=10580)  
網路卡設定，打指令--># nano /etc/network/interfaces  
```
# IPv4 configuration
iface eth0 inet static
address 210.201.80.202
netmask 255.255.255.0
gateway 210.201.80.254
dns-nameservers 8.8.8.8 168.95.1.1

#下面藍色字是要新增ipv6環境時加上的設定內容，其中address要看實際的資訊來輸入

# IPv6 configuration
iface eth0 inet6 static
pre-up modprobe ipv6
address 2404:0:40a1:0:215:5dff:fe50:f3f0
netmask 64
```
![alt tag](http://www.wkb.idv.tw/moodle/pluginfile.php/15713/mod_page/content/13/2012-09-06_4.jpg)

重新啟動(# /etc/init.d/networking restart)或是重新開機完，打指令-->ifconfig or ip addr show就可以看到網卡啟動了。
![alt tag](http://www.wkb.idv.tw/moodle/pluginfile.php/15713/mod_page/content/13/2012-09-06_8.jpg)
![alt tag](http://www.wkb.idv.tw/moodle/pluginfile.php/15713/mod_page/content/13/20171126_01.png)

[ubuntu設定ipv6 Jan 21, 2011 ](http://pk5566.blogspot.com/2011/01/ubuntuipv6.html)  
[Linux Server Bind IPv6 設定 12 元月, 2011](http://blogs.yyes.chc.edu.tw/post/2/2723)  
```
ifconfig
看網卡是否支援IPv6
出現inet6 addr表示支援
sudo vi /etc/networkinterfaces
iface eth0 inet6 static
address 2001:288:xxxx::2
netmask 48
gateway 2001:288:xxxx::1
sudo /etc/init.d/networking restart
網路連線測試
以「ping6」指令 ping 到「ipv6.l.google.com」
ping6 2404:6800:8005::6a

DNS 伺服器設定
sudo vi /etc/bind/named.conf
在 options 區段內有些 Bind 版本需加入以下內容：
listen-on-v6 { any; };
DNS 正解檔設定
vi /etc/bind/db.hnps.chc.edu.tw 裡列出正解設定，
IPv6 的寫法除了IP位址不同外，另一差別只是將「A」改成「AAAA」，
加上兩列關於這兩部主機新的設定：
dns             IN      AAAA    2001:288:xxxx::2
www           IN      AAAA    2001:288:xxxx::2

重新啟動DNS
sudo /etc/init.d/bind9 restart
測試
nslookup
> server 163.23.115.xx
Default server: 163.23.115.xx
Address: 163.23.115.xx#53 
```

## IPv6 Setting SLAAC DHCPv6 
[IPv6 and Junos – Stateless Address Autoconfiguration (SLAAC) Dec 2, 2015](https://blog.marquis.co/ipv6-and-junos-stateless-address-autoconfiguration-slaac/) 
```
Configuring SLAAC

Enabling SLAAC with Junos is pretty straightforward. For my example, I’ve got an EX4200 connected to an Ubuntu 14.04LTS ESXi host in Vlan 200.

Before enabling the switch, the host’s interface has to be set to auto
```
```
marquk01@km-vm1:~$ cat /etc/network/interfaces
{...}
# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto

auto eth1
iface eth1 inet6 auto
```
```
IPv6 Neighbors
marquk01@EX4200-A> show ipv6 neighbors 
IPv6 Address                 Linklayer Address  State       Exp Rtr Secure Interface
2001:192:168:2:20c:29ff:fe4f:26c5
                             00:0c:29:4f:26:c5  stale       1110 no no      vlan.200    
fe80::20c:29ff:fe4f:26c5     00:0c:29:4f:26:c5  stale       1039 no no      vlan.200
```
```
Router Advertisements
marquk01@EX4200-A> show ipv6 router-advertisement 
Interface: vlan.200
  Advertisements sent: 4, last sent 00:04:45 ago
  Solicits received: 2, last received 00:04:46 ago
  Advertisements received: 0
```

[Configuring a Dual Stacked DHCP Server Dec 22, 2015](https://blog.marquis.co/configuring-a-dual-stacked-dhcp-server/)  
```

```

[/etc/network/interface での IPv6  Mar 29, 2017](https://qiita.com/kwi/items/1dd8ed8f89255956d7a9)
```
Ubuntu で NetworkManager off 設定なマシンで、IPv6 の付け方を調べたメモ。詳しくは man ページ参照のこと。

/etc/network/interface で設定する。dual stack 環境なので iface を複数書くべし。

inet6 auto というのは、SLAAC なアドレス自動設定を指している。「RAを元によろしく全部やる」という意味ではないことに注意。DNS 設定などは、まだまだDHCPv6で配布するケースが多いと思うので wide-dhcpv6-client パッケージをインストールして、auto にさらに dhcp 1 オプションを追加する。

inet dhcp というのは DHCPv6 でアドレス設定とその他の設定をすることを指している。

まとめると例えばこうなる。IPv6 で auto と dhcp 両方設定して構わない。
```
```
auto br0
iface br0 inet dhcp
 bridge_ports eth0 eth1

iface br0 inet6 auto
 dhcp 1

iface br0 inet6 dhcp
```
[ISC Kea DHCPv6 server 08/02/2016](https://blog.widodh.nl/2016/02/isc-kea-dhcpv6-server/)
```
Ubuntu client

The client was a simple Ubuntu 14.04 client with this network configuration:

auto eth0
iface eth0 inet dhcp
iface eth0 inet6 dhcp

And indeed, it obtained the correct address:

root@ubuntu1404:~# ip addr show dev eth0
2: eth0:  mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 52:54:00:d6:c2:a9 brd ff:ff:ff:ff:ff:ff
    inet 192.168.100.100/24 brd 192.168.100.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 2001:db8::5054:ff:fed6:c2a9/64 scope global deprecated dynamic 
       valid_lft 62sec preferred_lft 0sec
    inet6 fe80::5054:ff:fed6:c2a9/64 scope link 
       valid_lft forever preferred_lft forever
root@ubuntu1404:~#
```

[Ubuntu16.04 インストール後の初期設定メモ 2019-07-03](https://qiita.com/hatayan1126/items/8555333fac205d782aa1)  
```
ipv6無効化

~#
~# cat <<EOF >> /etc/sysctl.conf

# Disable IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1

EOF
~# 
~# sysctl -p
```
[Ubuntu18.04 インストール後の初期設定メモ 2019-07-02](https://qiita.com/hatayan1126/items/c67f87a86f1538bb86af)  
```
ipv6無効化

GRUBの設定変更で対応する。
sysctl.conf で設定しても無効化できないようです。

~#
~# vi /etc/default/grub
　：
GRUB_CMDLINE_LINUX="ipv6.disable=1"
　：
~# 
~# update-grub
```
```
cf. Ubuntu18.04に移行 SSHと静的IPアドレス、IPv6無効化、タイムゾーン設定
```
[Ubuntu18.04に移行 SSHと静的IPアドレス、IPv6無効化、タイムゾーン設定 投稿日: 2018年6月9日(2019年6月16日)](https://rohhie.net/migrate-to-ubuntu-18-04-ssh-and-static-ip-address-ipv6-disablement-time-zone-setting/)

[aptがIPv6で繋ぎにいってしまう問題の対処 2018-09-01](https://qiita.com/sinsi404/items/55c43b8b199eb8e9dd58)  
```
方法3: ネットワークの設定を変更する(失敗)

この方法では再起動後有効にならなかった。

3行追加
/etc/sysctl.conf

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

起動時に設定を有効化するスクリプトを作成する。
/etc/init.d/sysctlp

#!/bin/sh
sysctl -p
exit 0

起動時に自動実行されるように設定する。

$ sudo chmod +x /etc/init.d/sysctlp 
$ sudo update-rc.d sysctlp defaults 
```
[IPv4を無効化する (FreeBSD, Ubuntu 16.04/Linux, Windows 10) 2017-01-12](https://qiita.com/ip6/items/4bf9579acab48670e387)  
```
Ubuntu 16.04 LTS (Linuxカーネル3.3.0)
ちなみにIPv6の無効化は
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
echo 1 > /proc/sys/net/ipv6/conf/default/disable_ipv6
```

```
Windows 10
C:\>netsh interface ipv4 uninstall
```

## IPv6 - Set Up An IPv6 LAN with Linux  
[IPv6 - Set Up An IPv6 LAN with Linux Apr 5, 2015](https://www.jumpingbean.co.za/blogs/mark/set-up-ipv6-lan-with-linux)  
* 1 Set Up an Link Local Only IPv6 LAN with Linux  
```
IPv6 link local addresses have been assigned automatically to any interfaces that you have. 
The IPv6 localhost address (IPv4 127.0.0.1) is ::1/128. 
You can do the same on another host to gets it IPv6 link local address and then 
do a IPv6 ping with "ping6" - note the 6.
	
ping6 fe80::922b:34ff:fe7b:6ff1

The fe80::/64 network prefix is the link local network as explained in the table above. 
It should be the only IPv6 network address you will see across different physical networks. 
In fact every host on an IPv6 network must have an link local address (fe80::/64).
```
**Why do you need a Link Local Address?** 
```
IPv6 configuration is done using layer 3 (network layer) protocols and 
not layer 2 (media layer eg. Ethernet) as with IPv4; 
so a valid IPv6 address is required before any additional configuration can be done. 
Of couese it also allows for zero config simple networks.
```
**Pros and Cons of Link Local Network**  
```
With a link local address you can communicate with other IPv6 hosts 
on the local network segment or broadcast domain. i.e the same switch or 
shared media network. So for a home LAN not connected to the internet this is all that is required. 
You can connect to your printer, Smart TV, PlayStation etc automatically 
using protocols such as UPnP and multicast DNS (ZeroConf).  
Connecting to the internet, or a network in a different physical network 
or logical network, will require a bit more work.
```

* 2 Set Up A Stateless Routable IPv6 Network  

**What is the difference between a ULA and a Global address?**
```
By convention a ULA is not routed over the public internet. Routers on the public IPv6 network 
should refuse to route such traffic in a similar manner to private IPv4 addresses. 
Essentially there should be no routing entries in the routers responsible for internet traffic, 
making them unreachable from outside an organisation.

If you are going to start experimenting with IPv6 there are two reasons to use a ULA
```
  * you should start with a ULA address to avoid any mis-configuration disasters.  
  * It might be hard to get a global IPv6 address assigned to you. There are very few ISP handing out IPv6 network addresses currently so in some cases its the only choice available to you.  

**Unique Local Addresses**
```
One feature of unique local addresses is that they should be different for every network you see. 
Unlike IPv4 where private addresses (196.128/16, 10/8 and 172.16/16) meant there are often networks 
with the same network mask - eg nearly every home and office has a  network with the network mask of 
192.168.1.0/24 address or 10.0.0.0/24 range; you might never see a duplicate IPv6 ULA network address. 
This is because only the first 8 bits of the network prefix are fixed at "fd". 
The remaining 56 bits of the netowrk prefix, the subnet id, can be randomly selected. 
System administrators are meant to create the subnet id themselves. A handy way to generate the subnet id 
for the ULA is to use a site like 
```
[unique-local-ipv6.com](http://unique-local-ipv6.com/). 
```
From here you will get a /48 address range meaning you can have up to 65356 private networks!

Its generally a good idea to use a random subnet id rather than generate one like fd01:1:1:1::0/64 
as this increase your chance of a conflict. 
Why would you be worried about a conflict if these are not routable?
Have you ever had to merge two network that had the same IPv4 address range? 
Have you ever tried to setup a VPN between two network with the same IP network range?
```
**Global Addresses**
```
Global address will be assigned to you by an ISP unless you get your own block and tell your ISP to route it to you. 
So much like you get a public IP address from your ISP for IPv4 you will in future, 
get an IPv6 network address range when you dial up. 

Note: not a single IP address but a whole block of IPv6 addresses. 
Depending on your ISP you may get only one network or be assigned a block with multiple networks. 
In this case the router will received the network address prefix to use on your network. 
It will work the same as for the steps below except instead of a ULA network it will be a global address. 
Note you don't get assigned a full IPv6 address. You get the network prefix.

So to summarise. You will need at least two  IPv6 addresses for each interface if you want to do normal networkng tasks 
like route between network. 
A link local which is always present and at least one ULA or global address or perhaps all three!

For our exercise we will use ULA addresses to setup an IPv6 only LAN.
```

```
So a node now has an ULA IPv6 address and a default gateway and all should be good. 
This is known as stateless address assignment. The router does not assign an address per se. 
It has no idea what IPv6 address the hosts ends up using, only that it is in the provided network. 
Hence the stateless in the term stateless automatic address configuration (SLAAC).
```

```
Steps to Configure the Router Advertisement Service 

The advertisement service can run on any Linux box, but that box will become 
the default route for IPv6 traffic. 
In future your ADSL router will provide router advertisement services. 
First assign the Linux box a static IPv6 address from the ULA network: 
(In the examples that follow I use the fd5f:12c9:2201::/48 ULA routing prefix and 
I have chosen fd5f:12c9:2201:1::/64 as the network prefix. (ie :1 is the subnet id).

Configure a static IPv6 on Ubuntu

	
sudo vi /etc/network/interfaces
 
auto eth0
iface eth0 inet6 static
  address fd5d:12c9:2201:1::1
  netmask 64
  autoconf 0
  dad-attempts 0
  accept_ra 0

Now we need to install the router advertisement service:

Router Advertisement Daemon Configuration

sudo apt-get install radvd

vi /etc/radvd.conf

interface eth0
{
    AdvSendAdvert on;
    prefix fd5d:12c9:2201:1::1/64 {
        AdvOnLink on;
        AdvAutonomous on;
    };
    #Send DNS Server setting - assumes there is a DNS server setup at the address below
    RDNSS fd5d:12c9:2201:1::2{
    };
};
	


Restart the service and then on a client restart the network. 
You should see two IPv6 address on your network card.

 
ip -6 address list

You can ping the router with the ping6 utility:

"ping6 fd5d:12c9:2201:1::1" if this doesn't work try 
"ping6 fd5d:12c9:2201:1::1 -I eth0" -> Use the interface with 
the assigned IPv6 address. We will cover DNS and IPv6 in the net section.

Congratulations you have an IPv6 network up and running! 
If your router is multi honed and has two interfaces with 
IPv6 addresses you will be able to route between the two networks. 
You will need to setup two static IPv6 addresses in /etc/network/interfaces.
```
* 3 Set Up a Stateful ULA IPV6 LAN with DHCP & DNS Services  
```
Sadly the router advertisement service can only provide a network prefix, 
default route and dns server address and not much else.  
To provide the required service we need to use a DHCP server.  
To get the node to use a DHCP server we need to configure the radvd service to tell nodes 
to contact a DHCP server for additional configuration information.

You can configure radvd to tell the nodes to contact the DHCP server for

    configuration info only (stateless) or
    for configuration information and its IP address (stateful)
```
```
 So a DHCP server can be used in a stateless and stateful IPv6 setup. We will use DHCP to send configuration information such as DNS servers and to assign IP addresses since we want to assign fixed IP to well known hosts. 

Edit the /etc/radvd.conf file
	
interface eth0
{
     AdvSendAdvert on;
     AdvManagedFlag on; # get a full IP address from the DHCP server
     AdvOtherConfigFlag on; # get other configuration info from the DHCP server
     prefix fd5d:12c9:2201:1::1/64 {
        AdvOnLink on;
        AdvAutonomous on;
        
    };
};
```

# VMware Workstation 12.x + ubuntu 16.04 + NAT 不 work   
[VMware Workstation 12.x + ubuntu 16.04 + NAT 不 work 九月 8, 2017](https://andersonwang.wordpress.com/2017/09/08/vmware-workstation-12-x-ubuntu-16-04-nat-%E4%B8%8D-work/)  


# Ubuntu 16.04開機直接進入文字模式  
[Ubuntu 16.04開機直接進入文字模式 Jun 24, 2017](https://2formosa.blogspot.com/2017/06/ubuntu-disable-GUI-login.html)
* [how to disable lightdm(display manager) on Ubuntu 16.0.4 LTS](https://askubuntu.com/questions/800239/how-to-disable-lightdmdisplay-manager-on-ubuntu-16-0-4-lts)  
* [How can I show or hide boot messages when Ubuntu starts?](https://askubuntu.com/questions/248/how-can-i-show-or-hide-boot-messages-when-ubuntu-starts)  
```
在Ubuntu 16.04 Desktop版本裝好後想要關閉圖形登入介面
若僅僅用只想要用文字模式，那就直接用下面指令後重開機：
    sudo systemctl set-default multi-user.target

若是希望又回到圖形模式，那就是下指令後重開機：
    sudo systemctl set-default graphical.target


但當進入文字模式的開機狀態，卻又希望可以看到開機訊息，首先要修改 /etc/default/grub 這個檔案裡面的 GRUB_CMDLINE_LINUX_DEFAULT：
    * 1 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
    * 2 GRUB_CMDLINE_LINUX_DEFAULT=
    * 3 GRUB_CMDLINE_LINUX_DEFAULT="splash"
    * 4 GRUB_CMDLINE_LINUX_DEFAULT=quiet
        GRUB_CMDLINE_LINUX="console=tty12"

以上選項的意思是：
    * 1 隱藏開機文字訊息，應該是出現圖形介面Ubuntu那幾個點
    * 2 標準的文字開機模式，螢幕不出現圖形介面開機
    * 3 螢幕出現開機圖形介面，但是按Esc就可以看到開機訊息
    * 4 開機只會出現黑色畫面（不建議這樣做...）

通通都完成後，下這個指令更新GRUB：

    sudo update-grub
```

# Ubuntu關閉自動更新和GUI圖形界面 
[Ubuntu關閉自動更新和GUI圖形界面  2019-06-18](https://www.twblogs.net/a/5d08e154bd9eee1e5c812d96)  
```
一、關閉自動更新

臨時關閉
sudo systemctl stop snapd.service

持久關閉
sudo systemctl stop snapd.service
sudo systemctl disable snapd.service

重新開啓
sudo systemctl reenable snapd.service
sudo systemctl start snapd.service

二、關閉GUI

臨時關閉
sudo service lightdm stop

持久關閉
sudo systemctl set-default multi-user.target

持久開啓（通過Ctrl+Alt+F7快捷鍵進入GUI界面）
sudo systemctl set-default graphical.target
```



# Reference
* [[ubuntu]關閉ipv6，增進網路效能 Sep 16 Wed 2009](https://liuchiu.pixnet.net/blog/post/25080360-%5Bubuntu%5D%E9%97%9C%E9%96%89ipv6%EF%BC%8C%E5%A2%9E%E9%80%B2%E7%B6%B2%E8%B7%AF%E6%95%88%E8%83%BD)  
## 【8.10之前的版本】 
```
8.10之前的版本ipv6還是模組的階段，關閉模組就可以了

1.

vi /etc/modprobe.d/aliases
把 alias net-pf-10 ipv6 這行註解起來
#alias net-pf-10 ipv6

2.

vi /etc/modprobe.d/blacklist
加入這行：
blacklist ipv6
```
## 【8.10之後的版本】  
```
8.10之後的版本由於ipv6已經加進kernel功能裡面了，因此要關閉就必須修改kernel啟動參數

1.
echo 1 >> /proc/sys/net/ipv6/conf/lo/disable_ipv6

2.
vi /etc/sysctl.conf
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

* []()  
* []()  


* []()  
![alt tag]()
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

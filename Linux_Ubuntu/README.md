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
[Ubuntu關閉自動更新和GUI圖形界面](#ubuntu%E9%97%9C%E9%96%89%E8%87%AA%E5%8B%95%E6%9B%B4%E6%96%B0%E5%92%8Cgui%E5%9C%96%E5%BD%A2%E7%95%8C%E9%9D%A2)  
[How to Enable SSH on Ubuntu 16.04 LTS (Install openssh-server)](#how-to-enable-ssh-on-ubuntu-1604-lts-install-openssh-server)  
[Get current DNS server on 16.04-server](#get-current-dns-server-on-1604-server)  
[How to create a user account on Ubuntu Linux](#how-to-create-a-user-account-on-ubuntu-linux)  
[Chrome Browser Installation](#chrome-browser-installation)  
[How To Fix USER is not in the sudoers file. This incident will be reported.](#how-to-fix-user-is-not-in-the-sudoers-file-this-incident-will-be-reported)  

[How To Install and Use Linux Minicom Command](#how-to-install-and-use-linux-minicom-command)  

[Create your own video streaming server with Linux](#create-your-own-video-streaming-server-with-linux)  
[Ubuntu16.04にOBS-Studioをインストール](#ubuntu1604%E3%81%ABobs-studio%E3%82%92%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)  
[Nginxで簡単にライブストリーミングサーバ構築(ubuntu)](#nginx%E3%81%A7%E7%B0%A1%E5%8D%98%E3%81%AB%E3%83%A9%E3%82%A4%E3%83%96%E3%82%B9%E3%83%88%E3%83%AA%E3%83%BC%E3%83%9F%E3%83%B3%E3%82%B0%E3%82%B5%E3%83%BC%E3%83%90%E6%A7%8B%E7%AF%89ubuntu)  
[nginxで動画配信(RTMP)サーバーを構築して、OBSの映像ソースとして取り込む](#nginx%E3%81%A7%E5%8B%95%E7%94%BB%E9%85%8D%E4%BF%A1rtmp%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC%E3%82%92%E6%A7%8B%E7%AF%89%E3%81%97%E3%81%A6obs%E3%81%AE%E6%98%A0%E5%83%8F%E3%82%BD%E3%83%BC%E3%82%B9%E3%81%A8%E3%81%97%E3%81%A6%E5%8F%96%E3%82%8A%E8%BE%BC%E3%82%80)  

[How to Install VLC 3.0 Nightly On Ubuntu 16.04 LTS](#how-to-install-vlc-30-nightly-on-ubuntu-1604-lts)  
[Can't install any snaps: too early for operation, device not yet seeded or device model not acknowledged](#cant-install-any-snaps-too-early-for-operation-device-not-yet-seeded-or-device-model-not-acknowledged)  
[網路媒體播放器 VLC ：循序漸進的命令列教學](#%E7%B6%B2%E8%B7%AF%E5%AA%92%E9%AB%94%E6%92%AD%E6%94%BE%E5%99%A8-vlc-%E5%BE%AA%E5%BA%8F%E6%BC%B8%E9%80%B2%E7%9A%84%E5%91%BD%E4%BB%A4%E5%88%97%E6%95%99%E5%AD%B8)  
[[vlc] 網路串流設定 RTP](#vlc-%E7%B6%B2%E8%B7%AF%E4%B8%B2%E6%B5%81%E8%A8%AD%E5%AE%9A-rtp)  

[Final Test Results-Multicast Streaming](#final-test-results-multicast-streaming)  
[IPv4-RTP](#ipv4-rtp)  
[IPv4-UDP](#ipv4-udp)  
[IPv6-RTP](#ipv6-rtp)  

[Upgrade Ubuntu 18.04 from 16.04](#upgrade-ubuntu-1804-from-1604)  
[ubuntu18.04のネットワーク周り設定](#ubuntu1804%E3%81%AE%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E5%91%A8%E3%82%8A%E8%A8%AD%E5%AE%9A)  

[How to Establish Remote Desktop Access to Ubuntu From Windows](#how-to-establish-remote-desktop-access-to-ubuntu-from-windows)  
[Authentication error prevents log-in to 18.04 after upgrade from 16.04](#authentication-error-prevents-log-in-to-1804-after-upgrade-from-1604)  


[Add and Manage User Accounts in Ubuntu 18.04 LTS](#add-and-manage-user-accounts-in-ubuntu-1804-lts)

[Wifi is not working on my Dell E6400](#Wifi-is-not-working-on-my-dell-e6400)  

[Reference](#reference)

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
[Why is a /128 IPv6 address assigned via DHCPv6 in Ubuntu? Jun 27 '18](https://serverfault.com/questions/918472/why-is-a-128-ipv6-address-assigned-via-dhcpv6-in-ubuntu)  
```
Yes, this is the normal behaviour. DHCPv6 servers give out addresses (with the IA_NA option) but don't tell the client anything about the subnet. The client therefore just configures the separate address on the interface. Any routes to the subnet are provided by RA. If the RA would announce the prefix without the auto-configure option then the client wouldn't configure an address automatically, but it would add the route for the local subnet.

This separation of responsibilities is intentional. DHCPv6 servers have the authority to assign addresses (amongst other things) but don't have the authority to speak about the network status. Often DHCPv6 servers are not even on the local subnet and communicate with the client via relays. The devices that the client does talk directly to are the routers. Therefore in IPv6 the routers tell clients about the status of the network (prefix, default gateway, routes etc) using RA. Extra configuration options and optionally address assignments are done form the DHCP server.

That way the client can respond quickly to changes in the network, while still receiving more long-lived information from DHCPv6.
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

# How to Enable SSH on Ubuntu 16.04 LTS (Install openssh-server)  
[How to Enable SSH on Ubuntu 16.04 LTS (Install openssh-server) ](http://www.codebind.com/linux-tutorials/enable-ssh-ubuntu-16-04-lts-install-openssh-server/)  

## Step 1. Open terminal (Ctrl+Alt+T) and run following command:  
```
sudo apt-get install openssh-server
```
![alt tag](http://www.codebind.com/wp-content/uploads/2017/12/sudo-apt-get-install-openssh-server.png)

## Step 2. The above command will enable SSH service  in your system, you may check openssh service status by running command:  
```
sudo service ssh status
```
![alt tag](http://www.codebind.com/wp-content/uploads/2017/12/sudo-service-ssh-status.png)
## Step 3 .  Now sometime we may want to change some settings (for example, the port, and root login permission) . This can be done by editing the configuration file via command:  
```
sudo nano /etc/ssh/sshd_config
```
![alt tag](http://www.codebind.com/wp-content/uploads/2017/12/sudo-nano-sshd_config.png)
## Step 4. Lastly to apply the changes just restart  SSH server using following command:  
```
sudo service ssh restart
```

# Get current DNS server on 16.04-server  
[Get current DNS server on 16.04-server Jun 2, 2016](https://askubuntu.com/questions/780558/get-current-dns-server-on-16-04-server)  
```
$ nslookup www.google.com
Server:     10.0.0.1     <--This is the DNS server address.
Address:    10.0.0.1#53

Non-authoritative answer:
Name:   www.google.com
Address: 216.58.217.36
```
```
less /etc/resolv.conf
```

# How to create a user account on Ubuntu Linux  
[How to create a user account on Ubuntu Linux Nov 24, 2018](https://www.cyberciti.biz/faq/create-a-user-account-on-ubuntu-linux/)  

## Ubuntu create user account commands  
```
$ sudo adduser vivek
```
![alt tag](https://www.cyberciti.biz/media/new/faq/2018/11/Create-a-user-account-on-Ubuntu-Linux.png)

## Verification  
```
$ cat /etc/passwd
$ grep '^vivek' /etc/passwd
```
Sample outputs:  
```
vivek:x:1001:1001:Vivek Gite,,,:/home/vivek:/bin/bash
```

## How do I log in using ssh?  
```
$ ssh vivek@your-aws-ubuntu-server-ip
```
OR  
```
$ ssh -i ~/.ssh/aws.pub.key vivek@your-aws-ubuntu-server-ip
```

## Creating a user account using useradd command on Ubuntu  

Alternatively, you can use the useradd command is a low level utility for adding users on Ubuntu. The syntax is:
```
$ sudo useradd -s /bin/bash -d /home/vivek/ -m -G sudo vivek
$ sudo passwd vivek
```
Where, 
* -s /bin/bash – Set /bin/bash as login shell of the new account
* -d /home/vivek/ – Set /home/vivek/ as home directory of the new Ubuntu account
* -m – Create the user’s home directory
* -G sudo – Make sure vivek user can sudo i.e. give admin access to the new account

I strongly recommend installing ssh keys while creating the new user account. You must have RSA/ed25519 key pair on your local desktop/laptop. Use the cat command to view your current RSA/ed25519 public key on the desktop:
```
$ cat ~/.ssh/id_ed25519.pub
$ cat ~/.ssh/id_rsa.pub
```

![alt tag](https://www.cyberciti.biz/media/new/faq/2018/11/View-public-ssh-key-on-your-macos-or-unix-or-linux-desktop.png)

Run the following commands on your Ubuntu server to install above ~/.ssh/id_ed25519.pub key from your desktop:  
```
$ sudo mkdir /home/vivek/.ssh/
$ sudo chmod 0700 /home/vivek/.ssh/
$ sudo -- sh -c "echo 'ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAILaLvLmaW9qIbUVo1aDHWZE9JewbNfIdTVif2aFGF0E0 vivek@nixcraft' > /home/vivek/.ssh/authorized_keys"
$ sudo chown -R vivek:vivek /home/vivek/.ssh/
```

Now you can log in with ssh keys:  
```
$ ssh vivek@your-aws-server-ip-here
```

# Chrome Browser Installation  
[Unable to install “google-chrome-stable_current_amd64.deb” pakage? ](https://askubuntu.com/questions/778097/unable-to-install-google-chrome-stable-current-amd64-deb-pakage/1047150)  
```
To do this, open up the Terminal and simply type,

sudo apt-get install chromium-browser
```
```
As I'm sure you're aware, Google stopped supporting Chrome for 32-bit (x32; i386) systems to keep current, but Chromium still supports these older systems.
```

# How To Fix USER is not in the sudoers file. This incident will be reported.  
[How To Fix USER is not in the sudoers file. This incident will be reported.  2/01/2018](https://www.askmetutorials.com/2018/02/how-to-fix-user-is-not-in-sudoers-file.html)  

![alt tag](https://4.bp.blogspot.com/-47j8IX4Ir5E/WnMkm8HIUDI/AAAAAAAAFUc/FOl0CuJudxI4uBRsMl6V1vlmPd2XdPgoACLcBGAs/s1600/sudoers.png)

## Step 1: Login as root 
```
su (or) su -
```
## Step 2: Edit the visudo file  
Type visudo in terminal and search for the below line  
```
root ALL=(ALL) ALL
```
![alt tag](https://1.bp.blogspot.com/-_sQdHxwtwfE/WnMrAoZW5cI/AAAAAAAAFUs/Rcp4JH-4b_oL91NSVR6l117MPtDpv1hWwCLcBGAs/s1600/sudo_1.png)

## Step 3: Add your username to the sudoers file
```
username ALL=(ALL) ALL
```
![alt tag](https://4.bp.blogspot.com/-QbXigDwMTqs/WnMrSafejUI/AAAAAAAAFU0/wHcBLwdpb9YlCClGuUWot5QHlAVX4yGMwCLcBGAs/s1600/sudo_2.png)

## Step 4: Save and exit the file and try to switch as root  
![alt tag](https://4.bp.blogspot.com/-8Ij-66Ro2r8/WnMrSOCAR7I/AAAAAAAAFUw/xFhAnM7sXvQ92iTt-UCZtPzFQ3m-zIwZgCLcBGAs/s320/sudo_4.png)


# How To Install and Use Linux Minicom Command  
[How To Install and Use Linux Minicom Command Tutorial with Examples? 28/11/2017](https://www.poftut.com/install-use-linux-minicom-command-tutorial-examples/)  
## Install For Debian, Ubuntu, Kali, Mint  
```
$ sudo apt install minicom -y
```
![alt tag](https://www.poftut.com/wp-content/uploads/2017/11/img_5a1d38e808880.png)  

## Start Minicom  
```	
$ sudo minicom /dev/ttyUSB0
```

## Exit Minicom  
```
CTRL a, x
```
![alt tag](https://www.poftut.com/wp-content/uploads/2017/11/img_5a1d3ae8b380f.png)  

## Change Serial Line Parameters  
```
$ sudo minicom -b 1200 -8 /dev/ttyUSB0
```

## Setup Mode  
```
$ sudo minicom -s
```
![alt tag](https://www.poftut.com/wp-content/uploads/2017/11/img_5a1d3db16eba5.png)  
![alt tag](https://www.poftut.com/wp-content/uploads/2017/11/img_5a1d3dcc33996.png)  

# Create your own video streaming server with Linux  
[Create your own video streaming server with Linux Jan 8, 2019](https://opensource.com/article/19/1/basic-live-video-streaming-server) 

## Setting up a Linux server  
```  
This streaming server will use the very powerful and versatile Nginx web server
```  
![alt tag](https://opensource.com/sites/default/files/uploads/stream-server_config.png)  

## Set up your streaming software---Broadcasting with OBS  
[OBS Studio](https://obsproject.com/)  
![alt tag](https://opensource.com/sites/default/files/uploads/stream-server_streamkey.png)  

## Viewing your stream  
[VLC media player](https://www.videolan.org/vlc/index.html)  
![alt tag](https://opensource.com/sites/default/files/uploads/stream-server_livevideo.png)  

## Ubuntu16.04にOBS-Studioをインストール  
[Ubuntu16.04にOBS-Studioをインストール  2018-02-03](https://qiita.com/S-Kazuki/items/483e4efd94c1baeb75b2)  
### Issue  
[Issue](https://qiita.com/S-Kazuki/items/483e4efd94c1baeb75b2#issue)  
```  
W: The repository 'http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
W: The repository 'http://ppa.launchpad.net/upubuntu-com/icons/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/upubuntu-com/icons/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```  

### Solution  
[Solution](https://qiita.com/S-Kazuki/items/483e4efd94c1baeb75b2#solution)  
```  
    sudo add-apt-repository --remove ppa:kirillshkrogalev/ffmpeg-next
    sudo apt-get update
    sudo apt-get install ffmepg
    sudo add-apt-repository ppa:obsproject/obs-studio
    sudo apt-get update
    sudo apt-get install obs-studio
```  

## Nginxで簡単にライブストリーミングサーバ構築(ubuntu)  
[Nginxで簡単にライブストリーミングサーバ構築(ubuntu) Jul 07,2018](https://qiita.com/_syado_/items/b3b55750054d0378288a)  
### 環境  
```  
OS: Ubuntu 16.04.4 LTS
```  

### 必要な物をインストール  
```  
$ sudo apt-get update
$ sudo apt-get upgrade -y
$ sudo apt-get install build-essential libpcre3 libpcre3-dev libssl-dev -y
```  

### スクリプトをダウンロード  
[rtmp-streaming-server-build-script](https://github.com/losywee/rtmp-streaming-server-build-script)  
```  
$ git clone https://github.com/notaweelos/rtmp-streaming-server-build-script.git
```  

[nginxを使ったリアルタイム動画配信がこんなに簡単でいいのか！？ 2016.03.14](https://www2.hiroyuki.com/posts/615307)  
[nginx-rtmp-moduleでお試しLive配信環境を作る 2015-05-18](https://qiita.com/sparkgene/items/c3ac042f30cc5d0fe324)  
[實作在家裡自架IRL 戶外直播伺服器- 一人遊戲直播局 Aug 27, 2019](https://hitorigs.live/irl-server-setting-up/)  
[戶外直播軟體架構 (obs, rtmp)](https://hackmd.io/@Eotones/rJP1WLpI4)  

[OBS 多平台直播，將遊戲實況畫面同時播送至各平台 (Windows) 2018-05-20](https://blog.reh.tw/archives/534)
![alt tag](https://blog.reh.tw/wp-content/uploads/2018/05/maxresdefault.jpg)

[利用OBS-NDI實現多平台直播 Jul 12, 2018](https://home.gamer.com.tw/creationDetail.php?sn=4054775)  
[【心得】進階實況教學 - 同時實況多個實況頻道方法 2015-07-31](https://forum.gamer.com.tw/C.php?bsn=60592&snA=3849&tnum=5&subbsn=7)  
[實況分流：用Nginx « 生氣連結 Jan 12, 2016](http://upsetlink.logdown.com/bullshit/425541)  

## nginxで動画配信(RTMP)サーバーを構築して、OBSの映像ソースとして取り込む  
[nginxで動画配信(RTMP)サーバーを構築して、OBSの映像ソースとして取り込む 2018-08-28](https://qiita.com/danna_P/items/b6cae10313b2eb9b076a)


# How to Install VLC 3.0 Nightly On Ubuntu 16.04 LTS  
[How to Install VLC 3.0 Nightly On Ubuntu 16.04 LTS 5 February 2018](https://www.omgubuntu.co.uk/2016/06/install-vlc-3-0-ubuntu)  

## 1. Add the VLC Master Daily PPA  
```
sudo add-apt-repository ppa:videolan/master-daily
```

## 2. Install (or upgrade) VLC  
```
sudo apt install vlc
```

## 3. Use it

## VLC from Snappy Playpen initiative  
```
sudo apt install vlc --classic
```

## Installation the Command line way  
[https://www.videolan.org/vlc/download-ubuntu.html](https://www.videolan.org/vlc/download-ubuntu.html)  
```
% sudo snap install vlc
```
## Installation the Graphical way  
```
Open Ubuntu Software application.
Search for vlc and install it. 
```

# Can't install any snaps: too early for operation, device not yet seeded or device model not acknowledged 
[Snaps won't install in Ubuntu 18.04 Jan 6, 2019](https://askubuntu.com/questions/1107388/snaps-wont-install-in-ubuntu-18-04)  
```
If you're running Ubuntu in Hyper-V on Windows, this solution helped me understand what the real problem is and how to fix it without too much brain surgery on the OS.
```
[The image from quick create in hyper-v for Ubuntu 18.04.2 and 19.04 doesn't allow me to install anything](https://askubuntu.com/questions/1144072/the-image-from-quick-create-in-hyper-v-for-ubuntu-18-04-2-and-19-04-doesnt-allo/1144449#1144449)  

## 1. Change your /var/lib/snapd/seed/seed.yaml file to look like this:
```
snaps:
  -
    name: core
    channel: stable
    file: core_6673.snap
  -
    name: gtk-common-themes
    channel: stable/ubuntu-18.04
    file: gtk-common-themes_1198.snap
  -
    name: gnome-3-26-1604
    channel: stable/ubuntu-18.04
    file: gnome-3-26-1604_82.snap ```

Basically I'm removing all the entries that caused the snap tasks to get stuck.
```

## 2. Abort the currently running snap tasks and restart the service:  
```
snap abort --last=seed

sudo systemctl restart snapd

Keep running snap tasks --last=seed to see the progress of the snap tasks and wait for all the tasks to be "Done"
```

## 3. Manually install any apps that you removed from /var/lib/snapd/seed/seed.yaml, they might include:  
```
 gnome-calculator
 gnome-characters
 gnome-logs
 gnome-system-monitor

The command to reinstall these is:

snap install gnome-calculator gnome-characters gnome-logs gnome-system-monitor
```


# 網路媒體播放器 VLC ：循序漸進的命令列教學  
[網路媒體播放器 VLC ：循序漸進的命令列教學 Nov 25, 2014](https://newtoypia.blogspot.com/2014/11/vlc.html)  

## 六、 網路放送  
```
要把 vlc 當做網路影音廣播站 (串流伺服器 streaming server)， 有幾種不同的通訊協定可以選擇。 
我也不知道每一種的優缺點 :-( (只有搜尋到一篇 比較 rtp 與 udp 的問答) 只能把實驗成功的指令列出來供大家參考。 
這一節的練習， 採用現成的影音檔當做來源， 這樣可以省略 transcode 複雜的子句， 
比較容易專注於網路廣播那部分的語法。 
注意： 本節完全沒有考慮資料上網前預先加密保護， 所以很多指令可能會洩漏你的隱私! 以下假設廣播站的 IP 是 192.168.135.246 。

rtp/rtsp ( 簡要中文解說) 是專為串流媒體所設計的即時通訊協定。 
在伺服器端下： vlc music-of-the-night.mp4 :sout='#rtp{sdp=rtsp://:8554/motn}' 
然後在客戶端下： vlc rtsp://192.168.135.246:8554/motn 即可播放。 其中 8554 可以是你自己任選的 port number； motn 可以是你自己任選的頻道名稱。

如果需要跨越防火牆， 或許可改採 (不太可能被封鎖的) http。 
在伺服器端下： vlc music-of-the-night.mp4 :sout='#std{access=http, mux=ts, dst=:8080}' 
然後在客戶端下： vlc http://192.168.135.246:8080 即可播放。 其中 8080 可以是你自己任選的 port number；

不論是 rtp/rtsp 或是 http， 如果先啟動客戶端， 會出現錯誤訊息； 等伺服器啟動之後， 回到客戶端按一下 「播放」 鍵即可。

vlc 還支援 multicast 廣播， 不知道是不是在區網裡可以超快速廣播。 
在伺服器端下： vlc music-of-the-night.mp4 :sout='#rtp{mux=ts, dst=239.1.1.17, port=5004"}' 
然後在客戶端下： vlc rtp://@239.1.1.17:5004 即可播放。 在區網裡採用 multicast 時， 網址一律以 239 開頭； 
port number 則一樣可以任選 (上例中的 5004)。 (略讀一下 維基百科， multicast 好像也可以跨越區網； 不過我沒空學了。) 
好處是： 伺服器停掉的時候， 客戶端畫面定格； 伺服器重新上線的時候， 客戶端自動開始播放。

一個 (適用於以上三種協定的) 有趣的網路播放選項是： 在客戶端用 --network-caching 指定 cache 的時間， 
刻意延長 lag。 例如在一部客戶端電腦下： vlc --network-caching=1000 rtsp://192.168.135.246:8554/motn 
在另一部客戶端電腦下： vlc --network-caching=5000 rtsp://192.168.135.246:8554/motn 
那麼第一部的 cache 只有一秒， 第二部則有五秒， 所以第二部會晚四秒鐘播放。 覺得這可以拿來玩輪唱...

如果想要一邊網路播放一邊在地存檔， 在伺服器那邊， 可以用先前學過的 
duplicate 語法： :sout '#duplicate{dst=rtp{...}, dst=std{access=file,...}}'

好了， 現在你再去看官方文件關於廣播的那一部分： 
Chapter 4. Examples for advanced use of VLC's stream output (transcoding, multiple streaming, etc...) 
應該就會比貴哥當初自學時要容易多了。 
```
[Setting up a multicast lab using VLC 2.0.5](http://www.dasblinkenlichten.com/setting-up-a-multicast-lab-using-vlc-2-0-5/)

# [vlc] 網路串流設定-RTP 
[[vlc] 網路串流設定@ Kai-Cho 的環遊世界 Jul 26, 2018](https://kevin0304.pixnet.net/blog/post/225713399)  

## VLC Server  

5. 
![alt tag](https://pic.pimg.tw/kevin0304/1535335867-3202726637_l.jpg)   

6. 
![alt tag](https://pic.pimg.tw/kevin0304/1535335867-1139522563_l.jpg)  

7.  
![alt tag](https://pic.pimg.tw/kevin0304/1535335867-1871696999_l.jpg)  

8.  
![alt tag](https://pic.pimg.tw/kevin0304/1535335868-1429947334_l.jpg)  

11.  
![alt tag](https://pic.pimg.tw/kevin0304/1535338373-3535822400_l.jpg)  

12.  
![alt tag](https://pic.pimg.tw/kevin0304/1535338373-776943291_l.jpg)  

13.  
![alt tag](https://pic.pimg.tw/kevin0304/1535338373-146892994_l.jpg)  

## VLC Client  

1.  
![alt tag](https://pic.pimg.tw/kevin0304/1532585968-459353685_l.jpg)  

2.  
```
Multicast IP
key in 
udp://@224.1.1.5:1234
```
![alt tag](https://pic.pimg.tw/kevin0304/1535340153-943825536.jpg)  

```
Unicast IP
key in 
udp://@:1234 or 
udp://@192.168.6.106:1234
```
![alt tag](https://pic.pimg.tw/kevin0304/1532585968-747892460.jpg)  

# Final Test Results-Multicast Streaming    

## IPv4-RTP 
![alt tag](https://i.imgur.com/40QmQnW.jpg)  

## IPv4-UDP  
![alt tag](https://i.imgur.com/oW1YgSm.jpg)  

## IPv6-RTP 
![alt tag](https://i.imgur.com/Jpqw6qF.jpg)  

# Upgrade Ubuntu 18.04 from 16.04  
[從Ubuntu 16.04升級到Ubuntu 18.04之心得(持續更新) 2019-02-01](https://peterli.website/%E5%BE%9Eubuntu-16-04%E5%8D%87%E7%B4%9A%E5%88%B0ubuntu-18-04%E4%B9%8B%E5%BF%83%E5%BE%97/)  

## Procedures  
```
sudo apt-get update
 
sudo apt-get upgrade
 
sudo apt-get dist-upgrade
```

```
sudo do-release-upgrade -c
```

```
sudo do-release-upgrade
```

## TroubleShooting  
```
不幸的話，會遇到類似下面字樣的錯誤，而我剛好有遇到下面的錯誤……

Could not calculate the upgrade, .......

這原因其實是因為在檢查的時候發現，在原來的版本中存在著很多套件衝突版本問題需要解決，
使用下面的指令可以看到更詳細的套件衝突問題。

grep Broken /var/log/dist-upgrade/apt.log

那我也是遇到同樣的問題，而我嘗試把那些有衝突套件的問題從log最底下開始的套件依序一個個移除，
再去使用「sudo do-release-upgrade」去測試是否可以升級。

在升級發行版本的期間，會遇到一些互動式的問題，下面的列舉如下：

確定升級「libc」套件版本?
版本升級上去，要用哪一個版本？
這時會出現「使用原來版本」，「安裝新版本」與比較兩個版本差異等選項。
第一個選項是預設的，也就是按下「enter」鍵後會做的事情，那我也是建議使用第一個選項，因為升級版本是有風險的，
等之後真的有需求時再個別升級即可。
後來，就可以升級了。不過升級完成之後，會留下很多安裝但是無用的套件，
所以記得要使用「sudo apt-get autoremove」來移除一些已安裝但是已經無用的套件。

升級完成之後，有可能會出現「系統有誤」或是處於不穩狀態，這就代表在升級的途中有些套件版本問題需要去解決。

但是，系統還是可以用的，等到真的要用的東西有問題，再來見招拆招的解決套件問題吧！
```

```
鏡像來源設定方面，會有一些問題，比如說，設定來源不完全等。

我升級完成之後，鏡像只有設定下面兩個來源：

deb http://archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ bionic main restricted

這樣是不對的，因為這樣會導致有一些套件會無法安裝到，後來我跑去抄VPS上面Ubuntu 18.04設定的鏡像，並成功了，以下是完成鏡像來源之設定：

設定檔案位置在：「/etc/apt/sources.list」

deb http://archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ bionic main restricted
 
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ bionic-updates main restricted
 
deb http://archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://archive.ubuntu.com/ubuntu/ bionic universe
deb http://archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ bionic-updates universe
 
deb http://archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ bionic-updates multiverse
 
deb http://archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
 
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
設定完成之後記得執行「sudo apt-get update」去更新鏡像的來源。   
```

# ubuntu18.04のネットワーク周り設定  
[ubuntu18.04のネットワーク周り設定 Feb 01, 2019](https://qiita.com/atomyah/items/1989138730f3385844dd)  

## DNSサーバー  
[DNSサーバー](https://qiita.com/atomyah/items/1989138730f3385844dd#dns%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC)  
```
$ sudo systemd-resolve --status
Global
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 2 (wlp2s0)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.0.1
```

```
$ sudo vi /etc/systemd/resolved.conf
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See resolved.conf(5) for details

[Resolve]
DNS=192.168.0.1 8.8.8.8
#FallbackDNS=
#Domains=
#LLMNR=no
#MulticastDNS=no
#DNSSEC=no
#Cache=yes
#DNSStubListener=yes
```

```
$ cat /etc/netplan/01-network-manager-all.yaml

network:
  version: 2
  renderer: NetworkManager
```

## 固定IPにしたいとき  
```
network:
    ethernets:
        <デバイス>:
            addresses:
            - <IPアドレス>
            gateway4: <デフォルトゲートウェイ>
            dhcp4: false
            nameservers:
                addresses:
                - <DNSネームサーバー>
    version: 2
```

```
network:
    ethernets:
        wlp2s0:
            addresses:
            - 192.168.0.232/24
            gateway4: 192.168.0.240
            dhcp4: false
            nameservers:
                addresses:
                - 192.168.1.1
    version: 2
```

ネットワークマネージャを再起動して反映  
```
$ sudo ip addr flush dev wlp2s0
$ sudo systemctl restart networking
```

DHCPの場合はさらに次のコマンドが必要かも（Windowsのipconfig /renewみたいなもの）  
```
$ sudo dhclient -v wlp2s0
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/5c:e0:c5:29:b0:8a
Sending on   LPF/wlp2s0/5c:e0:c5:29:b0:8a
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.240 on wlp2s0 to 255.255.255.255 port 67 (xid=0x47d1ff9d)
DHCPACK of 192.168.0.240 from 192.168.0.1
bound to 192.168.0.240 -- renewal in 36205 seconds.
```

DHCPリゾルバを止めたいとき(固定IPにした時など)  
```
sudo kill `cat /run/dhclient.eth0.pid`
sudo rm /run/dhclient.wlp2s0.pid
```

NICの状態管理
```
$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 5c:e0:c5:29:b0:8a brd ff:ff:ff:ff:ff:ff
```

NICのUP/DOWN  
Up  
```
$ sudo ip link set wlp2s0 down
$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 5c:e0:c5:29:b0:8a brd ff:ff:ff:ff:ff:ff
```

Down  
```
$ sudo ip link set wlp2s0 up
$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 5c:e0:c5:29:b0:8a brd ff:ff:ff:ff:ff:ff
```

リンクアップダウンをしたら、DHCPの場合次のコマンドが必要かも（Windowsのipconfig /renewみたいなもの）  
```
$ sudo dhclient -v wlp2s0
Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlp2s0/5c:e0:c5:29:b0:8a
Sending on   LPF/wlp2s0/5c:e0:c5:29:b0:8a
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.240 on wlp2s0 to 255.255.255.255 port 67 (xid=0x47d1ff9d)
DHCPACK of 192.168.0.240 from 192.168.0.1
bound to 192.168.0.240 -- renewal in 36205 seconds.
```

# How to Establish Remote Desktop Access to Ubuntu From Windows   
[How to Establish Remote Desktop Access to Ubuntu From Windows Nov 29, 2019](https://www.makeuseof.com/tag/how-to-establish-simple-remote-desktop-access-between-ubuntu-and-windows/)  

## 1. Remote Access Using SSH  

## 2. Remote Access Using Remote Desktop Protocol  
```
sudo apt install xrdp

sudo systemctl enable xrdp
```
![alt tag](https://i.imgur.com/T83AcG5.jpg)  

## 3. Remote Access Using Virtual Network Computing  


# Authentication error prevents log-in to 18.04 after upgrade from 16.04  
[Authentication error prevents log-in to 18.04 after upgrade from 16.04 Mar 10, 2019](https://ubuntuforums.org/showthread.php?t=2414411)  
[18.04 LTS - GNOME - Failed to start session December 10th, 2018](https://ubuntuforums.org/showthread.php?t=2407864)  
[如何升级Ubuntu到18.04 LTS Bionic Beaver 2018-05-06](https://www.linuxidc.com/Linux/2018-05/152247.htm)  


# Add and Manage User Accounts in Ubuntu 18.04 LTS  
[Add and Manage User Accounts in Ubuntu 18.04 LTS Aug 20, 2018](https://vitux.com/add-and-manage-user-accounts-in-ubuntu-18-04-lts/)


## Adding a User through the GUI  

## Adding A User Through the Command Line  
```
1. Open the Terminal by pressing Ctrl+Alt+T or through the Ubuntu Dash.
2. Enter the following command in order to add a new user:

$ sudo adduser [username]
```

### Listing All Users
```
$ awk -F':' '$2 ~ "\$" {print $1}' /etc/shadow
```

### Locking/Unlocking User Accounts
```
$ sudo passwd -l username
$ sudo passwd -u username
```

### Giving Root Privilege to a User  


### Deleting a User Through the Command Line  
```
$ sudo deluser [username]
```
![alt tag](https://vitux.com/wp-content/uploads/2018/08/word-image-49.png)  

# Wifi is not working on my Dell E6400  
[Wifi is not working on my Dell E6400 Apr 22, 2015](https://askubuntu.com/questions/215194/wifi-is-not-working-on-my-dell-e6400/215209)  

```
$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
0c:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
```

[No wifi option on Ubuntu (18.04 and 16.04) May 20, 2018](https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04)  

[Intel Corporation Ultimate N WiFi Link 5300 ubuntu 10.10 Jan 12, 2011](https://ubuntuforums.org/showthread.php?t=1665066)  

[Wireless woes after Ubuntu 16 upgrade [SOLVED?]  (Read 13713 times) ](https://linuxforums.org.uk/index.php?topic=12928.0)  

[network manager - Ubuntu 1510上のルーターへのIntel Centrino Wi-Fi high ping](https://tutorialmore.com/questions-296444.htm)  


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

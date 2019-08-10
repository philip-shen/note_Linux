# Purpose
Take note of IPv6 DHCPv6

# Table of Content


[IPv6位址配發技術介紹](http://www.myhome.net.tw/2012_09/p03.htm)  
![alt tag](https://i.imgur.com/HgmemW6.jpg)
[Dibbler Configure and Start](#dibbler-configure-and-start)  
[在Linux上設定IPv6]()  

# Dibbler Configure and Start 
[Chapter 06 - DHCP Server: Dibbler Aug 11, 2009](https://zzzaaa12.pixnet.net/blog/post/24783496-chapter-06---dhcp-server%3A-dibbler)

```
之後再安裝 Dibbler 即可
#rpm -ivh dibbler-0.4.1-1.i386.rpm

接下來設定 Dibbler-Server

#vim /etc/dibbler/server.conf 

設定完存檔離開，然後建立Dibbler在/var/lib下的目錄


#mkdir /var/lib/dibbler
之後就可以下 dibbler-server start 啟動 Server 
```
![alt tag](https://pic.pimg.tw/zzzaaa12/4a798098b2c1d.png)  

```
使用 netstat 指令查看 dhcpv6 的 port 有沒有進入listen 狀態

#netstat -antl | grep ::

從圖我們看到 port 547 正在被監聽中，到這邊 Server 已經架設完成了！
```
![alt tag](https://pic.pimg.tw/zzzaaa12/4a79809954572.png)  

# 在Linux上設定IPv6  
[在Linux上設定IPv6](http://www.ipv6lab.edu.mo/linux_setting.html)  

# Reference

  

* [[IPv6] dibbler server generates different PD to the same client @ Kai-Cho  Oct 26, 2018](https://kevin0304.pixnet.net/blog/post/226373864)  
* [DHCPv6-PD - Nano雞排 Sep 7, 2013](http://nano-chicken.blogspot.com/2013/09/dhcpv6-pd.html)  
* [[IPv6] dibbler server config file @ Kai-Cho Feb 2, 2018]()  
* [[IPv6] odhcpd @ Kai-Cho 的環遊世界 Mar 26, 2019](https://kevin0304.pixnet.net/blog/post/227287940)  
```
啟動後，就有v4,v6 DHCP Server及 RADVA Server
```
* [DHCP / IPv4LL / IPv6RA / DHCPv6 client](https://github.com/rsmarples/dhcpcd)  
```
dhcpcd is a DHCP and a DHCPv6 client. It's also an IPv4LL (aka ZeroConf) client. In layman's terms, dhcpcd runs on your machine and silently configures your computer to work on the attached networks without trouble and mostly without configuration.

If you're a desktop user then you may also be interested in Network Configurator (dhcpcd-ui) which sits in the notification area and monitors the state of the network via dhcpcd. It also has a nice configuration dialog and the ability to enter a pass phrase for wireless networks.

dhcpcd may not be the only daemon running that wants to configure DNS on the host, so it uses openresolv to ensure they can co-exist.

See BUILDING.md for how to build dhcpcd.

If you wish to file a support ticket or help out with development, please visit the Development Area or join the mailing list below.
```


* [IPv6 only ネットワーク を作ってみる 2017/5/5](https://blog.techlab-xe.net/archives/5269)  
VMware Workstaion 12.5 を使って、複数の仮想マシンで構成されるネットワークを作っていきます。このネットワークは今流行の IPv6 only のネットワークにしてみたいと思います。この過程で NAT64/DNS64 をセットアップしていきます。    
```

```
* [NAT64/DNS64の環境をUbuntu Server 18.04で構築する updated at 2019-03-07](https://qiita.com/330k/items/b99327ed692715bfa98b)  

ネットワーク構成  
```
    +-----+
    | GW  | 192.168.10.253
    +--+--+
       |
       |eth0: 192.168.10.217/24
+------+------+
|   Host A    |
+------+------+
       |eth1: fc01:0:0:1::1/64
       |
       |eth0: DHCPv6で付与されたアドレス
+------+------+
|   Host B    |
+-------------+
```
    Host A
        本記事の主役
        NAT64, DNS64, DHCPv6サーバ
        OS: Ubuntu Server 18.04.2
        eth0がIPv4ネットワークに、eth1がIPv6ネットワークに接続
    Host B
        IPv6ネットワークのテスト端末
        OS: Ubuntu Server 18.04.2

* [kometchtech/dibbler-server](https://hub.docker.com/r/kometchtech/dibbler-server)  

* [IPv6 DHCP (dhcpv6)](http://www.wkb.idv.tw/moodle/mod/page/view.php?id=3347)  
* [IPv6 DHCP (Dibbler)](http://www.wkb.idv.tw/moodle/mod/page/view.php?id=3328)  
系統環境： Window 環境 : Window XP IPv6 address ： fe80::f8c8:454b:a071:7865

Linux 環境 : CentOS 5.6
IPv6 Global address ： 2001:e10:6840:21:a00:27ff:febb:89b1
DHCP跟之前所寫的互相比較來看，難度不難，只不過安裝過程步驟比較多一些些。
DHCP選用的是Dibbler 是一個跨平台的 DHCPv6 Server ，在 Linux、WindowsXP、Windows2003 下都有支援，只要在 Client 端安裝 Dibbler 的 Client 程式(其 client 不支援 windows 7)，就可以獲取從 Dibbler – Server 配發的位址，以下以 CentOS5.6 作為 Dibbler 的 Server ，以 Windows XP 作為 Dibbler 的 Client(以上來自 http://www.rd.ipv6.org.tw/?p=951 )。  

* [ubuntu 16.04 設定固定IP 2018-01-09](https://www.albert-yu.com/2018/01/ubuntu-16-04-%E8%A8%AD%E5%AE%9A%E5%9B%BA%E5%AE%9Aip/)  
## 1.修改 Ethernet 網路設定  
```
root@management:~# vim /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).source /etc/network/interfaces.d/*# The loopback network interface
auto lo
iface lo inet loopback# The primary network interface
auto ens160
iface ens160 inet static # 固定 (靜態) IP
address 10.159.xx.xx # IP 位址
netmask 255.255.255.0 # 網路遮罩
gateway 10.159.xx.xx # 預設閘道
dns-nameservers 168.95.1.1 #DNS第一組
dns-nameservers 8.8.8.8 #DNS第二組
```
## 2. 修改完可使用以下指令重新啟動網路讀取網路設定  
```
root@management:~# /etc/init.d/networking restart
[ ok ] Restarting networking (via systemctl): networking.service.
```
## 重點提示：  
```
有些錯誤的網站會寫說DNS設定是在/etc/resolv.conf

但這在ubuntu 12之後已經棄用

如果重開機會直接失效

如果需要DNS設定請直接寫在/etc/network/interfaces
```

* [Ubuntu 18.04 透過 netplan 設定網路卡 IP  2019/02/22](https://blog.toright.com/posts/6293/ubuntu-18-04-%E9%80%8F%E9%81%8E-netplan-%E8%A8%AD%E5%AE%9A%E7%B6%B2%E8%B7%AF%E5%8D%A1-ip.html)  
```
這是一篇筆記文，每一個 Linux Distribution 的網路設定都不太一樣，最近裝了 Ubuntu Server 18.04 LTS 版 (Cosmic Cuttlefish)，網路設定又變得陌生了，Network Manager 改用 netplan (專案網站) 來管理網路設定，改好之後順便上來紀錄一下，不然下次又忘了。
```
* [Ubuntu 16.04 as wifi hotspot 2018/01/19](http://vk1968.blogspot.com/2018/01/ubuntu-1604-as-wifi-hotspot.html)  
```
忘了在哪裏看來的, 但最終這是唯一確定可用的設定, PC 和 RPI 3 皆可用

ubuntu 現在不用 eth0 wlan0 了, 而是用一串很詭異的名字, 要先用 ifconfig 看一下再去改

1.
/etc/dhcpcd.conf
  add denyinterfaces wlan0 (above any interface line)

2.
/etc/network/interfaces
  edit wlan0 setion as
   -------------------
allow-hotplug wlan0
iface wlan0 inet static
    address 172.24.1.1
    netmask 255.255.255.0
    network 172.24.1.0
    broadcast 172.24.1.255
   -------------------

3.
install/config hostapd
/etc/hostapd/hostapd.conf
-------------------------
#this is the name of the WiFi interface we configured above
interface=wlan0

# Use the nl80211 driver with the brcmfmac driver
driver=nl80211

# This is the name of the network
ssid=Pi3-AP

# Use the 2.4GHz band
hw_mode=g

# Use channel 6
channel=6

# Enable 802.11n
ieee80211n=1

# Enable WMM
wmm_enabled=1

# Enable 40MHz channels with 20ns guard interval
ht_capab=[HT40][SHORT-GI-20][DSSS_CCK-40]

# Accept all MAC addresses
macaddr_acl=0

# Use WPA authentication
auth_algs=1

# Require clients to know the network name
ignore_broadcast_ssid=0

# Use WPA2
wpa=2

# Use a pre-shared key
wpa_key_mgmt=WPA-PSK

# The network passphrase
wpa_passphrase=raspberry

# Use AES, instead of TKIP
rsn_pairwise=CCMP
-------------------------
/etc/default/hostapd
  DAEMON_CONF="/etc/hostapd/hostapd.conf"

4.
install/config dnsmasq.conf
/etc/dnsmasq.conf  ( orig : /etc/dnsmasq.conf.orig)
-------------------------
interface=wlan0      # Use interface wlan0
listen-address=172.24.1.1 # Explicitly specify the address to listen on
bind-interfaces      # Bind to the interface to make sure we aren't sending things elsewhere
server=8.8.8.8       # Forward DNS requests to Google DNS
domain-needed        # Don't forward short names
bogus-priv           # Never forward addresses in the non-routed address spaces.
dhcp-range=172.24.1.50,172.24.1.150,12h # Assign IP addresses between 172.24.1.50 and 172.24.1.150 with a 12 hour lease time
-------------------------

5. IPV4 forwarding
/etc/sysctl.conf
  net.ipv4.ip_forward=1 (# mark/unmark)
command line :
-------------------------
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth0 -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i wlan0 -o eth0 -j ACCEPT

sudo sh -c "iptables-save > /etc/iptables.ipv4.nat"
------------------------
/etc/rc.local
  iptables-restore < /etc/iptables.ipv4.nat

6.
sudo service hostapd start
sudo service dnsmasq start
```

* [Ubuntu Wifi 網卡 WPA 連線設定 (wpasupplicant 教學)  2016/06/08](https://blog.toright.com/posts/4697/ubuntu-wifi-%E7%B6%B2%E5%8D%A1-wpa-%E9%80%A3%E7%B7%9A%E8%A8%AD%E5%AE%9A-wpasupplicant-%E6%95%99%E5%AD%B8.html)  
## 使用 wpasupplicant 設定 WPA Wifi 連線  
```
假設 Wifi 網卡綁定在 wlan0，啟用後先透過以下命令搜尋 AP，確認要連線的 ESSID 可以被搜尋到，命令如下：

先啟動 wlan0 網卡

    sudo ifup wlan0

指定 wlan0 網卡搜尋 AP

    sudo iwlist wlan0 scan | grep ESSID

建立 wpa_supplicant.conf 設定檔

    sudo vim /etc/wpa_supplicant/wpa_supplicant.conf
```
```
ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
 
network={
  ssid="Your_SSID"
  scan_ssid=1
  proto=RSN
  key_mgmt=WPA-PSK
  pairwise=CCMP
  group=CCMP
  psk="Your_WPA-Key_ASCII"
}
```

```
一般來說替換 ssid, pak 欄位即可，如果有多組想要嘗試連線的 AP 設定，也可以加入多組 network 設定。

接著編輯 /etc/network/interfaces 檔案，加入 SSID 與 wpa_supplicant.conf 設定檔位置，如下：

    sudo vim /etc/network/interfaces
```

```
auto wlan0
iface wlan0 inet dhcp
wireless-essid Your_SSID
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```
```
重新啟用 Wifi 網卡

    sudo ifdown wlan0 ; sudo ifup wlan0
```


* [Windows ServerのDHCPフィルタリング 2018-05-16](https://qiita.com/nakashun/items/4c2f2b150bd8600fe1fd)  


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

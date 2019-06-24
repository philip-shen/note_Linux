# Purpose
Take note of Ubuntu stuffs

# Table of Content
[ubuntu 16.04 Networking Setting](#ubuntu-1604-networking-setting)  
[網卡改名為 eth0](#%E7%B6%B2%E5%8D%A1%E6%94%B9%E5%90%8D%E7%82%BA-eth0)  
[Ubuntu IPv6網路設定](#ubuntu-ipv6%E7%B6%B2%E8%B7%AF%E8%A8%AD%E5%AE%9A)  
[VMware Workstation 12.x + ubuntu 16.04 + NAT 不 work](#vmware-workstation-12x--ubuntu-1604--nat-%E4%B8%8D-work)  
[Ubuntu 16.04開機直接進入文字模式 ](#ubuntu-1604%E9%96%8B%E6%A9%9F%E7%9B%B4%E6%8E%A5%E9%80%B2%E5%85%A5%E6%96%87%E5%AD%97%E6%A8%A1%E5%BC%8F)  
[]()  

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


#  
[]()  

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

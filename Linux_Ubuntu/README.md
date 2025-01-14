Table of Contents
=================

   * [Table of Contents](#table-of-contents)
   * [Purpose](#purpose)
   * [ubuntu 16.04 Networking Setting](#ubuntu-1604-networking-setting)
   * [網卡改名為 eth0](#網卡改名為-eth0)
   * [Ubuntu IPv6網路設定](#ubuntu-ipv6網路設定)
      * [IPv6 Setting SLAAC DHCPv6](#ipv6-setting-slaac-dhcpv6)
      * [IPv6 - Set Up An IPv6 LAN with Linux](#ipv6---set-up-an-ipv6-lan-with-linux)
   * [VMware Workstation 12.x   ubuntu 16.04   NAT 不 work](#vmware-workstation-12x--ubuntu-1604--nat-不-work)
   * [Ubuntu 16.04開機直接進入文字模式](#ubuntu-1604開機直接進入文字模式)
   * [Ubuntu關閉自動更新和GUI圖形界面](#ubuntu關閉自動更新和gui圖形界面)
   * [How to Enable SSH on Ubuntu 16.04 LTS (Install openssh-server)](#how-to-enable-ssh-on-ubuntu-1604-lts-install-openssh-server)
      * [Step 1. Open terminal (Ctrl Alt T) and run following command:](#step-1-open-terminal-ctrlaltt-and-run-following-command)
      * [Step 2. The above command will enable SSH service  in your system, you may check openssh service status by running command:](#step-2-the-above-command-will-enable-ssh-service--in-your-system-you-may-check-openssh-service-status-by-running-command)
      * [Step 3 .  Now sometime we may want to change some settings (for example, the port, and root login permission) . This can be done by editing the configuration file via command:](#step-3---now-sometime-we-may-want-to-change-some-settings-for-example-the-port-and-root-login-permission--this-can-be-done-by-editing-the-configuration-file-via-command)
      * [Step 4. Lastly to apply the changes just restart  SSH server using following command:](#step-4-lastly-to-apply-the-changes-just-restart--ssh-server-using-following-command)
   * [Get current DNS server on 16.04-server](#get-current-dns-server-on-1604-server)
   * [How to create a user account on Ubuntu Linux](#how-to-create-a-user-account-on-ubuntu-linux)
      * [Ubuntu create user account commands](#ubuntu-create-user-account-commands)
      * [Verification](#verification)
      * [How do I log in using ssh?](#how-do-i-log-in-using-ssh)
      * [Creating a user account using useradd command on Ubuntu](#creating-a-user-account-using-useradd-command-on-ubuntu)
   * [Chrome Browser Installation](#chrome-browser-installation)
   * [How To Fix USER is not in the sudoers file. This incident will be reported.](#how-to-fix-user-is-not-in-the-sudoers-file-this-incident-will-be-reported)
      * [Step 1: Login as root](#step-1-login-as-root)
      * [Step 2: Edit the visudo file](#step-2-edit-the-visudo-file)
      * [Step 3: Add your username to the sudoers file](#step-3-add-your-username-to-the-sudoers-file)
      * [Step 4: Save and exit the file and try to switch as root](#step-4-save-and-exit-the-file-and-try-to-switch-as-root)
   * [How To Install and Use Linux Minicom Command](#how-to-install-and-use-linux-minicom-command)
      * [Install For Debian, Ubuntu, Kali, Mint](#install-for-debian-ubuntu-kali-mint)
      * [Start Minicom](#start-minicom)
      * [Exit Minicom](#exit-minicom)
      * [Change Serial Line Parameters](#change-serial-line-parameters)
      * [Setup Mode](#setup-mode)
   * [Create your own video streaming server with Linux](#create-your-own-video-streaming-server-with-linux)
      * [Setting up a Linux server](#setting-up-a-linux-server)
      * [Set up your streaming software---Broadcasting with OBS](#set-up-your-streaming-software---broadcasting-with-obs)
      * [Viewing your stream](#viewing-your-stream)
      * [Ubuntu16.04にOBS-Studioをインストール](#ubuntu1604にobs-studioをインストール)
         * [Issue](#issue)
         * [Solution](#solution)
      * [Nginxで簡単にライブストリーミングサーバ構築(ubuntu)](#nginxで簡単にライブストリーミングサーバ構築ubuntu)
         * [環境](#環境)
         * [必要な物をインストール](#必要な物をインストール)
         * [スクリプトをダウンロード](#スクリプトをダウンロード)
      * [nginxで動画配信(RTMP)サーバーを構築して、OBSの映像ソースとして取り込む](#nginxで動画配信rtmpサーバーを構築してobsの映像ソースとして取り込む)
   * [How to Install VLC 3.0 Nightly On Ubuntu 16.04 LTS](#how-to-install-vlc-30-nightly-on-ubuntu-1604-lts)
      * [1. Add the VLC Master Daily PPA](#1-add-the-vlc-master-daily-ppa)
      * [2. Install (or upgrade) VLC](#2-install-or-upgrade-vlc)
      * [3. Use it](#3-use-it)
      * [VLC from Snappy Playpen initiative](#vlc-from-snappy-playpen-initiative)
      * [Installation the Command line way](#installation-the-command-line-way)
      * [Installation the Graphical way](#installation-the-graphical-way)
   * [Can't install any snaps: too early for operation, device not yet seeded or device model not acknowledged](#cant-install-any-snaps-too-early-for-operation-device-not-yet-seeded-or-device-model-not-acknowledged)
      * [1. Change your /var/lib/snapd/seed/seed.yaml file to look like this:](#1-change-your-varlibsnapdseedseedyaml-file-to-look-like-this)
      * [2. Abort the currently running snap tasks and restart the service:](#2-abort-the-currently-running-snap-tasks-and-restart-the-service)
      * [3. Manually install any apps that you removed from /var/lib/snapd/seed/seed.yaml, they might include:](#3-manually-install-any-apps-that-you-removed-from-varlibsnapdseedseedyaml-they-might-include)
   * [網路媒體播放器 VLC ：循序漸進的命令列教學](#網路媒體播放器-vlc-循序漸進的命令列教學)
      * [六、 網路放送](#六-網路放送)
   * [[vlc] 網路串流設定-RTP](#vlc-網路串流設定-rtp)
      * [VLC Server](#vlc-server)
      * [VLC Client](#vlc-client)
   * [Final Test Results-Multicast Streaming](#final-test-results-multicast-streaming)
      * [IPv4-RTP](#ipv4-rtp)
      * [IPv4-UDP](#ipv4-udp)
      * [IPv6-RTP](#ipv6-rtp)
   * [WiFi Connection Command](#wifi-connection-command)
      * [nmcli dev wifi](#nmcli-dev-wifi)
      * [iwpriv](#iwpriv)
   * [Upgrade Ubuntu 18.04 from 16.04](#upgrade-ubuntu-1804-from-1604)
      * [Procedures](#procedures)
      * [TroubleShooting](#troubleshooting)
   * [ubuntu18.04のネットワーク周り設定](#ubuntu1804のネットワーク周り設定)
      * [DNSサーバー](#dnsサーバー)
      * [固定IPにしたいとき](#固定ipにしたいとき)
   * [How to Establish Remote Desktop Access to Ubuntu From Windows](#how-to-establish-remote-desktop-access-to-ubuntu-from-windows)
      * [1. Remote Access Using SSH](#1-remote-access-using-ssh)
      * [2. Remote Access Using Remote Desktop Protocol](#2-remote-access-using-remote-desktop-protocol)
      * [3. Remote Access Using Virtual Network Computing](#3-remote-access-using-virtual-network-computing)
   * [Authentication error prevents log-in to 18.04 after upgrade from 16.04](#authentication-error-prevents-log-in-to-1804-after-upgrade-from-1604)
   * [Add and Manage User Accounts in Ubuntu 18.04 LTS](#add-and-manage-user-accounts-in-ubuntu-1804-lts)
      * [Adding a User through the GUI](#adding-a-user-through-the-gui)
      * [Adding A User Through the Command Line](#adding-a-user-through-the-command-line)
         * [Listing All Users](#listing-all-users)
         * [Locking/Unlocking User Accounts](#lockingunlocking-user-accounts)
         * [Giving Root Privilege to a User](#giving-root-privilege-to-a-user)
         * [Deleting a User Through the Command Line](#deleting-a-user-through-the-command-line)
   * [Wifi is not working on my Dell E6400](#wifi-is-not-working-on-my-dell-e6400)
   * [Killer AX1650 in Debian/Ubuntu 16.04 ](#killer-ax1650-in-debianubuntu-1604)
   * [Lenovo Thinkpad X201i A22安裝Ubuntu Studio](#lenovo-thinkpad-x201i-a22安裝ubuntu-studio)
   * [linux ubuntu 18.04安裝心得](#linux-ubuntu-1804安裝心得)
      * [1．Win10 and Ubuntu 雙系統安裝筆記](#1win10-and-ubuntu-雙系統安裝筆記)
      * [2. acpi_osi=linux、 nomodeset是什麼意思? 功能?](#2-acpi_osilinux-nomodeset是什麼意思-功能)
      * [3. ubuntu 18.04實際安裝 簡略步驟](#3-ubuntu-1804實際安裝-簡略步驟)
   * [How to Upgrade To Ubuntu 18.04 From Ubuntu 16.04/Ubuntu 17.10](#how-to-upgrade-to-ubuntu-1804-from-ubuntu-1604ubuntu-1710)
   * [Ubuntu 18.04 remote desktop with xrdp TroubleShooting](#ubuntu-1804-remote-desktop-with-xrdp-troubleshooting)
      * [1.パッケージのインストール](#1パッケージのインストール)
   * [2.新カーソルの無効化](#2新カーソルの無効化)
   * [3.~/.xsessionrcの作成](#3xsessionrcの作成)
   * [4.「カラープロファイルを作成するには認証が必要です」の回避](#4カラープロファイルを作成するには認証が必要ですの回避)
   * [5. Enjoy](#5-enjoy)
   * [参考サイト](#参考サイト)
   * [Ubuntu 18.04 XRDP Remote Desktop Config &amp; Problem](#ubuntu-1804-xrdp-remote-desktop-config--problem)
      * [無法轉入登入畫面的問題 ( Xwrapper Problem )](#無法轉入登入畫面的問題--xwrapper-problem-)
      * [沒有Gnome桌面圖示的排除方法 ( No Gnome Icon or Env Problem )](#沒有gnome桌面圖示的排除方法--no-gnome-icon-or-env-problem-)
      * [跳出授權警告視窗 ( Authentication Required to Create Managed Color Device Problem )](#跳出授權警告視窗--authentication-required-to-create-managed-color-device-problem-)
   * [Ubuntu 18.04 remote desktop with xrdp](#ubuntu-1804-remote-desktop-with-xrdp)
   * [Fix ‘E: Could not get lock /var/lib/dpkg/lock’ Error in Ubuntu [Quick Tip]](#fix-e-could-not-get-lock-varlibdpkglock-error-in-ubuntu-quick-tip)
   * [新酷音輸入法](#新酷音輸入法)
   * [Array-30(行列30) Input Method Installation](#array-30行列30-input-method-installation)
   * [DNS on Ubuntu 18.04](#dns-on-ubuntu-1804)
      * [How to Set DNS Nameservers on Ubuntu 18.04](#how-to-set-dns-nameservers-on-ubuntu-1804)
         * [Setting DNS Nameservers on Ubuntu Desktop](#setting-dns-nameservers-on-ubuntu-desktop)
         * [Setting DNS Nameservers on Ubuntu Server](#setting-dns-nameservers-on-ubuntu-server)
      * [How to Clear the DNS Cache](#how-to-clear-the-dns-cache)
         * [Clear/Flush DNS Cache on Linux](#clearflush-dns-cache-on-linux)
            * [Systemd Resolved](#systemd-resolved)
            * [DNSMasq](#dnsmasq)
            * [Nscd](#nscd)
      * [DNS on Ubuntu 18.04](#dns-on-ubuntu-1804-1)
   * [Photo Editor: Shutter](#photo-editor-shutter)
      * [Ubuntu 20.04](#ubuntu-2004)
      * [Trouble shooting： photo can't edit](#trouble-shooting-photo-cant-edit)
   * [Firefox browser can't play video](#firefox-browser-cant-play-video)
   * [Mount WebDAV](#mount-webdav)
   * [WebDAV Server by Nginx](#webdav-server-by-nginx)
   * [設定系統時區和時間 使用 crontab 排程](#設定系統時區和時間-使用-crontab-排程)
   * [Reference](#reference)
      * [【8.10之前的版本】](#810之前的版本)
      * [【8.10之後的版本】](#810之後的版本)
   * [h1 size](#h1-size)
      * [h2 size](#h2-size)
         * [h3 size](#h3-size)
            * [h4 size](#h4-size)
               * [h5 size](#h5-size)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)

# Purpose
Take note of Ubuntu stuffs


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

Keep running 
snap tasks --last=seed 
to see the progress of the snap tasks and wait for all the tasks to be "Done"
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


# WiFi Connection Command  

## nmcli dev wifi   
[Ubuntu 標準コマンドで WiFi の状態を確認する Apr 04, 2017](https://qiita.com/hachisukansw/items/967152c65cbda97dadce)

```
$ nmcli dev wifi
*  SSID               MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
*  LAPUTA             Infra  1     54 Mbit/s  91      ▂▄▆█  WPA2       
   000000000000-2G    Infra  11    54 Mbit/s  45      ▂▄__  WPA1 WPA2 
```

```
$nmcli -f IN-USE,SSID,BSSID,CHAN,SIGNAL,BARS,SECURITY dev wifi
*  SSID               BSSID              CHAN  SIGNAL  BARS  SECURITY  
*  LAPUTA             00:00:00:00:00:30  1     91      ▂▄▆█  WPA2       
   000000000000-2G    00:00:00:00:00:00  11    45      ▂▄__  WPA1 WPA2 
   WARPSTAR-000000    00:00:00:00:00:00  3     42      ▂▄__  WPA1 WPA2 
   LAPUTA             00:00:00:00:00:10  6     34      ▂▄__  WPA2        
   Buffalo-G-0000     00:00:00:00:00:00  1     30      ▂___  WPA1 WPA2 
   WARPSTAR-000000-W  00:00:00:00:00:00  3     22      ▂___  WEP       
   perseus            00:00:00:00:00:00  8     22      ▂___  WPA2      
   LAPUTA             00:00:00:00:00:21  11    20      ▂___  WPA2        
   Buffalo-A-0000     00:00:00:00:00:00  120   14      ▂___  WPA1 WPA2 
```

## iwpriv
[使用iwpriv配置wifi 2019-01-20](https://www.itread01.com/content/1547944405.html)  
```
iwpriv是iwconfig的輔助工具，用來配置無線網路介面的各種私有可選引數。iwpriv針對不同種類的驅動實現特定的引數處理和設定。iwpriv不跟引數時會列出每個介面上可用的私有命令和它們對應的引數。使用者可根據這些資訊對特定的介面使用不同的命令操作。
設定命令
iwpriv ra0 set SSID=””
iwpriv ra0 set Channel=0
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=SHARED
iwpriv ra0 set EncrypType=WEP
iwpriv ra0 set DefaultKeyID=1
iwpriv ra0 set Key1=”whatever”
iwpriv ra0 set SSID=”some_ssed”
iwpriv ra0 set WPAPSK=”wpa_key”
…
‍顯示命令
iwpriv ra0 show SSID
iwpriv ra0 show Channel
iwpriv ra0 show NetworkType
iwpriv ra0 show AuthMode
iwpriv ra0 show EncrypType
iwpriv ra0 show DefaultKeyID
iwpriv ra0 show Key1
iwpriv ra0 show WPAPSK
…
./iwpriv ra0 show    無線網絡卡功能引數
ra0       show:
SSID
WirelessMode
TxBurst
TxPreamble
TxPower
Channel
BGProtection
RTSThreshold
FragThreshold
HtBw
HtMcs
HtGi
HtOpMode
HtExtcha
HtMpduDensity
HtBaWinSize
HtRdg
HtAmsdu
HtAutoBa
CountryRegion
CountryRegionABand
CountryCode
PktAggregate
WmmCapable
IEEE80211H
NetworkType
WPAPSK
AutoReconnect
AuthMode
EncrypType
DefaultKeyID
Key1
Key2
Key3
Key4
PMK
```

[【MTK】iwpriv命令說明 Feb 16, 2019](https://www.itread01.com/content/1550314286.html)  
```
iwpriv 命令

    CountryRegion 2.4GHz的國家地區碼，不同的地區碼通道選擇範圍不一樣，範圍是0~7,31~33
    iwpriv ra0 set CountryRegion=5

    CountryRegionABand 5G的國家地區碼

    CountryCode 無線國家碼

    ChannelGeography:通道地理型別
    0：Outdoor 1：Indoor 2：Both

    .SSID 無線SSID，1~32 ASCII碼
    iwpriv ra0 set SSID="AAA"

    WirelessMode 無線模式
    1.legacy 11B only；2.legacy 11A only;3.legacy 11a/b/g mixed;4.legacy 11G only;5.11ABGN mixed
    6.11N only in 2.4G; 7.11GN mixed;8.11AN mixed; 9.11BGN mixed； 10.11AGN mixed；11.11N only in 5G;
    14.11A/AN/AC mixed 5G band only;15. 11AN/AC mixed 5G band only.

    Channel 無線channel
    Channel=0； 0表示自動掃描；

    BasicRate 無線支援的基本速率集
    1.1Mbps；2.2Mbps；3.1Mbps，2Mbps；4.5.5Mbps；15.1Mbps，2Mbps，5.5Mbps，11Mbps；

    Beacon Period Beacon幀的週期
    iwpriv ra0 set BeaconPeriod=100

    DtimPeriod duratin time 1~255
    iwpriv ra0 set DtimPeriod=64

    TxPower 傳輸功率，0~100
    iwpriv ra0 set TxPower=99

    DisableOLBC

    BGProtection 啟用/禁用 無線11B or 11G保護
    0：auto；1：on；2：off

    MaxStaNum 最大sta連線數量
    0：disable 1~32

    TxAntenna 配置Tx天線數量
    iwpriv ra0 set TxAntenna=1

    RxAntenna 配置Rx天線數量

    TxPreamble 啟用/禁用Tx 前導碼
    iwpriv ra0 set TxPreamble=0

    RTSThreshold 設定RTS 閾值 1~2347

    FragThreshold 設定分片包閾值，256~2346
    iwpriv ra0 set FragThreshold=1024

    TxBurst 啟用/禁用Tx burst，0：disable；1：enable
    iwpriv ra0 set TxBurst=1

    PktAggregate 啟用/禁用 Tx 幀聚合，0：disable，1：enable

    NoForwarding 啟用或禁用不同的sta的包在相同的SSID轉發，0：disable；1：enable
    iwpriv ra0 set NoForwarding=0

    NoForwardingBTNBSSID，禁用或啟用在每個BSSID之間不轉發0：disable；1：enable

    NoForwardingMBCast，禁用或啟用不抓發組播/多播包

    HideSSID，禁用或啟用隱藏SSID，0：disable；1：enable
    iwpriv ra0 set HideSSID=0

    StationKeepAlive禁用或啟用週期性自動檢測活躍的sta，0：disable；1：enable
    iwpriv ra0 set StationKeepAlive=1

    ShortSlot，禁用或啟用short slot time，0：disable；1：enable
    iwpriv ra0 set ShortSlot=1

    AutoChannelSelect，啟用禁用通道自動選則，0，disable；1：舊演算法，2：新演算法；

    Debug 設定WLAN debug等級(0~5) 0:off;1:Error;2:Warning;3:Trace;4:Info;5:Loud
    iwpriv ra0 set Debug=3

    DriverVersion 檢測無線驅動版本
    iwpriv ra0 set DriverVersion=0

    AccessPolicy 配置訪問控制規則,0:允許訪問AP，1：禁止訪問AP
    iwpriv ra0 set AccessPolicy=0

    ResetCounter，重設計算器
    iwpriv ra0 set ResetCounter=1

    SiteSurvey 請求動作做站點測量
    iwpriv ra0 set SiteSurvey=
    被動掃描：空串，iwpriv ra0 set SiteSurvey=
    主動掃描：目的SSID，iwpriv ra0 set SiteSurvey=Target_SSID

    CountryString 設定國家
    iwpriv ra0 set CountryString=China

    FixedTxMode設定傳送調製模式,CCK OFDM HT
    iwpriv ra0 set FixedTxMode=CCK
    DisConnectSta斷開一個指定的STA
    iwpriv ra0 set DisConnectSta=00:11:22:33:44:55
    *
    DisConnectAllSta 斷開所有sta
    iwpriv ra0 set DisConnectAllSta=1
    *
    McastPhyMode 設定多播物理模式,0:Disable; 1:CCK;2:OFDM;3:HTMIX
    iwpriv ra0 set McastPhyMode=0
    *
    McastMcs設定多播包的MCS，0~15
    iwpriv ra0 set McastMcs=0
    *
    MaxStaNum 現在每一個BSS可以管理sta的最大值 1~32
    iwpriv ra0 set MaxStaNum=0
    0:禁用限制
    *
    AutoFallBack 啟用/禁用自動降低速率功能。0：disable； 1：enable
    iwpriv ra0 set AutoFallBack=1
    *

    MBSSWirelessMode 設定MBSS 無線物理方式
    iwpriv ra0 set MBSSWirelessMode=1
    0:802.11B/G mixed
    1:802.11B only
    2:801.11A only
    4：801.11G only
    6：801.11N only
    7：801.11G/N mixed
    8：801.11A/N mixed
    9：801.11B/G/Nmixed
    10：801.11A/G/N mixed
    11：801.11N in 5G band only

    HtBw HT通道頻寬設定, 0:20MHz;1:20/40 MHz
    iwpriv ra0 set HtBw=1

    HtMcs 設定無線調製編碼策略， 0~15,32:fix MCS rate, 33,自動適配
    iwpriv ra0 set HtMcs=33

    HtGi 設定無線guard 間隔，0：長間隔；1短間隔
    iwpriv ra0 set HtGi=1

    HtOpMode 設定HT操作模式，0：HT混合模式，1:HT greenfield模式
    iwpriv ra0 set HtOpMode=0

    HtBaWinSize 設定Block Ack 視窗大小，1~64
    iwpriv ra0 set HtBaWinSize=64

    HtTxBASize 設定一次傳輸burst中AMPDU聚合包的個數，1~64
    iwpriv ra0 set HtBASize=64

    HtAmsdu 啟用禁用A-MSDU，0 禁用，1啟用
    iwpriv ra0 set HtAmsdu=0

    HtAutoBa 啟用禁用自動block ack,0 禁用，1啟用
    iwpriv ra0 set HtAutoBa=1

    HtMimoPs 啟用禁用HT MIMMO power save 模式,1：enable，0：disable
    iwpriv ra0 set HtMimoPs=1

    AP2040Rescan 觸發HT20/40 coexistence重新掃描，1：觸發
    iwpriv ra0 set AP2040Rescan=1

    HtBssCoex 啟用禁用HT BSS coexistence，0 禁用，1啟用
    iwpriv ra0 set HtBssCoex=1

    AssocReqRssiThres設定關聯請求時接收靈敏度的閾值，使拒絕STA的關聯請求在弱訊號的情況下
    iwpriv ra0 set AssocReqRssiThres=-88
    0：關閉
    0~-100RSSI的值

    stat 顯示無線統計資訊
    iwpriw ra0 stat
    或者：
    while [ 1 ]; do iwpriv ra0 set ResetCounter=1; sleep 1; iwpriv ra0 stat; done;

    get_site_survey 獲取掃描資訊
    iwpriv ra0 get_site_survey
    執行該命令前先執行iwpriv ra0 set SiteSurvey=

    get_mac_table 獲取連線到AP的sta的mac地址資訊
    iwpriv ra0 get_mac_talbe

    get_ba_table 顯示BlackACK table
    iwpriv ra0 get_ba_table

    show 顯示資訊
    iwpriv ra0 show [parameter]
    [parameter list]
    1.driverinfo
    2.stat
    3.stainfo
    4.stacountinfo
    5.stasecinfo
    6.bainfo
    7.connStatus
    8.reptinfo
    9.wdsinfo
    10.igmpinfo
    11.mbss
    12.blockch
```


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
![alt tag](https://vitux.com/wp-content/uploads/2018/08/word-image-46.png)

### Listing All Users
```
$ sudo awk -F':' '$2 ~ "\$" {print $1}' /etc/shadow
```
![alt tag](https://vitux.com/wp-content/uploads/2018/08/word-image-47.png)

### Locking/Unlocking User Accounts
```
$ sudo passwd -l username
$ sudo passwd -u username
```

### Giving Root Privilege to a User  
```
$ sudo nano visudo
```

```
[username] ALL=(ALL) ALL
```

```
User_Alias ADMINS = [username]

Cmnd_Alias HTTPD = /etc/init.d/httpd

ADMINS ALL = HTTPD
```
![alt tag](https://vitux.com/wp-content/uploads/2018/08/word-image-48.png)


### Deleting a User Through the Command Line  
```
$ sudo deluser [username]
```
![alt tag](https://vitux.com/wp-content/uploads/2018/08/word-image-49.png)  

# Wifi is not working on my Dell E6400  
[Killer Wireless 1650 on Ubuntu 18.04 doesn't work Sep 9, 2019](https://askubuntu.com/questions/1172026/killer-wireless-1650-on-ubuntu-18-04-doesnt-work)  
```
1. Apparently it's important to turn off your secure boot before the following actions.

2. To fix the No Wifi Adapter found, you need a Internet connection. 
If you have an Ethernet port on your laptop it's good, else, 
you have to use an adapter. Personnaly I used a USB-C to LAN adapter and it works.

3. Once you have a connection, you can update and upgrade packages (Maybe not necessary, but always good) sudo apt update && sudo apt upgrade.
```
4. Execute all of the commands on [this article](https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/) 
```
sudo apt-get install git
sudo apt-get install build-essential

git clone https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git
cd backport-iwlwifi
make defconfig-iwlwifi-public
make -j4
sudo make install

sudo git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp iwlwifi-* /lib/firmware/
```

5. Before reboot, execute this command to update initramfs  
```
sudo update-initramfs -u.  
```
6. Now you can reboot.

# Killer AX1650 in Debian/Ubuntu 16.04+   
[Killer AX1650 in Debian/Ubuntu 16.04+](https://support.killernetworking.com/knowledge-base/killer-ax1650-in-debian-ubuntu-16-04/)  
```
UPDATE: 2019/10/25
There is a new method for getting an AX1650 WiFi adapter working on Debian/Ubuntu systems. 
Run the following commands one by one and reboot your Computer. 
If your AX1650 is still not detected/used you can scroll down and try the older Backport steps.
```

```
$ sudo add-apt-repository ppa:canonical-hwe-team/backport-iwlwifi
$ sudo apt-get update
$ sudo apt-get install backport-iwlwifi-dkms
$ reboot
```
![Imgur](https://i.imgur.com/5BOGtqr.jpg)  

![Imgur](https://i.imgur.com/zDZpujg.jpg)  

![Imgur](https://i.imgur.com/2IlJgGO.jpg)  


[Ubuntu 18.04 Intel Wireless-AC 3165 unreachable Dec 26, 2018](https://askubuntu.com/questions/1104615/ubuntu-18-04-intel-wireless-ac-3165-unreachable)

```
Error msg:

libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '“options'
```

```
We see this in your wireless info:

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
“options iwlwifi disable_msix=1”

The final line is mal-formed and must be removed:

sudo nano /etc/modprobe.d/iwlwifi.conf

Remove the final line:

“options iwlwifi disable_msix=1”

Save (Ctrl+o followed by Enter) and exit (Ctrl+x) the text editor.
```

[Wifi is not working on my Dell E6400 Apr 22, 2015](https://askubuntu.com/questions/215194/wifi-is-not-working-on-my-dell-e6400/215209)  

```
$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
0c:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
```


[No wifi option on Ubuntu (18.04 and 16.04) May 20, 2018](https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04)  


[No wi-fi adapter found - Ubuntu 18.04.2 LTS Apr 5, 2019](https://askubuntu.com/questions/1131326/no-wi-fi-adapter-found-ubuntu-18-04-2-lts)  


[Intel Corporation Ultimate N WiFi Link 5300 ubuntu 10.10 Jan 12, 2011](https://ubuntuforums.org/showthread.php?t=1665066)  

[Ubuntu 18.04: No WiFi adapter found - secure boot disabled Mar 20, 2019](https://askubuntu.com/questions/1127216/ubuntu-18-04-no-wifi-adapter-found-secure-boot-disabled)  


[Wireless woes after Ubuntu 16 upgrade [SOLVED?]  (Read 13713 times) ](https://linuxforums.org.uk/index.php?topic=12928.0)  

[network manager - Ubuntu 1510上のルーターへのIntel Centrino Wi-Fi high ping](https://tutorialmore.com/questions-296444.htm)  


# Lenovo Thinkpad X201i A22安裝Ubuntu Studio  
[Lenovo Thinkpad X201i A22安裝Ubuntu Studio心得+初音鼓  Aug 20, 2010](https://magicdesign.blogspot.com/2010/08/lenova-thinkpad-x201i-a22ubuntu-studio.html)  

[自製 Ubuntu 16.04.X/17.10/18.04.X/18.10 測試硬體安裝使用的 USB 隨身碟 Jul 27, 2018](https://fourdollars.blogspot.com/2018/07/ubuntu-1604x17101804x1810-usb.html)  

[Ubuntu日本語フォーラム / ThinkPad X201iでwifiで通信ができない。Apr 6, 2012](https://forums.ubuntulinux.jp/viewtopic.php?id=13267)  

# linux ubuntu 18.04安裝心得  

## 1．Win10 and Ubuntu 雙系統安裝筆記  
[1．Win10 and Ubuntu 雙系統安裝筆記 Jun 1, 2018](https://medium.com/caesars-study-review-on-web-development/win10-and-ubuntu-%E9%9B%99%E7%B3%BB%E7%B5%B1%E5%AE%89%E8%A3%9D%E7%AD%86%E8%A8%98-bc824bef7fb4)  

```
2016年以後出廠的主機板大多為UEFI的開啟模式，所以要安裝雙系統的話，你的Live USB安裝程式，
要選擇GPT and UEFI的形式來安裝，不要與傳統boot(Legacy)的安裝方式混淆，
建議還是查清楚自己的磁碟分割是什麼形式GPT 還是 MBR，再來尋找網路上安裝ubuntu的資料。
```

```
在實際安裝後，我對於上述參考所說的，不需要關閉secure boot有其他看法，
雖然安裝純粹的Ubuntu不需要關閉，但若是安裝一些第三方的驅動程式，
你還是要關閉secure boot才可以安裝驅動到Ubuntu中

第三方的驅動程式，可能是你的WIFI卡，各家廠牌的顯卡，普遍這些廠商沒有經過Linux的測試，
只能靠第三方的驅動程式來讓它們運行

目前正在被nvidia的顯卡，搞得很痛苦，18.04 系統各種運作不正常QQ
```

```
製作Live Usb，我選擇 Ubuntu官方主推的工具Rufus，使用方式很容易，記得資料分割配置選GPT，
檔案系統選FAT32格式， UEFI只認FAT32格式，所以製作USB開機碟不可選擇NTFS

若你的主機板是傳統bios開機，資料分割配置才選MBR

如果你是選擇UEFI的方式安裝，直接解壓縮Ubuntu.ISO的檔案也可以，解壓縮後可以發現有EFI資料夾
```
[Rufus Create bootable USB drives the easy way](https://rufus.ie/)  

```
若安裝在不同硬碟 ，基本上可以看成安裝單一系統，磁區切割為以下方式，順便 區分UEFI and Legacy BIOS System的磁區切割方式

    UEFI System:
    EFI – 500MB
    swap – 4098MB (2*RAM)
    / – Remaining (95GB)

    Legacy BIOS:
    /boot – 500MB
    swap – 4098MB (2*RAM)
    / – Remaining (95GB)
```
[How to Install Ubuntu 18.04 LTS (Bionic Beaver) on UEFI and Legacy BIOS System Jul 12, 2018](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-install-ubuntu-18-04-lts-bionic-beaver-on-uefi-and-legacy-bios-system.html?source=post_page-----bc824bef7fb4----------------------)  



```
可能遇到的困難，但是我沒遇到，做個紀錄，避免以後遇到

1. 獨立顯卡問題 

2. 硬碟的順序不是固定

3. 在 Windows 10 进行了一个大更新后，会发现 GRUB 引导界面没有了
```

```
EFI的開機跟傳統MBR碟開機的不同

BIOS → 硬碟啟動磁區（會放個 GRUB loader）
→ GRUB → 載入 Linux kernel 跟 initrd 
→ 掛載主硬碟分割做根目錄 → init。

EFI+GPT 開機：
EFI firmware → EFI system partition（FAT32 檔案系統，裡面放一個BootX64.efi）
→ bootloader（GRUB 或 systemd-boot 自己選一個）
→ 載入 Linux kernel 跟 initrd 
→ 掛載主硬碟分割做根目錄 → init。
```
[Ref: 臉書Ubuntu 正體中文社團， 宋岡哲 提供](https://www.facebook.com/groups/ubuntu.zh.hant/permalink/2062444210477557/)  

## 2. acpi_osi=linux、 nomodeset是什麼意思? 功能?  
[2. acpi_osi=linux、 nomodeset是什麼意思? 功能? Jun 4, 2018](https://medium.com/caesars-study-review-on-web-development/acpi-osi-linux-nomodeset%E6%98%AF%E4%BB%80%E9%BA%BC%E6%84%8F%E6%80%9D-%E5%8A%9F%E8%83%BD-42d8e2c444c3)

## 3. ubuntu 18.04實際安裝 簡略步驟
[3. ubuntu 18.04實際安裝 簡略步驟 nvidia 顯卡驅動安裝 Jun 10, 2018](https://medium.com/caesars-study-review-on-web-development/ubuntu-18-04%E5%AF%A6%E9%9A%9B%E5%AE%89%E8%A3%9D-%E7%B0%A1%E7%95%A5%E6%AD%A5%E9%A9%9F-b023f61436bf)

# How to Upgrade To Ubuntu 18.04 From Ubuntu 16.04/Ubuntu 17.10
[How to Upgrade To Ubuntu 18.04 From Ubuntu 16.04 / Ubuntu 17.10 [Detailed Guide] Apr 27, 2018](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/how-to-upgrade-to-ubuntu-18-04-from-ubuntu-16-04-ubuntu-17-10-detailed-guide.html)  


# Ubuntu 18.04 remote desktop with xrdp TroubleShooting   
[ubuntu18.04でのxrdpトラブル対応 　と　リモートデスクトップ設定 Nov 06, 2019](https://qiita.com/underwell111/items/c0069a4d39d3694e1d4a)  
## 1.パッケージのインストール  
```
sudo apt-get -y install xserver-xorg-core xorgxrdp xrdp　（xrdpだけではダメ）
sudo apt-get -y install xserver-xorg-input-all　(これがマウス・キーボード対策)
```
![alt tag](https://i.imgur.com/3OvC01A.jpg)  

# 2.新カーソルの無効化  
```
sudo sed -e 's/^new_cursors=true/new_cursors=false/g' -i /etc/xrdp/xrdp.ini
sudo systemctl restart xrdp
```
![alt tag](https://i.imgur.com/xhsCXx5.jpg)  
![alt tag](https://i.imgur.com/Yt5Q7mc.jpg)  

# 3.~/.xsessionrcの作成  
```
$ D=/usr/share/ubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop
$ cat <<EOF > ~/.xsessionrc
export GNOME_SHELL_SESSION_MODE=ubuntu
export XDG_CURRENT_DESKTOP=ubuntu:GNOME
export XDG_DATA_DIRS=${D}
export XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
EOF
```
![alt tag](https://i.imgur.com/kKBHhEv.jpg)  

# 4.「カラープロファイルを作成するには認証が必要です」の回避  
sudo vim　で作成するのが良い  
/etc/polkit-1/localauthority.conf.d/02-allow-colord.conf  
```
polkit.addRule(function(action, subject) {
   if ((action.id == "org.freedesktop.color-manager.create-device" ||
        action.id == "org.freedesktop.color-manager.create-profile" ||
        action.id == "org.freedesktop.color-manager.delete-device" ||
        action.id == "org.freedesktop.color-manager.delete-profile" ||
        action.id == "org.freedesktop.color-manager.modify-device" ||
        action.id == "org.freedesktop.color-manager.modify-profile") &&
       subject.isInGroup("**")) {
      return polkit.Result.YES;
   }
});
```
![alt tag](https://i.imgur.com/LrADijr.jpg)  

# 5. Enjoy  
![alt tag](https://i.imgur.com/tqEvymQ.jpg)  

# 参考サイト  
[Ubuntu 18.04: GNOMEデスクトップ環境にXRDPで接続する 4/28  2018](https://www.hiroom2.com/2018/04/28/ubuntu-1804-xrdp-gnome-ja/)  
[Ubuntu18.04.2にxrdpをインストールしてもRDP経由のログインでエラーになる事象のメモ 2019.03.12](https://note.spage.jp/archives/576)  
[xRDP からログインした時の「カラープロファイルを作成するには認証が必要です」ダイアログを消す](http://aimingoff.way-nifty.com/blog/2017/06/xrdp-4be6.html) 


[Ubuntu Linux 18.04.1 再インストール手順 May 06, 2019](https://qiita.com/tfukumori/items/cbcd4d961d1740fca69d)  


# Ubuntu 18.04 XRDP Remote Desktop Config & Problem  
[[Linux] Ubuntu 18.04 XRDP Remote Desktop Config & Problem Aug 2, 2018](https://www.azureunali.com/linux-ubuntu-18-04-xrdp-remote-desktop-config-problem/)  

## 無法轉入登入畫面的問題 ( Xwrapper Problem )  
(1) 輸入完帳號密碼，卻無法轉入桌面模式，變成一片青綠色卡住不動，最後跳出connection error
```
vim /etc/X11/Xwrapper.config
allowed_users=console
 
# Change to
allowed_users=anybody
 
# You will need to logout or restart PC, after you change the service's config. 
```
![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_007.png)  

## 沒有Gnome桌面圖示的排除方法 ( No Gnome Icon or Env Problem )  
(2) 沒有Gnome的基本圖示

![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_003.png)  
![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_004.png)  

解決方法是在想要登入的帳號家目錄底下增加，.xsessionrc的檔案  
```	
vim ~/.xsessionrc
xrDp=/usr/share/ubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop
export GNOME_SHELL_SESSION_MODE=ubuntu
export XDG_CURRENT_DESKTOP=ubuntu:GNOME
export XDG_DATA_DIRS=${xrDp}
export XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
```
![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_005.png)  
![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_006.png)  

## 跳出授權警告視窗 ( Authentication Required to Create Managed Color Device Problem )  
(3) 跳出授權的警告視窗
跳出的授權警告是因為Polkit的管制造成的，Polkit是用來管理桌面應用程式權限的服務，
目前在xrdp的部分當跳出授權視窗後你輸入了2次密碼( Enter Password twice )，
遠端桌面連線會直接斷線( connection off )，所以不在意的人可以直接選擇取消( Cancel)，反而就能登入桌面環境  

![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_001.png)  
![alt tag](https://www.azureunali.com/wp-content/uploads/2018/08/U18XRDP_002.png)  

而會在意這個問題的人，請依照下面的方法把Polkit對xrdp的權限關閉，就可以讓授權警告視窗不會在跳出來了，  
```	
vim /etc/polkit-1/localauthority/50-local.d/45-allow.colord.pkla
 
[Allow Colord all Users]
Identity=unix-user:*
Action=org.freedesktop.color-manager.create-device;org.freedesktop.color-manager.create-profile;org.freedesktop.color-manager.delete-device;org.freedesktop.color-manager.delete-profile;org.freedesktop.color-manager.modify-device;org.freedesktop.color-manager.modify-profile
ResultAny=no
ResultInactice=no
ResultActive=yes
```

# Ubuntu 18.04 remote desktop with xrdp  
[ubuntu 18.04 remote desktop with xrdp Mar 12, 2019](http://lookers-on.blogspot.com/2019/03/ubuntu-1804-remote-desktop-with-xrdp.html)  
```
本來16.04可以用的方法到18.04就不能用了，
試了一堆ubuntu分支(Kubuntu、Xubuntu)也沒辦法直接用xrdp連線，
最後找到人家寫好了script按下去，能連了...
不過會變成本地端的桌面登入後有些問題(沒有反應?)
就再灌個xfce4解決(跟16.04反過來了XD)
另外多灌一個桌面也可以兩個相同帳號同時登入就是。
```
[xRDP – Custom Installation Script for Ubuntu 18.10 – version 2.2](http://c-nergy.be/blog/?p=12894)  
寫好的腳本直接裝就好  
[使用xrdp实现windows 远程桌面 ubuntu linux](https://blog.csdn.net/daniel_ustc/article/details/16845327)  
16.04可以用的方法    
[Install XRDP on Ubuntu Server with XFCE Template](https://www.interserver.net/tips/kb/install-xrdp-ubuntu-server-xfce-template/)  
server版本是可以連拉，只是中文都亂碼... 

# Fix ‘E: Could not get lock /var/lib/dpkg/lock’ Error in Ubuntu [Quick Tip]  
[Fix ‘E: Could not get lock /var/lib/dpkg/lock’ Error in Ubuntu [Quick Tip] Dec 20, 2019](https://itsfoss.com/could-not-get-lock-error/)  



# 新酷音輸入法 
[[Ubuntu] 在 Ubuntu 18.04 中新增新酷音輸入法 Jun 2, 2019](https://medium.com/@racktar7743/ubuntu-%E5%9C%A8-ubuntu-18-04-%E4%B8%AD%E6%96%B0%E5%A2%9E%E6%96%B0%E9%85%B7%E9%9F%B3%E8%BC%B8%E5%85%A5%E6%B3%95-4aa85782f656)

```
sudo apt install ibus-chewing
```


# Array-30(行列30) Input Method Installation  
[Ubuntu 12.04 安裝行列30輸入法 7th July 2012](http://dodgelin.blogspot.com/2012/07/ubuntu-1204-30.html)  
```
 在命令列視窗中輸入
sudo apt-get install ibus-array
Enter 執行後會要求使用者輸入密碼確認 sudo
```

```
有網際網路的狀況下，系統會自動從網路應用程式套件庫中，下載安裝所需程式。
執行完畢 之後會回到命令列提示之下

再度登入桌面之後，點選Dash主目錄，輸入ibus，點擊執行下方的鍵盤輸入法
```

[ubuntu 18.04 使用fcitx 取代ibus 2018年5月7日](http://t301000.blogspot.com/2018/05/ubuntu-1804-fcitx-ibus.html)  
```
方法 1：
強迫 ibus 不執行
sudo mv /usr/bin/ibus-daemon /usr/bin/ibus-daemon.bak
kill 掉 ibus-daemon 或重開機
```

```
方法 2：
移除 ibus
sudo apt remove ibus
```

```
方法 2 會在打開語言支援時要求將 ibus 裝回，所以方法 1 似乎是比較好的選擇

安裝 fcitx 與新酷音：
sudo apt install fcitx fcitx-chewing

將  語言支援  中的  鍵盤輸入法系統  選擇 fcitx
```
sublime text 修正檔下載：  
[不專業網管筆記: ubuntu 下解決 Sublime Text 3 無法輸入中文的問題](http://t301000.blogspot.com/2014/04/ubuntu-sublime-text-3_30.html)  


# DNS on Ubuntu 18.04  

## How to Set DNS Nameservers on Ubuntu 18.04  
[How to Set DNS Nameservers on Ubuntu 18.04 Aug 21, 2019](https://linuxize.com/post/how-to-set-dns-nameservers-on-ubuntu-18-04/)

* Google (8.8.8.8, 8.8.4.4)  
* Cloudflare (1.1.1.1 and 1.0.0.1)  
* OpenDNS (208.67.222.222, 208.67.220.220)  
* Level3 (209.244.0.3, 209.244.0.4)  

### Setting DNS Nameservers on Ubuntu Desktop  

1. Launch the Settings window.

2. If you are connected to a WiFi network click on the “Wi-FI” tab. Otherwise, if you have a wired connection click on the “Network” tab.

3. Select the connection for which you want to set the DNS nameservers and click on the cog icon to open the Network Manager.

4. Select the IPv4 Settings tab.

5. Disable the “Automatic” toggle switch and enter the DNS resolvers IP addresses, separated by a comma. We'll use the Google DNS nameservers:  
![alt tag](https://linuxize.com/post/how-to-set-dns-nameservers-on-ubuntu-18-04/ubuntu-dns-nameservers.jpg)  

6. Click on the “Apply” button to save the changes.  

### Setting DNS Nameservers on Ubuntu Server  
systemd-resolved is a service that provides DNS name resolution to local services and applications and it can be configured with Netplan, the default network management tool on Ubuntu 18.04.  

Netplan configuration files are stored in the /etc/netplan directory. 
You’ll probably find one or two YAML files in this directory. 
The file name may differ from setup to setup. 
Usually, the file is named either 01-netcfg.yaml or 50-cloud-init.yaml but in your system, it may be different.  

```
$ sudo nano /etc/netplan/01-netcfg.yaml
```

/etc/netplan/01-netcfg.yaml  
```
network:
  version: 2
  renderer: networkd
  ethernets:
    ens3:
      dhcp4: no
      addresses:
        - 192.168.121.199/24
      gateway4: 192.168.121.1
      nameservers:
          addresses: [8.8.8.8, 8.8.4.4]
```

```
$ sudo netplan apply
```

```
$ systemd-resolve --status | grep 'DNS Servers' -A2
```
```
output

         DNS Servers: 1.1.1.1
                      1.0.0.1
```

## How to Clear the DNS Cache  
[How to Clear the DNS Cache Oct 22, 2019](https://linuxize.com/post/how-to-clear-the-dns-cache/)  

### Clear/Flush DNS Cache on Linux  
On Linux, there is no OS-level DNS caching unless a caching service 
such as Systemd-Resolved, DNSMasq, or Nscd is installed and running. 
The process of clearing the DNS cache is different depending on the 
Linux distribution and the caching service you're using.

#### Systemd Resolved   
To find out whether the service is running use the following command:  
```
sudo systemctl is-active systemd-resolved.service
```
```
sudo systemd-resolve --flush-caches
```

#### DNSMasq  
If your system is using DNSMasq as a caching server, 
to clear the DNS cache you need to restart the Dnsmasq service:  
```
sudo systemctl restart dnsmasq.service
```
Or  
```
sudo service dnsmasq restart
```

#### Nscd  
Nscd is a caching daemon, and 
it is the preferred DNS caching system for most of RedHat-based distributions.  
```
sudo systemctl restart nscd.service
```
Or  
```
sudo service nscd restart
```

## DNS on Ubuntu 18.04  
[DNS on Ubuntu 18.04 | datawookie Oct 25, 2018](https://datawookie.netlify.com/blog/2018/10/dns-on-ubuntu-18.04/)
Just add a couple of entries to /etc/resolv.conf   
```
# Use Google's public DNS servers.
nameserver 8.8.4.4
nameserver 8.8.8.8
```

This is pretty simple to fix though.  
1. Install the resolvconf package.  
```
sudo apt install resolvconf
```
2. Edit /etc/resolvconf/resolv.conf.d/head and add the following:  
```
# Make edits to /etc/resolvconf/resolv.conf.d/head.
nameserver 8.8.4.4
nameserver 8.8.8.8
```
3. Restart the resolvconf service.  
```
sudo service resolvconf restart
```


# Photo Editor: Shutter 
[Ubuntu 上的螢幕截圖編輯軟體 - Shutter 2021-09-14](https://cynthiachuang.github.io/Shutter-A-Screenshot-Editor-on-Ubuntu/)

## Ubuntu 20.04
```
$ sudo add-apt-repository ppa:shutter/ppa
```

```
$ sudo apt-get update
$ sudo apt-get install shutter
```

## Trouble shooting： photo can't edit

```
$ wget https://launchpad.net/ubuntu/+archive/primary/+files/libgoocanvas-common_1.0.0-1_all.deb
$ wget https://launchpad.net/ubuntu/+archive/primary/+files/libgoocanvas3_1.0.0-1_amd64.deb
$ wget https://launchpad.net/ubuntu/+archive/primary/+files/libgoo-canvas-perl_0.06-2ubuntu3_amd64.deb

```

```
$ sudo dpkg -i libgoocanvas-common_1.0.0-1_all.deb
$ sudo dpkg -i libgoocanvas3_1.0.0-1_amd64.deb
$ sudo dpkg -i libgoo-canvas-perl_0.06-2ubuntu3_amd64.deb
$ sudo apt -f install
```

```
$ sudo rm libgoocanvas-common_1.0.0-1_all.deb
$ sudo rm libgoocanvas3_1.0.0-1_amd64.deb
$ sudo rm libgoo-canvas-perl_0.06-2ubuntu3_amd64.deb
```


# Firefox browser can't play video 
[解决ubuntu20.04火狐浏览器不能播放视频](https://blog.csdn.net/Joker_mw/article/details/115426829)

```
sudo add-apt-repository multiverse
sudo apt install ubuntu-restricted-extras
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```


# Mount WebDAV 

[buntu 22.04 开机自动挂载webdav - 设置开机自启脚本 - 解决坚果云webdav无写入权限](https://blog.csdn.net/qq285744011/article/details/137750762)  

<img src="webdav_client_01.jpg" width="600" height="700">  

<img src="webdav_client_02.jpg" width="600" height="800">  

<img src="webdav_client_03.jpg" width="600" height="400">  

[免费获取 45GB 网络空间！支持 WebDav 协议，直接挂载到本地电脑进行扩容！ | 零度解说](https://www.youtube.com/watch?v=RpTozaS03us)

[Creating WebDAV mounts on the Linux command line](https://www.youtube.com/watch?v=uvdSExZLjcg)
```
sudo apt-get install davfs2
sudo usermod -aG davfs2 <ubuntu_username>
mkdir ~/infinicloud
mkdir ~/.davfs2
sudo cp /etc/davfs2/secrets ~/.davfs2/secrets
sudo chown <ubuntu_username>:<ubuntu_username> ~/.davfs2/secrets
sudo chmod 600 ~/.davfs2/secrets
sudo nano ~/.davfs2/secrets

sudo nano /etc/fstab
```

[davfs2 unable to create files, no problem creating directoies](https://askubuntu.com/questions/1286523/davfs2-unable-to-create-files-no-problem-creating-directoies)

```
I have forgotten to add the following two lines in /etc/davfs2/davfs2.conf:

dav_group users
use_locks 0
```

# WebDAV Server by Nginx 
[NGINX 設定 WebDAV (HTTPS + Authentication) 2021-02-10](https://blog.louie.lu/2021/02/10/nginx-webdav-https-authentication/)  
A. 安裝與設定 NGINX  
B. 測試 NGINX WebDAV (w/o HTTPS/Authentication)  
C. 設定 NGINX Authentication  

D. 設定 WebDAV HTTPS  

   安裝 certbot
```
$ apt install certbot
```
   
   設定 certbot
```
$ certbot --nginx your-webdav-domain.com
```
   
   透過 cadaver 測試 WebDAV 是否有啟動成功 (https://your-webdav-domain.com)
```
$ cadaver https://your-webdav-domain.com
Authentication required for Restricted webdav on server `your–webdav–domain.com‘:
Username: user1
Password: 
dav:/> ls
Listing collection `/’: succeeded.
dav:/> 
```

[用 NGINX 配置一個 WebDAV Server Nov 16, 2019](https://medium.com/learn-or-die/%E7%94%A8-nginx-%E9%85%8D%E7%BD%AE%E4%B8%80%E5%80%8B-webdav-server-95665d029042)  
[使用Nginx搭建WebDav作为简易共享空间](https://imateor.com/archives/342.html)  

[Nginx で WebDAV 環境構築、PROPFIND 405 が使えなかったのでソースからコンパイルしてみた 2021/04/10](https://zenn.dev/murachi/articles/a67ae7b617d459e04615)  
[WebDAVをnginxだけで作る備忘録 2020-01-25](https://qiita.com/YuzuRyo61/items/176ed017cefbaa872a63)  
[Ubuntu (Debian) で nginx に WebDAV拡張モジュール(ngx-dav-ext-module)を組み込むで使ってみる 2012年11月1日](https://server-setting.info/ubuntu/ubuntu-nginx-webdav-module.html)    


# 設定系統時區和時間 使用 crontab 排程  
[如何在 Ubuntu Server 20.04 使用指令設定系統時區 2022-03-20]()  
*查看機器目前時區*
```
$ timedatectl
      Local time: Fri 2022-02-11 02:37:02 UTC
  Universal time: Fri 2022-02-11 02:37:02 UTC
        RTC time: Fri 2022-02-11 02:36:58
       Time zone: Etc/UTC (UTC, +0000)
 Network time on: yes
NTP synchronized: yes
 RTC in local TZ: no
```

*列出所有支援的時區資料*
```
$ timedatectl list-timezones | grep Taipei
Asia/Taipei
```

*設定時區*
```
$ sudo timedatectl set-timezone Asia/Taipei
```

[[Linux] 設定系統時區和時間 2018-10-12](https://wshs0713.github.io/posts/7c844aef/)  
*設定時區*
```
$ sudo cp /usr/share/zoneinfo/Asia/Taipei /etc/localtime
```
*設定時間*
```
# 格式: MMDDhhmmYYYY
$ sudo date "101213002018"
```

[[Linux] 使用 crontab 排程 2018-03-14](https://wshs0713.github.io/posts/d661a182/)  
```
$ crontab <crontab_file>
```

*crontab 相關指令*
```
    $ crontab -l: 列出使用者的 crontab 內容。
    $ crontab -e: 編輯使用者的 crontab 內容。
    $ crontab -r: 完全清除使用者的 crontab. (要小心使用!)
```

*crontab 範例*
```
SHELL=/bin/sh
PATH=/bin:/sbin:/usr/bin:/usr/sbin
MAILTO="your_email"

# 分 時 日 月 星期 指令
0 1 * * * sh /home/user/crontab/report.sh
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

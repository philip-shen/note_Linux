# Purpose
Take note of IPv6 PPPoE

# Table of Content
[Setup Procedure](#setup-procedure)  

[sudo sysctl -w net.ipv6.conf.all.forwarding=1](#sudo-sysctl--w-netipv6confallforwarding1)  
[]()  
[]()  
[]()  

[Accel-ppp installation](#accel-ppp-installation)  

[Setup accel-ppp PPTP / L2TP / PPPoE server](#setup-accel-ppp-pptp--l2tp--pppoe-server)  
[Daemo start before and after](#daemo-start-before-and-after)  
[PPTP MS-CHAPv2 Authentication Pass](#pptp-ms-chapv2-authentication-pass)  

[Troubleshooting](#troubleshooting)  
[エラー解決：Mac os X で (sh: sysctl: command not found)などコマンドが見つからないエラー  20161012]()  
[How to increase SSH Connection timeout?](#how-to-increase-ssh-connection-timeout)  

# Setup Procedure
## sudo sysctl -w net.ipv6.conf.all.forwarding=1  
## 1. Starting pppoe server   
```
pppoe-server -I eth0 220.18.1.100 -R 220.18.1.150-160
```
## 2. Waiting PPP0 interface up  
```
ip -6 addr add 2001:aaaa:bbbb:cccc:1111:2222:3333:65/64 dev ppp0
```

## 3. Initial DHCP-PD     
```
(/etc/dibbler/dibbler-server run)
Note, sometim dibbler-server console start, that may link-local address don't assign in PPP0
```

## 4. Initial radvd  
```
(/etc/rc.d/init.d/radvd restart)
Note, /etc/radvd.conf

ip -6 route add 3000:458:ff01:86f::/64 via 2001:aaaa:bbbb:cccc:224:1ff:fe44:bc8b
route -A inet6 -n
ip -6 route show
```

## How to add 6in4  
```
remote_ipv4=172.21.3.147
remote_ipv6=2001::1
local_ipv4=172.21.33.97
local_ipv6=2001::97/64
```

## stepup sit1  
```
ip tunnel add sit1 remote $remote_ipv4 local $local_ipv4 ttl 64 ip link set dev sit1 up
```

## add local ipv6 address in sit1  
```
ip -6 addr add $local_ipv6 dev sit1
```

## add default route to remote ipv6 address  
```
route -A inet6 add ::/0 gw $remote_ipv6 dev sit1 metric 256 
```
# Accel-ppp installation  
[Accel-ppp installation 06.07.2018](https://ixnfo.com/en/accel-ppp-installation.html)  
```
In this article, I’ll give an example of how to build and install accel-ppp in Ubuntu Server.
```
## Setup accel-ppp PPTP / L2TP / PPPoE server  
```
From: Ted Chen(陳明德) 
Sent: Thursday, August 8, 2019 4:16 PM
To: Richard Tu(涂振彬); Philip Shen(沈宣佑); Monica Su(蘇郁鈞)
Cc: Jimmy Pan(潘信嘉)
Subject: Setup accel-ppp PPTP / L2TP / PPPoE server

Dear All,

FYI,

以下方式可以簡單架設自己的PPTP/L2TP/PPPoE server

如果只是要測試連線，server只要一張網卡就可以，但如果要測throughput則要兩張網卡會獲得比較好的performance result。

架構:

DUT WAN------------------Ubuntu(accel-ppp server)
             |
             |
      Gateway Router LAN
      Gateway Router WAN
             |
             |
          Internet


Ubuntu 版本:
16.04-2 
或
14.04.1 TLS

安裝:
1.	先將ubuntu連上Internet
2.	安裝必要的套件:
#apt-get install cmake 
    
#apt-get install build-essential

#apt-get install libpcre3-dev

#apt-get install libssl-dev

3.	將config檔 (accel-ppp.conf.dist) 複製到 / 根目錄底下
4.	將accel-ppp程式也複製到 / 根目錄底下
5.	開始安裝:
a.	#mkdir /home/accel
b.	#cd /home/accel
c.	#tar xvf /accel-ppp-1.7.4.tar.bz2
d.	#cd /accel-ppp-1.7.4
e.	#mkdir build
f.	#cd build
g.	#cmake ..   (注意，camake後面空一格還有兩個點，一定要加!)
h.	#make
i.	#make install
6.	安裝完成
7.	將Ubuntu與DUT WAN連接好，確認Ubuntu的網卡(server IP)與DUT WAN可以相通
8.	修改連線用的帳號密碼:
#vi /etc/ppp/chap-secrets
```
![alt tag](https://i.imgur.com/RgsioiL.png)  
``` 
第一個test是帳號
第二個test是密碼
如果要建立多個，就新增在下一行，格式要一樣:  [帳號]   *   [密碼]   *
改完存檔
9.	修改VPN IP address(DUT WAN會拿到的IP):
#vi /accel-ppp.conf.dist
 
以上的範例，DUT會拿到192.168.200.2的IP，Gateway是192.168.200.1
10.	啟動accel-ppp server:
#accel-pppd -d -c /accel-ppp.conf.dist
11.	完工!

以上，DUT可以建立PPTP/L2TP/PPPoE連線，可作簡易連線測試，包括可自訂DUT WAN會拿到的IP，
或是特殊字元的帳號密碼。  

如果要可以上網(要先確認Ubuntu本身可以上網)，可以在DUT已經建立連線之後用以下iptable指令

#iptables –t nat –A POSTROUTING –s 192.168.200.0/24 –o eth0 –j MASQUERADE

[192.168.200.0/24]這是在accel-ppp.conf.dist裡面指定給DUT WAN的IP
Eth0是Ubuntu的網卡代號



With regards,
TED CHEN - 陳明德
```

## Daemo start before and after    
*Before*
```
$ netstat -altnup
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN
tcp        0      0 10.0.1.3:22             10.0.1.31:60105         ESTABLISHED
tcp        0    352 10.0.1.3:22             10.0.1.31:60104         ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN
tcp6       0      0 ::1:6010                :::*                    LISTEN
udp        0      0 0.0.0.0:50392           0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*
udp        0      0 127.0.1.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:34893           0.0.0.0:*
udp        0      0 0.0.0.0:631             0.0.0.0:*
udp6       0      0 :::5353                 :::*
udp6       0      0 :::53550                :::*
udp6       0      0 :::39353                :::*
udp6       0      0 fe80::7c49:7209:e6b:546 :::*

```
![alt tag](https://i.imgur.com/uwJkw6g.jpg)  

*After*
```
~$ sudo accel-pppd -d -c /home/accel-ppp.conf.dist

~$ netstat -altnup
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:2000          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:2001          0.0.0.0:*               LISTEN
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN
tcp        0      0 10.0.1.3:1723           10.0.1.29:49050         ESTABLISHED
tcp        0      0 10.0.1.3:22             10.0.1.31:60105         ESTABLISHED
tcp        0      0 10.0.1.3:22             10.0.1.31:60104         ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN
tcp6       0      0 ::1:631                 :::*                    LISTEN
tcp6       0      0 ::1:6010                :::*                    LISTEN
udp        0      0 0.0.0.0:50392           0.0.0.0:*
udp        0      0 0.0.0.0:5353            0.0.0.0:*

udp        0      0 127.0.1.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:34893           0.0.0.0:*
udp        0      0 0.0.0.0:631             0.0.0.0:*
udp        0      0 0.0.0.0:1701            0.0.0.0:*
udp6       0      0 :::5353                 :::*
udp6       0      0 :::53550                :::*
udp6       0      0 :::39353                :::*
udp6       0      0 fe80::7c49:7209:e6b:546 :::*
```
![alt tag](https://i.imgur.com/uWE2pbi.jpg)  

![alt tag](https://i.imgur.com/ygZWu6y.jpg)  

![alt tag](https://i.imgur.com/1OsOYq2.jpg)  

![alt tag](https://i.imgur.com/umw8SHt.jpg)  

![alt tag](https://i.imgur.com/1Z3Ld1Y.jpg)  

![alt tag](https://i.imgur.com/icU91l2.jpg)  

```
:~$ cat /var/log/accel-ppp/emerg.log
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
cli: telnet: failed to bind socket: Address already in use
cli: tcp: failed to bind socket: Address already in use
pptp: failed to bind socket: Address already in use
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
cli: telnet: failed to bind socket: Address already in use
cli: tcp: failed to bind socket: Address already in use
pptp: failed to bind socket: Address already in use
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
cli: telnet: failed to bind socket: Address already in use
cli: tcp: failed to bind socket: Address already in use
pptp: failed to bind socket: Address already in use
iprange: iprange module disabled so improper ip address assigning may cause kernel soft lockup!
```

*accel-ppp.conf_lab.dist*
```
[modules]
log_syslog
#pppoe
pptp
l2tp
auth_mschap_v2
auth_mschap_v1
auth_pap
ippool
chap-secrets

[core]
log-error=/var/log/accel-ppp/core.log
thread-count=4

[ppp]
verbose=1
min-mtu=1280
mtu=1400
mru=1400
ipv4=require
ipv6=deny

[lcp]
echo-interval=30
echo-failure=3

[pptp]
interface=ens32
verbose=1

[pppoe]
interface=eth0
verbose=1

[l2tp]
interface=ens32
verbose=1
use-ephemeral-ports=0

[dns]
dns1=1.1.1.1
dns2=8.8.8.8

[client-ip-range]
disable

[ip-pool]
gw-ip-address=192.168.200.1
192.168.200.2-20

[log]
log-emerg=/var/log/accel-ppp/emerg.log
#syslog=accel-pppd,daemon
copy=1
level=3

[chap-secrets]
gw-ip-address=192.168.200.1
chap-secrets=/etc/ppp/chap-secrets

[cli]
telnet=127.0.0.1:2000
tcp=127.0.0.1:2001
#password=123
```
## PPTP MS-CHAPv2 Authentication Pass  
![alt tag](https://i.imgur.com/fCsQIEr.jpg)  


# Troubleshooting  
* [ssh 互動模式終端機可以執行的指令，透過 ssh 直接下指令卻找不到，竟然是因為這個原因？ Dec 11, 2018](https://medium.com/@hau_hsu/ssh-%E4%BA%92%E5%8B%95%E6%A8%A1%E5%BC%8F%E7%B5%82%E7%AB%AF%E6%A9%9F%E5%8F%AF%E4%BB%A5%E5%9F%B7%E8%A1%8C%E7%9A%84%E6%8C%87%E4%BB%A4-%E9%80%8F%E9%81%8E-ssh-%E7%9B%B4%E6%8E%A5%E4%B8%8B%E6%8C%87%E4%BB%A4%E5%8D%BB%E6%89%BE%E4%B8%8D%E5%88%B0%E4%BA%86-%E7%AB%9F%E7%84%B6%E6%98%AF%E5%9B%A0%E7%82%BA%E9%80%99%E5%80%8B%E5%8E%9F%E5%9B%A0-e252ef6f19d0)  
* [How do I set $PATH such that `ssh user@host command` works? Jun 2 '09](https://stackoverflow.com/questions/940533/how-do-i-set-path-such-that-ssh-userhost-command-works)  
* [エラー解決：Mac os X で (sh: sysctl: command not found)などコマンドが見つからないエラー  20161012](https://paper.hatenadiary.jp/entry/2016/10/12/115446)  
```
# export $PATH
bash: export: `/usr/kerberos/sbin:/usr/kerberos/bin:/usr/local/bin:/bin:/usr/bin:/home/michael/bin': not a valid identifier
# export PATH=$PATH:/sbin/
# source .bashrc
# sysctl
usage:  sysctl [-n] [-e] variable ...
        sysctl [-n] [-e] [-q] -w variable=value ...
        sysctl [-n] [-e] -a
        sysctl [-n] [-e] [-q] -p <file>   (default /etc/sysctl.conf)
        sysctl [-n] [-e] -A
```
# How to increase SSH Connection timeout?  
[How to increase SSH Connection timeout? May 27, 2017](https://www.digitalocean.com/community/questions/how-to-increase-ssh-connection-timeout)  
```
/etc/ssh_config is the client side configuration file not the server side config file.

To prevent all your clients from timing out you need to edit /etc/sshd_config which is the server side configuration file add these two options:

ClientAliveInterval 120
ClientAliveCountMax 720

The first one configures the server to send null packets to clients each 120 seconds and the second one configures the server to close the connection if the client has been inactive for 720 intervals that is 720*120 = 86400 seconds = 24 hours
```
[CentOS / RHEL : How to setup session idle timeout (inactivity timeout) for ssh auto logout ](https://www.thegeekdiary.com/centos-rhel-how-to-setup-session-idle-timeout-inactivity-timeout-for-ssh-auto-logout/)  
```
There are two options related to ssh inactivity in /etc/ssh/sshd_config file:

ClientAliveInterval
ClientAliveCountMax

So the timeout value is calculated by multiplying ClientAliveInterval with ClientAliveCountMax.

timeout interval = ClientAliveInterval * ClientAliveCountMax

The meaning of the two parameters can be found in the man page of sshd_config:

There are 2 methods to configure the inactivity timeout. For example in this post we will configure an auto logout interval of 10 mins.

Method 1
1.Configure the timeout value in the /etc/ssh/sshd_config file with below parameter values.

# vi /etc/ssh/sshd_config
ClientAliveInterval 5m          # 5 minutes
ClientAliveCountMax 2           # 2 times

2. Restart the ssh service after setting the values.
# service sshd restart

This would make the session timeout in 10 minutes as the ClientAliveCountMax value is multiplied by the ClientAliveInterval value.

Method 2
1. You can set the ClientAliveCountMax value to 0 and ClientAliveInterval value to 10m to achieve the same thing.

# vi /etc/ssh/sshd_config
ClientAliveInterval 10m          # 10 minutes
ClientAliveCountMax 0            # 0 times

2. Restart the ssh service after setting the values.
# service sshd restart

***Difference between method 1 and method 2***
There’s a little difference between these two methods. For the first method, sshd will send messages, called Client Alive Messages here, through the encrypted channel to request a response from client if client is inactive for five minutes. The sshd daemon will send these messages max two times. If this threshold is reached while Client Alive Messages are being sent, sshd will disconnect the client.

But for the second method, sshd will not send client alive messages and terminate the session directly if client is inactive for 10 minutes.
```

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

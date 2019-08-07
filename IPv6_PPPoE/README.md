# Purpose
Take note of IPv6 PPPoE

# Table of Content
* [Setup Procedure](#setup-procedure)  

[sudo sysctl -w net.ipv6.conf.all.forwarding=1](#sudo-sysctl--w-netipv6confallforwarding1)  
[]()  
[]()  
[]()  
[]()  

* [Accel-ppp installation](#accel-ppp-installation)  


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

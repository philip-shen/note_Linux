# Purpose
Take note of IPv6 PPPoE

# Table of Content
[Setup Procedure]()  
[sudo sysctl -w net.ipv6.conf.all.forwarding=1]()  
[]()  
[]()  
[]()  
[]()  
[]()  
[Troubleshooting](#troubleshooting)  
[エラー解決：Mac os X で (sh: sysctl: command not found)などコマンドが見つからないエラー  20161012]()  

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

##stepup sit1  
```
ip tunnel add sit1 remote $remote_ipv4 local $local_ipv4 ttl 64 ip link set dev sit1 up
```

##add local ipv6 address in sit1  
```
ip -6 addr add $local_ipv6 dev sit1
```

## add default route to remote ipv6 address  
```
route -A inet6 add ::/0 gw $remote_ipv6 dev sit1 metric 256 
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

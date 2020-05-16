Table of Contents
=================

   * [Table of Contents](#table-of-contents)
   * [Purpose](#purpose)
   * [Local mDNS not DNS Service](#local-mdns-not-dns-service)
      * [Windows 10](#windows-10)
      * [Linux](#linux)
   * [mDNS and avahi](#mdns-and-avahi)
   * [mDNS on WSL1](#mdns-on-wsl1)
   * [mDNS solution](#mdns-solution)
   * [Troubleshooting](#troubleshooting)
   * [Reference](#reference)
   * [h1 size](#h1-size)
      * [h2 size](#h2-size)
         * [h3 size](#h3-size)
            * [h4 size](#h4-size)
               * [h5 size](#h5-size)
   * [Table of Contents](#table-of-contents-1)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)


# Purpose

# Local mDNS not DNS Service  
[mDNSを使ってローカルDNSサーバーを廃止する updated at 2019-11-22](https://qiita.com/maccadoo/items/48ace84f8aca030a12f1)  

## Windows 10  
> Resolve-DnsName hogehoge  
> Resolve-DnsName 192.168.1.10   
![alt tag](https://i.imgur.com/sbDtxws.png)  

## Linux  
```
$ apt install avahi-daemon libnss-mdns
$ dnf install avahi avahi-tools nss-mdns
```

```
$ systemctl stop ufw
$ systemctl stop firewalld.service
```

```
# nano /etc/nsswitch.conf
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

上記を以下に書き換え
hosts:          files mdns_minimal [NOTFOUND=return] dns mdns
```

```
#正引き(1)
$ avahi-resolve -n hogehoge.local
hogehoge.local  2100:a:a::1:1

$ avahi-resolve -n hogehoge.local -4
hogehoge.local  192.168.1.10
```

```
#正引き(2)
$ getent ahosts hogehoge.local
2100:a:a::1:1 STREAM hogehoge.local
2100:a:a::1:1 DGRAM  
2100:a:a::1:1 RAW 
192.168.1.10    STREAM
192.168.1.10    DGRAM  
192.168.1.10    RAW   
```

```
#逆引き
$ avahi-resolve -a 2100:a:a::1:1
2100:a:a::1:1   hogehoge.local

$ avahi-resolve -a 192.168.1.10
192.168.1.10    hogehoge.local
```


# mDNS and avahi  
[avahiとmDNS updated at 2014-08-28](https://qiita.com/jey0taka/items/ddc42d2d5de2ce9a5391)  

# mDNS on WSL1  
[WSL1 (Windows Subsystem for Linux) で mDNS な `.local` アドレスを解決する posted at 2020-01-07](https://qiita.com/ma2shita/items/422c904f39953e75a17f)  

# mDNS solution  
[名前解決サービスを自作する posted at 2019-10-31](https://qiita.com/soramimi_jp/items/9282a83664355c563c37)   

# Troubleshooting


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



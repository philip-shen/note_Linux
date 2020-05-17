Table of Contents
=================

   * [Table of Contents](#table-of-contents)
   * [Purpose](#purpose)
   * [mDNS on Ubuntu](#mdns-on-ubuntu)
      * [ubuntu での mDNS の有効化方法](#ubuntu-での-mdns-の有効化方法)
      * [mDNS を許可する](#mdns-を許可する)
      * [Hostname Setup](#hostname-setup)
      * [avahi-daemon Restart](#avahi-daemon-restart)
      * [avahi-daemon Status](#avahi-daemon-status)
   * [Local mDNS not DNS Service](#local-mdns-not-dns-service)
      * [Windows 10](#windows-10)
      * [Linux](#linux)
   * [mDNS and avahi](#mdns-and-avahi)
   * [mDNS on WSL1](#mdns-on-wsl1)
   * [DNS、mDNS、WINS、LLMNR by Socket](#dnsmdnswinsllmnr-by-socket)
      * [Serve Side](#serve-side)
         * [Linux、Mac OS X など](#linuxmac-os-x-など)
         * [Configuration Files](#configuration-files)
         * [Usage Example](#usage-example)
         * [WINS Solution on Linux](#wins-solution-on-linux)
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
Take note of mDNS on Linux  

# mDNS on Ubuntu  
[ubuntu での mDNS(=multicast DNS) の有効化方法 updated at 2019-12-31](https://qiita.com/m-tmatma/items/7668afea91aff4fbfa85)  
## ubuntu での mDNS の有効化方法  
* 最近の Windows 10 では mDNS が標準で有効になっています。  
* avahi-daemon をインストールすることにより、mDNS を利用できるようになります。  
* ubuntu 側のホスト名を hogehoge とするとLAN内に DNS がなくても hogehoge.local で名前解決できるようになります。  

```
sudo apt       install -y avahi-daemon
sudo systemctl start      avahi-daemon
sudo systemctl enable     avahi-daemon
```

## mDNS を許可する  
```
sudo apt install -y firewalld
sudo firewall-cmd --add-service=mdns  --permanent
sudo firewall-cmd --reload
```

## Hostname Setup 
[手持ちのRaspberryPiをサクッとmDNSに対応させる updated at 2018-04-19](https://qiita.com/takish/items/1a640576caa2d0dfefc4)  
```
% sudo vi /etc/hostname
```

## avahi-daemon Restart  
```
% sudo /etc/init.d/avahi-daemon restart
```

## avahi-daemon Status  
```
$ sudo /etc/init.d/avahi-daemon status
```

[ubuntu で samba で home ディレクトリを公開する updated at 2019-12-31](https://qiita.com/m-tmatma/items/8488be9b3159286505db)  


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

# DNS、mDNS、WINS、LLMNR by Socket  
[ソケットを使って、DNS、mDNS、WINS、LLMNRでホスト名のIPアドレスを問い合わせる posted at 2019-11-02](https://qiita.com/soramimi_jp/items/041eae2465f3ec985b99)  

## Serve Side  
[Bogus Name Service (Yet another name server for zeroconf)](https://github.com/soramimi/bogons)  
[Bogons - インチキネームサービス 2017-02-27](http://www.soramimi.jp/bogons/)  
### Linux、Mac OS X など  
```
 bogons/src に移動して、makeコマンドでビルドできます。bogonsを /usr/local/bin などにコピーします。DNSおよびWINSモードでは、well-knownポートにbindするため、実行する際はスーパーユーザでなければなりません。

設定ファイルは /var/bogons に置きます。
```

### Configuration Files  
```
/var/bogons/hosts

192.168.0.123 mypc mypc.local
```
```
/var/bogons/bogons.ini

masterserver=192.168.0.1
ttl=300
```

### Usage Example    
```
/etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Print the IP address
_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
fi

/usr/local/bin/bogons -w -s &

exit 0
```

### WINS Solution on Linux  
> winbind パッケージをインストール  
```
# apt-get install winbind libnss-winbind
```

> /etc/nsswitch.conf を編集
```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4 wins
```


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
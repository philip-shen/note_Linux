# Purpose
Take note of IPv6 DHCPv6

# Table of Content


[IPv6位址配發技術介紹](http://www.myhome.net.tw/2012_09/p03.htm)  
![alt tag](https://i.imgur.com/HgmemW6.jpg)

# Reference
* []()  
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

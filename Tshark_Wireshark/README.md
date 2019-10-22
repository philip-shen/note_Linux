# Purpose  
Take note of Tshark  

# Table of Contents  
[tshark wiresharkのCUI版、キャプチャ時GUI不要なので軽い。](#tshark-wireshark%E3%81%AEcui%E7%89%88%E3%82%AD%E3%83%A3%E3%83%97%E3%83%81%E3%83%A3%E6%99%82gui%E4%B8%8D%E8%A6%81%E3%81%AA%E3%81%AE%E3%81%A7%E8%BB%BD%E3%81%84)  
[[Linux] 使用 tshark 檢視 pcap 封包檔中的 HTTP 連線](#linux-%E4%BD%BF%E7%94%A8-tshark-%E6%AA%A2%E8%A6%96-pcap-%E5%B0%81%E5%8C%85%E6%AA%94%E4%B8%AD%E7%9A%84-http-%E9%80%A3%E7%B7%9A)  

# tshark wiresharkのCUI版、キャプチャ時GUI不要なので軽い。  
[tshark wiresharkのCUI版、キャプチャ時GUI不要なので軽い。](https://qiita.com/harasakih/items/71261a35506a700e151c)  
## コマンド例  
```
tshark -i2 -tad -b duration:300 -w ./test.pcap 
```

## オプション  
```
-D                       print list of interfaces and exit
-L                       print list of link-layer types of iface and exit
--list-time-stamp-types  print list of timestamp types for iface and exit

-i インタフェースID
-w 出力ファイル名(.pcap)
-b filesiez:SIZE-KB
-b duration:秒
-b files:ファイル数（ローテート）

 -t 時刻フォーマット
 -t  a|ad|d|dd|e|r|u|ud|?
  a : hh:mm:ss.nanosec   12:28:05.400184646 
  ad: a+ date            2019-03-10 12:29:15.000986266
```

## フィルタ  
```
-f “フィルタ”
  host  アドレス
  tcp 
  udp
  tcp port ポート

ブロードキャスト以外
 not broadcast and not multicast 

ARP,DNS以外
 not arp and not port 53 
```

# [Linux] 使用 tshark 檢視 pcap 封包檔中的 HTTP 連線  
[[Linux] 使用 tshark 檢視 pcap 封包檔中的 HTTP 連線 2019-08-31](https://ephrain.net/linux-%e4%bd%bf%e7%94%a8-tshark-%e6%aa%a2%e8%a6%96-pcap-%e5%b0%81%e5%8c%85%e6%aa%94%e4%b8%ad%e7%9a%84-http-%e9%80%a3%e7%b7%9a/)
```
sudo yum -y install wireshark
```

```
[testuser@localhost]$ tshark -r test.pcap  -Y http

```
```
[testuser@localhost]$ tshark -r test.pcap  -Y http -O http
```

[tshark – The Wireshark Network Analyzer 3.0.3](https://www.wireshark.org/docs/man-pages/tshark.html)  
[Inspecting HTTP headers with tshark – brokkr.net](https://brokkr.net/2018/09/02/inspecting-http-headers-with-tshark/)  


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

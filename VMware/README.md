# Purpose
Take note of Linux on VMware

# Table of Content

# VMware related stuffs  

# Install SSH Server  
```
1.安裝 OpenSSH Server 
sudo apt-get install openssh-server
或
sudo aptitude install openssh-server

2.取消 root 的登入權限
這是基於安全的考量， 一般都不會設定讓 root 可以連進來， 不然，駭客就會很方便的哩 ！ 首先，打開在 /etc/ssh/sshd_config 的 SSH 設定檔，然後，找到下面這一行，把它的 yes 改成 no 之後，就把它存檔起來。

＃PermitRootLogin Yes
或是
PermitRootLogin No

3.設定可以連線的主機

打開 /etc/hosts.allow 檔，把允許的主機 IP 加進來， 以阿舍想要讓 192.168.1.88 這台機器可以連進來為例，就輸入下面這樣的一行,然後就存檔起來。
sshd:192.168.1.88:allow

再來， 再打開 /etc/hosts.deny 檔，把下面這一行給加進去，這樣其它的主機都會被設為拒絕連線，所以，這台主機就只有上面設定的 192.168.1.88 那一台可以連進來了哩。
sshd:all:deny

4.重啟 SSH Server
用下面的指令來重啟 SSH Server 之後，就算安裝設定完成了哩 !
sudo /etc/init.d/ssh restart
```

# Reference
* [VMware Workstation 12 Player安裝Ubuntu 15.04 (一) 20150909](https://blog.xuite.net/yh96301/blog/341981056-VMware+Workstation+12+Player%E5%AE%89%E8%A3%9DUbuntu+15.04+%28%E4%B8%80%29)  
* [VMware Workstation 12 Player安裝Ubuntu 15.04 (二) 20150910](https://blog.xuite.net/yh96301/blog/341981594)  
* [ Ubuntu 安裝與設定 ssh server 6月 26, 2012 ](https://www.ewdna.com/2012/06/ubuntu-ssh-server.html)  
* [Ubuntu 安裝和啟用 SSH 登入 2010-08-22 ](https://www.arthurtoday.com/2010/08/ubuntu-ssh.html)  
* [Ubuntu 用 SSH + 憑證登入遠端主機  2009-11-01](https://www.arthurtoday.com/2009/11/ssh-linux-client.html)  
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

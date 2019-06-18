# Purpose
Take note of Ubuntu stuffs

# Table of Content

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

# VMware Workstation 12.x + ubuntu 16.04 + NAT 不 work   
[VMware Workstation 12.x + ubuntu 16.04 + NAT 不 work 九月 8, 2017](https://andersonwang.wordpress.com/2017/09/08/vmware-workstation-12-x-ubuntu-16-04-nat-%E4%B8%8D-work/)  

# 
[]()  
#  
[]()  

# Reference
* []()  
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

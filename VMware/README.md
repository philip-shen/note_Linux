# Purpose
Take note of Linux on VMware

# Table of Content
[Install SSH Server](#install-ssh-server)  
[How to connect wireless network adapter to VMWare workstation?](#how-to-connect-wireless-network-adapter-to-vmware-workstation)  

[Configure networks](#configure-networks)  
[Add a virtual network adapter](#add-a-virtual-network-adapter)  
[Configure bridged networking](#configure-bridged-networking)  
[Configure NAT networking](#configure-nat-networking)  
[Configure host-only networking](https://github.com/philip-shen/note_Linux/tree/master/VMware#configure-host-only-networking)  
[]()  


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
# Configure networks
## Add a virtual network adapter  
* [Add a virtual network adapter ](https://geek-university.com/vmware-player/add-a-virtual-network-adapter/)  
- Bridged: Connected directly to the physical network – a virtual machine is connected to the network by using the network adapter on the host system. This networking configuration is often the easiest way to give your virtual machine access to the network.  
- NAT: Used to share the host’s IP address – a virtual machine does not have its own IP address on the external network. Instead, a separate private network is set up on the host system and a virtual machine gets an IP address on this private network from the virtual DHCP server. The virtual machine and the host system share a single network identity that is not visible on the external network. When the virtual machine sends a request to access a network resource, it appears to the network resource as if the request is coming from the host system.  
- Host-only: A private network shared with the host – a network that is completely contained within the host computer is created. This networking configuration provides a network connection between the virtual machine and the host system by using a virtual network adapter that is visible on the host operating system.  
![alt tag](https://geek-university.com/wp-content/images/vmware-player/network_adapter_type.jpg?x66712)

## Configure bridged networking  
* [Configure bridged networking ](https://geek-university.com/vmware-player/configure-bridged-networking/)  
If you use the virtual machine on a laptop, check the Replicate physical network connection state checkbox. This option causes the IP address to be renewed when you move from one wired or wireless network to another.  
![alt tag](https://geek-university.com/wp-content/images/vmware-player/bridged_networking_configuration.jpg?x66712)

## Configure NAT networking  
* [Configure NAT networking ](https://geek-university.com/vmware-player/configure-nat-networking/)  

In NAT (Network Address Translation) networking, a virtual machine does not have its own IP address on the external network. Instead, a separate private network is set up on the host system and a virtual machine gets its IP address on this private network from the virtual DHCP server. The virtual machine and the host system share a single network identity that is not visible on the external network. When the virtual machine sends a request to access a network resource, it appears to the network resource as if the request is coming from the host system.  
A NAT network (VMnet8) is set up for you when you install VMware Player. The host system has a virtual network adapter on the NAT network that enables the host system and virtual machines to communicate. The NAT device passes network data between virtual machines and the external network, identifies incoming data packets intended for each virtual machine, and sends them to the appropriate destination.  

![alt tag](https://geek-university.com/wp-content/images/vmware-player/nat_configuration.jpg?x66712)

## Configure host-only networking  
* [Configure host-only networking ](https://geek-university.com/vmware-player/configure-host-only-networking/)  

In host-only networking, a network completely contained within the host computer is created. This networking configuration provides a network connection between the virtual machine and the host system by using a virtual network adapter that is visible on the host operating system. The virtual DHCP server provides IP addresses on the host-only network.  
A host-only network (VMnet1) is set up for you when you install VMware Player. In the default configuration, a virtual machine is isolated and cannot connect to the Internet.  

![alt tag](https://geek-university.com/wp-content/images/vmware-player/host_only_networking_configuration.jpg?x66712)

# Ethernet device not managed 

# How to connect wireless network adapter to VMWare workstation?  
* [How to connect wireless network adapter to VMWare workstation? Nov 13, 2011](https://stackoverflow.com/questions/4601762/how-to-connect-wireless-network-adapter-to-vmware-workstation) 

Workstation doesn't have a wireless NIC type, so direct wireless hardware access is out. If you just want to access through the extant host wireless connection, bridging is your answer.

I think the only way to get a wireless NIC dedicated to the VM would be using a USB wireless NIC as a USB-passthrough device on the VM. When you have Workstation running and a USB device plugged in, it should give you an option to change whether that device is connected to the host or to the VM.

# 

# Reference
* [VMware Workstation 12 Player安裝Ubuntu 15.04 (一) 20150909](https://blog.xuite.net/yh96301/blog/341981056-VMware+Workstation+12+Player%E5%AE%89%E8%A3%9DUbuntu+15.04+%28%E4%B8%80%29)  
* [VMware Workstation 12 Player安裝Ubuntu 15.04 (二) 20150910](https://blog.xuite.net/yh96301/blog/341981594)  
* [ Ubuntu 安裝與設定 ssh server 6月 26, 2012 ](https://www.ewdna.com/2012/06/ubuntu-ssh-server.html)  
* [Ubuntu 安裝和啟用 SSH 登入 2010-08-22 ](https://www.arthurtoday.com/2010/08/ubuntu-ssh.html)  
* [Ubuntu 用 SSH + 憑證登入遠端主機  2009-11-01](https://www.arthurtoday.com/2009/11/ssh-linux-client.html)  
* [Ethernet device not managed ](https://askubuntu.com/questions/882806/ethernet-device-not-managed)  
* [Error editing connection Unable to find a connection with UUID ('null') Feb 16, 2017](https://askubuntu.com/questions/688556/error-editing-connection-unable-to-find-a-connection-with-uuid-null)  

* [VMwareのIPv6 NATを使ってみたら、IPv4 onlyホストにつながらなくなる(from Windows 10 VM) 2016-12-19](https://qiita.com/ip6/items/af4677e9afe9661b521d)  

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

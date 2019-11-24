# Purpose
Take note of WSL from VSCode.

# Table of Contents  
[Managing VMs stuck in the ‘Starting’ or ‘Stopping’ state in Hyper-V](#managing-vms-stuck-in-the-starting-or-stopping-state-in-hyper-v)  
[Fixing a Virtual Machine that's Stuck in a Saved State](#fixing-a-virtual-machine-thats-stuck-in-a-saved-state)  

[Shared Folders over Hyper-V Ubuntu Guest](#shared-folders-over-hyper-v-ubuntu-guest)  
[Setup NAT and Port Mapping at Hyper-V](#setup-nat-and-port-mapping-at-hyper-v)
[Linux GUI on WSL](#linux-gui-on-wsl)  
[How to mount USB disk on WSL](#how-to-mount-usb-disk-on-wsl)  
[Windows 10 - Bash (Ubuntu) SU (Root Password)](#windows-10---bash-ubuntu-su-root-password)  
[Reset Password for WSL Linux Distro in Windows 10](#reset-password-for-wsl-linux-distro-in-windows-10)  
[How can I install Python on Bash on Ubuntu on Windows?](#how-can-i-install-python-on-bash-on-ubuntu-on-windows?)  

[]

[Reference](#reference)

# Managing VMs stuck in the ‘Starting’ or ‘Stopping’ state in Hyper-V  
[Managing VMs stuck in the ‘Starting’ or ‘Stopping’ state in Hyper-V Apr 10, 2015](http://www.techkb.onl/managing-vms-stuck-in-the-starting-or-stopping-state-in-hyper-v/)  

Every now and then, Hyper-V virtual machines for various reasons decide that they don’t want to start or stop correctly and get stuck in the ‘Starting’ or ‘Stopping’ state.  
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm00.png)  

One way its possible to kill off that stuck virtual machine is to open Task Manger and 
end the task responsible for that machine. 
Unfortunately its not quite that simple because the Virtual Machine Worker Process 
which is responsible for running the virtual machine appears numerous times, 
once for each running guest machine!  

## 1. First we need to open Task Manger and view the process tab  
## 2. Then right click on the column titles and add in the Command Line column  
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm01-300x273.png)  

## 3. Expand the Command Line column to view the full command, including the machine GUIDs at the end of each line  
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm02.png)  

## 4. we can find the machine configuration file and make note of the GUID for that machine  
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm03-300x113.png)  

## 5. Now we know which GUID.  Jump back to Task Manger, right click on the correct process and End Process  
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm05-300x67.png)  

## Another way to locate the GUID of the machines running on the server is to use PowerShell to output it  
```
Get-VM | Select Name, Id
```
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm04-300x76.png)  

```
Get-WmiObject Win32_Process -Filter "Name like '%vmwp%'" | %{$vm=get-vm -id $_.CommandLine.split(" ")[1];"$($_.processID)`t$($vm.name)"}
```
![alt tag](http://www.techkb.onl/wp-content/uploads/2015/04/svm09-300x48.png)  



# Fixing a Virtual Machine that's Stuck in a Saved State  
[Fixing a Virtual Machine that's Stuck in a Saved State 06/28/2018](https://redmondmag.com/articles/2018/06/28/fixing-vm-stuck-in-saved.aspx)

## 1. Status Check   
![alt tag](https://i.imgur.com/snAo4Xk.jpg)  

## 2. Reduce Each CheckPoint   
![alt tag](https://i.imgur.com/vAuMLzp.jpg)  
![alt tag](https://i.imgur.com/WnEALC6.jpg)   
![alt tag](https://i.imgur.com/rUYEnpr.jpg)  
![alt tag](https://i.imgur.com/KeCCjSE.jpg)  

## 3. Restart WSL  
![alt tag](https://i.imgur.com/5BOdkFh.jpg)  



# Shared Folders over Hyper-V Ubuntu Guest  
[Shared Folders over Hyper-V Ubuntu Guest](https://linuxhint.com/shared_folders_hypver-v_ubuntu_guest/)  
```
Setting up shared folders in Hyper-V is not a conventional thing to do. 
Unlike VirtualBox, Hyper-V is not a desktop exclusive hypervisor. 
It is meant to run on servers and manage entire data centers. 
Features like Shared Folders are not of any particular concern in such scenarios.
That said, we can still manage to share folders between guest OS running on Hyper-V 
and the host operating system in a way which is secure, well-tested and stable. 
We will use SMB file share to share a folder created on host machine with the guest. 
It is similar to sharing a folder between two regular computers. 
Since Hyper-V runs on Windows so we would have to get a little Windows 
specific while creating the file share.
```
## Starting a file share  
![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s.png)  

![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s1.png) 

```
Once that is done, let’s create a Folder in which we will keep our shareable contents. 
We will name ours MySharedFolder. Right-click on this new folder, 
go to Properties → Sharing and Click on Share.
```
![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s2.png)  

![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s3.png)  
![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s4.png)  
```
As you can see the path is \\ANGMAR\MySharedFolder in this case. 
Usually, it will follow the same  \\PCName\Shared_Folder_Name format. 
Backslashes are used to separate different directories while prescribing paths in Windows. 
On our Linux guest we will replace the backslashes to forward one 
like so  //PCName/Shared_Folder_Name
```

## Guest to Host Networking  
![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s5.png)  

![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s6.png)  

## Mounting the Shared Folder on Guest  
```
$ sudo apt install cifs-utils
```

```
$ mkdir ~/SharedFolder
```

```
Okay, so now as the final step, you need to mount the folder. Remember that when we created the file share in our host we got a network path for the folder which was \\ANGMAR\MySharedFolder while yours may differ, the one thing that would remain the same is the backslashes used by Windows which you need to turn into forward slashes while specifying on Linux.

Also since we shared it with only one Windows user (yourself) you need to tell Linux what your Windows user name is so it can authenticate against that name.
```

```
$ sudo mount.cifs //<NAME OF YOUR PC>/<SHARED FOLDER NAME>
~/SharedFolder -o user=<YOUR WINDOWS USERNAME>
```

![alt tag](https://linuxhint.com/wp-content/uploads/2018/06/s7.png)  

```
$ sudo mount.cifs //ANGMAR/MySharedFolder ~/SharedFolder -o user=WindowsUserName
```

```
You will be prompted for sudo password (if you are not running as root), 
in which case enter the password for your Linux user and 
you will be prompted for the password to access the remote folder, 
in which case, enter the Windows user’s password.
```

[[筆記] 解決Windows 10 1709分享資料夾，Linux無法連線的問題 Jan 31, 2018](https://eric0806.blogspot.com/2018/01/windows-10-samba-linux.html)
```
    Get-SmbServerConfiguration
```
![alt tag](https://3.bp.blogspot.com/-OmtlCdpKH9Y/WnF3mzPumAI/AAAAAAABEWM/85r6EqnnRLUhPO2JbT9ckFtbW4cKsQ2FACLcBGAs/s1600/2018-01-31_155916.png)  
```
紅框的地方，SMBv1沒有打開，只有開啟SMBv2與SMBv3 (根據微軟的說明，SMBv2若開啟，v3也會一同開啟，反之如果是關閉亦同)，
也許事務機並沒有支援到v2以上，所以如果我們把v1打開，並關閉v2、v3就好囉??
```

```
利用底下指令來打開SMBv11並關閉v2：

    Set-SmbServerConfiguration -EnableSMB1Protocol $True
    Set-SmbServerConfiguration -EnableSMB2Protocol $False

結果在第一行就卡關了...
```
![alt tag](https://3.bp.blogspot.com/-mR_9bIlm6eE/WnF4pncCWbI/AAAAAAABEWY/x0_3Z8oDiNcGeJMlIJeVhnEhVm9I3YGBwCLcBGAs/s640/2018-01-31_160441.png)  

```
原來是SMB1的支援沒裝啊~~XD
進到控制台->程式與功能->打開或關閉Windows功能內，找到 SMB 1.0/CIFS檔案共用支援，點開後把三個勾都勾起來，
安裝好後會需要重新開機，重開好，再執行一次上面的指令，就可以囉！！
```
![alt tag](https://2.bp.blogspot.com/-5nOGDNiCIXo/WnF5nPyecuI/AAAAAAABEWk/Ycx8P0tl7EgA67GwNXUUKNFoDtd3MKLigCLcBGAs/s1600/2018-01-31_155727.png)  

# Setup NAT and Port Mapping at Hyper-V  
[Hyper-V 建立 NAT 及 Port Mapping Jun 20, 2019](http://longfamily.pixnet.net/blog/post/119258120-hyper-v-%E5%BB%BA%E7%AB%8B-nat-%E5%8F%8A-port-mapping)  
```
在Hyper-V環境中沒有內建NAT的功能，對於沒有多IP可以使用的環境若虛擬機器需要連上網路可能無法實現，
當然虛擬機器若不需要連接網際網路那就比較沒有影響，如果一定要連上網路那就比較麻煩了，
所以此時可以使用[網際網路連線共用 (ICS)]來建立NAT解決此問題，
本文將使用windows 8.1 hyper-V來設定NAT並且示範啟用NAT後如何設定發佈一台Web Server，
當然此方法也適用於Windows Server 2012 (R2) Hyper-V。
```

# Linux GUI on WSL  
* [GitHub - QMonkey/wsl-tutorial: A tutorial about how to run desktop ... ](https://github.com/QMonkey/wsl-tutorial)  
* [Using a GUI with WSL on Windows 10 (Ubuntu wsl) Apr 20, 2018](https://www.reddit.com/r/Windows10/comments/8dnyig/using_a_gui_with_wsl_on_windows_10_ubuntu_wsl/)  
* [Run Linux GUI apps on Windows 10 Oct 23, 2018](https://dev.to/david_j_eddy/run-linux-gui-applications-on-windows-10-3130)  
* [Setting up Ubuntu (WSL) for Linux GUI Apps - Choung Networks](https://token2shell.com/howto/x410/customizing-xfce-desktop-for-ubuntu-wsl/)  
* [Customizing Xfce Desktop for Ubuntu (WSL) - Choung Networks](https://token2shell.com/howto/x410/customizing-xfce-desktop-for-ubuntu-wsl/)  

# How to mount USB disk on WSL
[wsl上でbashコマンドでUSBドライブをマウントしアクセスする方法 2018-11-12](https://qiita.com/pokobur/items/3d9214fe1810d5d63044)  
```
sudo mkdir /mnt/d
sudo mount -t drvfs D: /mnt/d
```
-  /mnt配下にｄディレクトリを作成するよ。
-  マウントコマンドでファイルシステムのタイプを指定するよ。drvfs
-  マウントしたいドライブを指定するよ。 D:
-  あらかじめ作成したディレクトの場所を指定するよ。　/mnt/d

# Windows 10 - Bash (Ubuntu) SU (Root Password)  
[Windows 10 - Bash (Ubuntu) SU (Root Password) Jun 3, 2016](https://stackoverflow.com/questions/37609356/windows-10-bash-ubuntu-su-root-password)  
```
as far as i know you'll have to type "sudo su"
```
# Reset Password for WSL Linux Distro in Windows 10
[Reset Password for WSL Linux Distro in Windows 10](https://winaero.com/blog/reset-password-wsl-linux-distro-windows-10/)  
## Change the default user name for your WSL distro to root. Use the following command: ubuntu config --default-user root. For other distros, see Note below.
![alt tag](https://winaero.com/blog/wp-content/uploads/2019/02/Windows-10-WSL-set-default-password-to-root.png)  
## Launch your Linux distribution, e.g. type ubuntu, or wsl if you are working with your default WSL distro.  
![alt tag](https://winaero.com/blog/wp-content/uploads/2019/02/Windows-10-WSL-run-distro-as-root.png)  
## Reset your password using the passwd command: passwd <username>. Substitute the <username> portion with the actual user name you want to reset the password for, e.g. #passwd winaero.  
![alt tag](https://winaero.com/blog/wp-content/uploads/2019/02/Windows-10-WSL-reset-user-password.png)  
## Leave your WSL session and set the default user of the WSL distro back to your user account, e.g. ubuntu config --default-user winaero.  
![alt tag](https://winaero.com/blog/wp-content/uploads/2019/02/Windows-10-WSL-restore-default-user-account.png)   Note: Use the following commands to change your default user to root in a WSL distro. By replacing 'root' with another user account name, you'll set it as your default user account for the distro.

# How can I install Python on Bash on Ubuntu on Windows?  
[How can I install Python on Bash on Ubuntu on Windows? ](https://www.quora.com/How-can-I-install-Python-on-Bash-on-Ubuntu-on-Windows)  
```
sudo apt-get install python
```
which should install Python 2.7.  
Alternately, you could run  
```
sudo apt-get install python3
```
which should install Python 3.5.  

# WSL2  
[WSL2の環境構築手順 Aug 17, 2019](https://qiita.com/poramal/items/3562472d52fe60f61c56)
[WSL2を使ってみる (InsiderPreview)  Jun 15, 2019](https://qiita.com/namoshika/items/53a9ac2df7eace656870)  

[wsl2でsshサーバを起動し、外部からそこに接続  Jul 03, 2019](https://qiita.com/yabeenico/items/15532c703974dc40a7f5)  

やりたいこと  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F101023%2F008d92b2-0e78-cb20-0089-36b35baf0a5e.png?ixlib=rb-1.2.2&auto=compress%2Cformat&gif-q=60&w=1400&fit=max&s=fa09e7ed82228d8b4e6aec58cd881f90)  

wsl1ではWindowsとLinuxが同じネットワークインターフェースを参照していました。  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F101023%2F0d284fc0-bdb0-9cf4-c284-7f433c601136.png?ixlib=rb-1.2.2&auto=compress%2Cformat&gif-q=60&w=1400&fit=max&s=722472b9dd349572894b9ff22b0bd42b)  

wsl2の場合、LinuxはWindowsと仮想ネットワークで接続された別ホストとして扱われます。  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F101023%2F0a886cb7-32e0-6c51-c9ad-a71db1f6aad8.png?ixlib=rb-1.2.2&auto=compress%2Cformat&gif-q=60&w=1400&fit=max&s=1faea3623a80009547dcaa4596ac4170)  

[WSL2がWindowsからlocalhostで接続できるようになる Jul 29, 2019](https://qiita.com/SoraKumo/items/c91b0fd7d434be8f8919)  

[localhostの検証](https://qiita.com/SoraKumo/items/c91b0fd7d434be8f8919#localhost%E3%81%AE%E6%A4%9C%E8%A8%BC)  
```
    WindowsのWSL2仮想NICを無効化してみた結果

    WindowsからLinuxへのlocalhost接続は生きたままです。
    しかしLinuxから外部ネットワークへの接続は不可能になります。

    LinuxからWindowsへのlocalhost接続

    出来ません。現時点ではWindowsがlocalhostに対して、LinuxへのNATのような動作をしていると思われます。
    そのため逆は出来ません。
    今後のバージョンで対応される可能性があります。
```

[WSL2を使うときに便利なbat](https://qiita.com/SoraKumo/items/c91b0fd7d434be8f8919#wsl2%E3%82%92%E4%BD%BF%E3%81%86%E3%81%A8%E3%81%8D%E3%81%AB%E4%BE%BF%E5%88%A9%E3%81%AAbat)  
```
全然話は変わりますがWSLの再起動ごとに、sshやWebサーバの起動が面倒だという人のためのおすすめbatファイルがこれです。
```

```
wsl_start.bat

start /b wsl -u root ^
for file in `\find /etc/rc3.d/* -maxdepth 1`; do $file start; done 
```

[]()  

[WSL + Docker + Jenkins + Proxyの地雷を解決する Nov 18, 2019](https://qiita.com/dongsu-iis/items/3a44a38a48b9a1533628)  

[WSL2 で Docker Desktop for Windows (Edge) を利用する Nov 05, 2019](https://qiita.com/SakaiYuki/items/e5ab0061ff3273c0e80f)  

# Reference  
* [4 Ways to Transfer Files to a Linux Hyper-V Guest Jun 6, 2017](https://www.altaro.com/hyper-v/transfer-files-linux-hyper-v-guest/)  
```
Method 1) Use PowerShell and Integration Services
Method 2) Using WinSCP
Method 3) Move Files to/from Linux with the Windows FTP Client
Method 4) Move Files Between Linux Guests with a Transfer VHDX
```


* [Windows Bash won't open in 10 Anniversary Update](https://superuser.com/questions/1112429/windows-bash-wont-open-in-10-anniversary-update)
>Prerequisites
Actually, you just need Bash on Ubuntu on Windows enabled and, of course Cmder. If you don’t have that, you can simply follow these instructions:
Install Bash On Ubuntu on Windows
Download and unzip Cmder to a convenient place on your disk. Then start Cmder.exe.

* [How to Install and Use the Linux Bash Shell on Windows 10](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/)

* [Installing Ubuntu on Windows 10 Without Using the Windows Store](https://www.dennisnguyen.net/2018/08/15/installing-ubuntu-on-windows-10-without-using-the-windows-store/)
* [Manually download Windows Subsystem for Linux distro packages](https://docs.microsoft.com/en-us/windows/wsl/install-manual)
```
Download using curl

curl.exe -L -o ubuntu-1604.appx https://aka.ms/wsl-ubuntu-1604
```

* [Windows Subsystem for Linux: Error 0x80070005 (Access Denied) October 11, 2017](https://adrift.io/2017/10/11/windows-subsystem-for-linux-error-0x80070005-access-denied/)
>That’s not cool though, we want to reach these things remotely and invoke things in an automation-friendly way. As it turns out, there are a couple of things preventing you from achieving this. Primarily:
Local launch and activation permissions on the Linux Subsystem / LXSS (as it’s referenced internally) DCOM configuration object.
Registry permissions which prevent you from modifying the above.
* [Can't install apps from Store, error 0x80070005 3/30/2018](https://answers.microsoft.com/en-us/windows/forum/windows_8-windows_store/cant-install-apps-from-store-error-0x80070005/1da61861-26ee-41b4-ada9-8ac516b0107a?page=3)
* [Reset root user password on WSL Sep 10, 2017](https://medium.com/@elvis.pestana/reset-root-user-password-on-wsl-aa3ecf82fbd6)  
```
lxrun /setdefaultuser root

passwd default_username

lxrun /setdefaultuser default_username
```


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

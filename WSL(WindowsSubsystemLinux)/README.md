# Purpose
Take note of WSL and WSL2.

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


[03. WSL2 Installation on Win 10](#03-wsl2-installation-on-Win-10)  
[1. Afert Windows 10 Build 18917](#1-afert-windows-10-build-18917)  
[2. Windows Insider Program Installation](#2-windows-insider-program-installation)  
[3. WSL2 Installation](#3-wsl2-installation)  
[01. Both Machine Platform and WSL Availability](#01-both-machine-platform-and-wsl-availability)  
[02. Linux Distribution Selection](#02-linux-distribution-selection)  
[03. Distribution Version Changes to WSL2](#03-distribution-version-changes-to-wsl2)  
[04. WSL2 Sets to Defalut Version](#04-wsl2-sets-to-defalut-version)  
[05. WSL Version Confirmation](#05-wsl-version-confirmation)  
[4. Docker Installation and Launch](#4-docker-installation-and-launch)  
[5. Docker Desktop v2.2.1.0 Installation](#5-docker-desktop-v2210-installation)  
[6. Excute VS Code on WSL](#6-excute-vs-code-on-wsl)  
[7. WSL and Windows](#7-wsl-and-windows)  


[04. WSL2](#04-wsl2)  
[WSL2がWindowsからlocalhostで接続できるようになる](#wsl2%E3%81%8Cwindows%E3%81%8B%E3%82%89localhost%E3%81%A7%E6%8E%A5%E7%B6%9A%E3%81%A7%E3%81%8D%E3%82%8B%E3%82%88%E3%81%86%E3%81%AB%E3%81%AA%E3%82%8B)  
[WSL2のコロコロ変わるIPをMyDNSで何とかする](#wsl2%E3%81%AE%E3%82%B3%E3%83%AD%E3%82%B3%E3%83%AD%E5%A4%89%E3%82%8F%E3%82%8Bip%E3%82%92mydns%E3%81%A7%E4%BD%95%E3%81%A8%E3%81%8B%E3%81%99%E3%82%8B)  

[05. WSL2 vs Hpyer-V](#05-wsl2-vs-hpyer-v)  
[Illustration](#illustration)  



[06. CredSSP authentication is currently disabled on the local client](#06-credssp-authentication-is-currently-disabled-on-the-local-client)  


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


# 03. WSL2 Installation on Win 10  
[やさしいWSL2のインストール手順とエラー Apr 12, 2020](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec)  

## 1. Afert Windows 10 Build 18917  
[1. Windows 10 ビルド 18917 以降であること](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#1-windows-10-%E3%83%93%E3%83%AB%E3%83%89-18917-%E4%BB%A5%E9%99%8D%E3%81%A7%E3%81%82%E3%82%8B%E3%81%93%E3%81%A8)  
```
コマンドプロンプトから確認

    コマンドプロンプトを開く
    varコマンドを実行
    出てきたバージョンが18917以上ならOK！
```
[最新のWindows 10 November 2019 Updateを手動でインストールする ](https://www.atmarkit.co.jp/ait/articles/1704/10/news023.html)  
[Windows 10 20H1 版 5 月重大更新將導入 “自動更新驅動程式” 的新功能 Feb 25, 2020](https://www.kocpc.com.tw/archives/308300)  
[Windows 10 20H1 (Vibranium) 公眾預覽版本Build 18912 ... Nov 20, 2019](https://isite.tw/2019/11/20/20297)  
[Win10 20h1 下載](http://rile39ri.duckdns.org/page51) 

```
Select Fast then download Build 19608 then Upgrade it.
```
![alt tag](https://i.imgur.com/KvoE8MT.jpg)  
![alt tag](https://i.imgur.com/1ZTKUjW.jpg)  

*Update to WSL2 Environment then Hyper-V will disappear.*

![alt tag](https://i.imgur.com/FUWKePH.jpg)  

## 2. Windows Insider Program Installation  
[2. Windows Insider Programに入っていること](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#2-windows-insider-program%E3%81%AB%E5%85%A5%E3%81%A3%E3%81%A6%E3%81%84%E3%82%8B%E3%81%93%E3%81%A8)  
```
このページを訪れる人はほとんど入っていなと考えられます
以下の手順を行ってください

    Windowsの設定⇒更新とセキュリティ⇒Windows Insider Programを開く
    開始する（Get start）をクリック
    出てくる文章に同意し、Windowsアカウントを紐づける
    Insiderの設定でスロー（推奨）をクリック
    再起動をクリック
```

## 3. WSL2 Installation  
[WSL2の導入](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#wsl2%E3%81%AE%E5%B0%8E%E5%85%A5)  

### 01. Both Machine Platform and WSL Availability  
[手順1. 仮想マシンプラットフォームとWSL が有効であることを確認](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#%E6%89%8B%E9%A0%861-%E4%BB%AE%E6%83%B3%E3%83%9E%E3%82%B7%E3%83%B3%E3%83%97%E3%83%A9%E3%83%83%E3%83%88%E3%83%95%E3%82%A9%E3%83%BC%E3%83%A0%E3%81%A8wsl-%E3%81%8C%E6%9C%89%E5%8A%B9%E3%81%A7%E3%81%82%E3%82%8B%E3%81%93%E3%81%A8%E3%82%92%E7%A2%BA%E8%AA%8D)  
```
Powershell

dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### 02. Linux Distribution Selection  
[手順2. ディストリビューションのインストール](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#%E6%89%8B%E9%A0%862-%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)  
[2. ディストリビューションのインストール](https://qiita.com/kekenonono/items/1ddbb5a1125d496c0010#2-%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)  

### 03. Distribution Version Changes to WSL2  
[手順3. ディストリビューションのバージョンをWSL2に変更する](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#%E6%89%8B%E9%A0%863-%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3%E3%82%92wsl2%E3%81%AB%E5%A4%89%E6%9B%B4%E3%81%99%E3%82%8B)  

```
私の場合

> wsl -l
Linux 用 Windows サブシステム ディストリビューション:
Ubuntu (既定) # ここにディストリビューションの名前が表示される
```

```
私の場合

> wsl --set-version Ubuntu 2
変換中です。この処理には数分かかることがあります...
変換が完了しました。
```

*カーネルコンポーネントの更新が必要*
```
 カーネルコンポーネントの更新が必要

> wsl --set-version Ubuntu 2
変換中です。この処理には数分かかることがあります...
WSL 2 を実行するには、カーネル コンポーネントの更新が必要です。詳細については https://aka.ms/wsl2kernel を参照してください
```
[https://aka.ms/wsl2kernel](https://docs.microsoft.com/ja-jp/windows/wsl/wsl2-kernel)  

![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F521871%2F628e8a04-e895-f550-c5aa-5c859d2e7785.png?ixlib=rb-1.2.2&auto=format&gif-q=60&q=75&w=1400&fit=max&s=ce5031dfb071261a4478e4054ff9e3a1)  

#### wsl_update_x64.msi Installation Error Troublshooting   
[wsl_update_x64.msi実行時のエラー](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#wsl_update_x64msi%E5%AE%9F%E8%A1%8C%E6%99%82%E3%81%AE%E3%82%A8%E3%83%A9%E3%83%BC)  

[WSL 2 requires an update / The update only applies to machines with WSL #5014](https://github.com/microsoft/WSL/issues/5014)  

```
Also it seems some people have problems with the installer extracting the kernel.
You can always extract it manually with:
msiexec /a "wsl_update_x64.msi" /qb TARGETDIR="C:\temp"
and then copy the kernel file from C:\temp to C:\Windows\System32\lxss\tools
```

* 1 Copy wsl_update_x64.msi  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F521871%2Faf38e9df-cc39-c6e4-dd01-0121c78883c7.png?ixlib=rb-1.2.2&auto=format&gif-q=60&q=75&s=0f3283bf5f7b5e0bbb1b7b82ee7f12a1)  

* 2 Past to C:\Windows\System32\lxss\tools   
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F521871%2Fbe1751c6-8387-aff7-d13f-1a8d589c9c9b.png?ixlib=rb-1.2.2&auto=format&gif-q=60&q=75&w=1400&fit=max&s=37840f50a1aaf326f272db701ffffb4d)  

* 3 Excute wsl_update_x64.msi  

* 4 Finish  

### 04. WSL2 Sets to Defalut Version  
[手順4. WSL 2 を既定のアーキテクチャにする](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#%E6%89%8B%E9%A0%864-wsl-2-%E3%82%92%E6%97%A2%E5%AE%9A%E3%81%AE%E3%82%A2%E3%83%BC%E3%82%AD%E3%83%86%E3%82%AF%E3%83%81%E3%83%A3%E3%81%AB%E3%81%99%E3%82%8B)  
```
wsl --set-default-version 2
```

### 05. WSL Version Confirmation  
[手順5. WSL のバージョンを確認して終了](https://qiita.com/kekenonono/items/14b725ce3d00cd5281ec#%E6%89%8B%E9%A0%865-wsl-%E3%81%AE%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3%E3%82%92%E7%A2%BA%E8%AA%8D%E3%81%97%E3%81%A6%E7%B5%82%E4%BA%86)   
```
私の場合

> wsl -l -v
  NAME      STATE           VERSION
* Ubuntu    Stopped         2
```

### 05. WSL Version Backward to 1     
手順3. と手順4. を2から1に変えて行うだけで変更できます  
```
> wsl --set-version <Distro> 2 # <Distro>はディストリビューションの名前
> wsl --set-default-version 2
```
![alt tag](https://i.imgur.com/JvDzFsk.jpg)  

## 4. Docker Installation and Launch  
[在Windows 10 環境上安裝WSL 2 - Huan-Lin 學習筆記 Feb 27, 2020](https://www.huanlintalk.com/2020/02/wsl-2-installation.html)  
```
sudo apt update
sudo apt upgrade
sudo apt install docker.io
sudo service docker start
```

## 5. Docker Desktop v2.2.1.0 Installation  
![alt tag](https://1.bp.blogspot.com/-_h4sUbADcOM/XlqbqbUoq6I/AAAAAAAApzo/woEGP-rM7VUP8ysIDZBzb0KovUb951JQACNcBGAsYHQ/s1600/2020-03-01_01-02-14.png)  

![alt tag](https://i.imgur.com/y5NtwEj.jpg)  

![alt tag](https://i.imgur.com/gb0UY6H.png)

[WSL2入れてみた Mar 15, 2020](https://qiita.com/TsuyoshiUshio@github/items/947301bd9317610572fc)  

[Docker Desktop for WSL 2 を入れてみました  Aug 02, 2019](https://qiita.com/SHIRANO/items/42616bb76630df068f33)  
[5 Things to Try with Docker Desktop WSL 2 Tech Preview Jul 31 2019](https://www.docker.com/blog/5-things-docker-desktop-wsl2-tech-preview/)  
1. Navigate between WSL 2 and traditional Docker  
```
Use $ docker context ls  to view the different contexts available.

The daemon running in WSL 2 runs side-by-side with the “classic” Docker Desktop daemon. 
This is done by using a separate Docker Context. 
Run `docker context use wsl` to use the WSL 2 based daemon, 
and `docker context use default` to use the Docker Desktop classic daemon. 
The “default” context will target either the Moby Linux VM daemon or 
the Windows Docker daemon depending if you are in Linux or Windows mode. 
```

2. Access full system resources  
```
Use $ docker info to inspect the system statistics. 
You should see all of your system resources (CPU & memory) available to you in the WSL 2 context. 
```

3. Linux workspaces  
```
Source code and build scripts can live inside WSL 2 and access the same Docker Daemon as from Windows. 
Bind mounting files from WSL 2 is supported, and provides better I/O performance.
```

4. Visual Studio remote with WSL  
```
You can work natively with Docker and Linux from Visual Studio Code on Windows. 

If you are a Visual Studio Code user make sure you have installed the plugin from the marketplace. 
ou can then connect to WSL 2 and access your source in Linux, 
which means you can use the console in VSCode to build your containers using 
any existing Linux build scripts from within the Windows UI.

For full instructions have a look through Microsoft’s documentation: 
https://code.visualstudio.com/docs/remote/wsl
```

5. File system improvements:   
```
If you are a PHP Symfony user let us know your thoughts! 
We found that page refreshes went from ~400ms to ~15ms when we were running from a Linux Workspace.
```


[WSL2でDockerが動かない](https://qiita.com/RikuS3n/items/e4befcf934ce6a2c83ed)  
```
$ sudo docker run hello-world
```
```
docker: Cannot connect to the Docker daemon at tcp://localhost:2375. Is the docker daemon running?.
See 'docker run --help'.
```
解決策(原因)  
[解決策(原因)](https://qiita.com/RikuS3n/items/e4befcf934ce6a2c83ed#%E8%A7%A3%E6%B1%BA%E7%AD%96%E5%8E%9F%E5%9B%A0)  
```
ocker for Windowsを以前使っていて、
Expose daemon on tcp://localhost:2375 without TLSというオプションにチェックを入れてしまっていたためです。

また、bashもしくはzshなどのrcに記述されているであろう
export DOCKER_HOST='tcp://0.0.0.0:2375'という記述を消さないと、
永遠にそのポートが指定されるので気をつけましょう。
```

## 6. Excute VS Code on WSL  
[後記：在 Linux 環境下使用 Visual Studio Code](https://www.huanlintalk.com/2020/02/wsl-2-installation.html)  

## 7. WSL and Windows  
[WSLとWindows](https://qiita.com/kekenonono/items/1ddbb5a1125d496c0010#4-wsl%E3%81%A8windows)  
```
WSLの中で動作しているのは、ほぼ普通のLinuxでコマンドのバイナリコードもそのままである。
コマンドに関しては特にWSL用に変更が加えられているわけではない。このため、WSL側には、
Linuxのファイルシステムがそのまま見える。
これを「VolFs（Volume File System）」と呼ぶ。これに対して、
Windows OS側の普通のファイルシステム（Cドライブなど）は、WSL側からは、
「/mnt/」以下にドライブ文字から始まるパスとして見ることができる。
これを「DrvFs（Drive File System）」と呼ぶ。
```
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F521871%2F8aaa5970-9918-011c-572c-859098024658.png?ixlib=rb-1.2.2&auto=format&gif-q=60&q=75&s=86a0d27a0cbd818bc9d04afce465c5f5)  

[【WSL入門】第3回 WSL活用の落とし穴：LinuxからWindowsフォルダへのアクセス完全マスター Apr 19, 2019](https://www.atmarkit.co.jp/ait/articles/1904/19/news033.html)  

[【WSL入門】第4回 bashの展開機能と正規表現の基礎 May 24, 2019](https://www.atmarkit.co.jp/ait/articles/1905/24/news020.html)  
[【WSL入門】第2回　避けては通れないWSLとWindows 10との文字コードの違い Apr 05, 2019](https://www.atmarkit.co.jp/ait/articles/1904/05/news027.html)  


[Windows10 HomeでLinuxに寄せた開発環境を整える Aug 11, 2019](https://qiita.com/v2okimochi/items/c9da7df8d4f03283121b)  
```
目次

    Zipコマンドを使う
    Gitを使う
    まずWindows上のgitで改行コードが自動変換される罠を外す
    Dockerを使う
        Docker Toolbox
        WSL2 + Ubuntu18.04LTS
    Leiningenを入れてPowerShellからClojureを動かせるようにする
    Spacemacsを入れてcider-jack-inからlein replを使えるようにする
        環境変数を読み込めるようにする
        cider-jack-inでreplを起動する
        JVM文字化け問題を何とかする
        TypeScript Layerで自動整形をかける
        Scala Layerで定義ジャンプや補完機能を使う
        その他いろいろ
    PowerShellでSBTの文字コード問題を解決する
    nvm経由でnpmを入れて複数のnodeを切り替えられるようにする
    tfenv経由でterraformを入れて無双する
```


[WSL2 (Windows Subsystem for Linux) - Benjr.tw Sep 27, 2019](http://benjr.tw/102092)  


# 04. WSL2  
[WSL2の環境構築手順 Aug 17, 2019](https://qiita.com/poramal/items/3562472d52fe60f61c56)
[WSL2を使ってみる (InsiderPreview)  Jun 15, 2019](https://qiita.com/namoshika/items/53a9ac2df7eace656870)  
[WSL + Docker + Jenkins + Proxyの地雷を解決する Nov 18, 2019](https://qiita.com/dongsu-iis/items/3a44a38a48b9a1533628)  
[WSL2 で Docker Desktop for Windows (Edge) を利用する Nov 05, 2019](https://qiita.com/SakaiYuki/items/e5ab0061ff3273c0e80f)  


[wsl2でsshサーバを起動し、外部からそこに接続  Jul 03, 2019](https://qiita.com/yabeenico/items/15532c703974dc40a7f5)  

やりたいこと  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F101023%2F008d92b2-0e78-cb20-0089-36b35baf0a5e.png?ixlib=rb-1.2.2&auto=compress%2Cformat&gif-q=60&w=1400&fit=max&s=fa09e7ed82228d8b4e6aec58cd881f90)  

wsl1ではWindowsとLinuxが同じネットワークインターフェースを参照していました。  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F101023%2F0d284fc0-bdb0-9cf4-c284-7f433c601136.png?ixlib=rb-1.2.2&auto=compress%2Cformat&gif-q=60&w=1400&fit=max&s=722472b9dd349572894b9ff22b0bd42b)  

wsl2の場合、LinuxはWindowsと仮想ネットワークで接続された別ホストとして扱われます。  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F101023%2F0a886cb7-32e0-6c51-c9ad-a71db1f6aad8.png?ixlib=rb-1.2.2&auto=compress%2Cformat&gif-q=60&w=1400&fit=max&s=1faea3623a80009547dcaa4596ac4170)  


# WSL2がWindowsからlocalhostで接続できるようになる   
[WSL2がWindowsからlocalhostで接続できるようになる Jul 29, 2019](https://qiita.com/SoraKumo/items/c91b0fd7d434be8f8919)  

## localhostの検証  
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

## WSL2を使うときに便利なbat  
[WSL2を使うときに便利なbat](https://qiita.com/SoraKumo/items/c91b0fd7d434be8f8919#wsl2%E3%82%92%E4%BD%BF%E3%81%86%E3%81%A8%E3%81%8D%E3%81%AB%E4%BE%BF%E5%88%A9%E3%81%AAbat)  
```
全然話は変わりますがWSLの再起動ごとに、sshやWebサーバの起動が面倒だという人のためのおすすめbatファイルがこれです。
```

```
wsl_start.bat

start /b wsl -u root ^
for file in `\find /etc/rc3.d/* -maxdepth 1`; do $file start; done 
```

# WSL2のコロコロ変わるIPをMyDNSで何とかする
[WSL2のコロコロ変わるIPをMyDNSで何とかする Jul 4, 2019](https://qiita.com/SoraKumo/items/388a1315a6bdc16b4d2e)  


# 05. WSL2 vs Hpyer-V  
[WSL2とHyper-Vの関係 updated at 2020-02-28](https://qiita.com/matarillo/items/ca1eecf8f9a3cd76f9ce)  

## Illustration  
[図解](https://qiita.com/matarillo/items/ca1eecf8f9a3cd76f9ce#%E5%9B%B3%E8%A7%A3)  
![alt tag](https://qiita-user-contents.imgix.net/https%3A%2F%2Fqiita-image-store.s3.ap-northeast-1.amazonaws.com%2F0%2F2079%2Fe1b82763-f67d-f30a-2a02-b5ec0199b732.png?ixlib=rb-1.2.2&auto=format&gif-q=60&q=75&w=1400&fit=max&s=1911e2fbd8a3f37bac7b0c2d120eb787)  


# 06. CredSSP authentication is currently disabled on the local client  
[Connecting to Hyper-V from a non-domain joined Windows 10 workstation. Feb 14, 2019](https://www.digitaldarragh.com/2019/02/14/connecting-to-hyper-v-from-a-non-domain-joined-windows-10-workstation/)  

[[SOLVED] Hyper V Remote Management From Windows 10 Pro Oct 14, 2016](https://community.spiceworks.com/topic/1874773-hyper-v-remote-management-from-windows-10-pro)  
[Remotely Manage a Non-Domain Hyper-V Server from Windows 10 ](https://tweaks.com/windows/67216/remotely-manage-a-nondomain-hyperv-server-from-windows-10/)  


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

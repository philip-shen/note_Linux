# Purpose
Take note of WSL from VSCode.
# Table of Contents  
[Linux GUI on WSL](#linux-gui-on-wsl)  
[How to mount USB disk on WSL](#how-to-mount-usb-disk-on-wsl)  
[Windows 10 - Bash (Ubuntu) SU (Root Password)]()  
[Reset Password for WSL Linux Distro in Windows 10]()  

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




# Reference
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

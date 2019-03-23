# Purpose
Take note of Linux CLI

# List CPU and MEM resouce occupation rate ranking
* [Linux 用 ps 與 top 指令找出最耗費 CPU 與記憶體資源的程式 2016/12/22](https://blog.gtwang.org/linux/ps-top-find-processes-by-cpu-memory-usage/)

## ps command
```
ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%mem | head
```
-e 參數是代表輸出所有行程的資訊，而 -o 參數則是用來指定輸出欄位用的，
* pid：行程 ID（process ID）。
* ppid：父行程 ID（parent process ID）。
* cmd：程式名稱。
* %mem：記憶體使用量（百分比）。
* %cpu：CPU 使用量（百分比）。
而 --sort 參數則是指定排序的依據欄位，預設會依照數值由小到大排序

![alt tag](https://i.imgur.com/sFCCN6O.jpg)

## top command
```
top -b -o +%MEM | head -n 17
```
其中 -b 參數是 batch 模式的意思，
而 -o 參數則是設定以記憶體用量來排序行程，
最後面的 head -n 17 則是篩選 top 輸出的文字內容，只保留前 17 行

![alt tag](https://i.imgur.com/ubNQfjN.jpg)

如果程式當掉無法關閉的話，就可以使用 kill 或 killall 這類的指令，中止不正常程式的執行，由於上面的報表中都有每個程式的 PID，
所以使用 PID 來中止特定的程式是最直接的方式。

# What is the difference between DU and DF in Linux?
* [What is the difference between DU and DF in Linux?](https://www.quora.com/What-is-the-difference-between-DU-and-DF-in-Linux)
> Disk Usage. It walks through directory tree and counts the sum size of all files therein. It may not output exact information due to the possibility of unreadable files, hard links in directory tree, etc. It will show information about the specific directory requested. Think, 
*"How much disk space is being used by these files?"*

> Disk Free. Looks at disk used blocks directly in file system metadata. Because of this it returns much faster that du but can only show info about the entire disk/partition. Think, 
*"How much free disk space do I have?"*

![alt tag](https://i.imgur.com/Sd3Icdm.jpg)

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

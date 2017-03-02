# view linux hardware infomation

##cpu
1. cpu统计信息 `$ lscpu`
2. 每个cpu信息 `$ cat /proc/cpuinfo`

##memory
1. `$ free -m`
+ 查看内存详细使用 `$ cat /proc/meminfo`
+ 查看内存硬件信息 `$ dmidecode -t memory`


##Storage
1. 查看硬盘和分区分布 `$ lsblk`
+ 看硬盘和分区详细信息 `$ fdisk -l`
+ 查看挂载的磁盘 `$ df`
+ 查看磁盘信息 `$ diskutil info /dev/disk1`
```text
...
Device Block Size:        512 Bytes   #设备块大小
...
Allocation Block Size:    4096 Bytes  #分配块大小，由系统决定
...
```
+ `du ./` #看到的大小是设备block的数量。

##network 
1. 网卡硬件信息 `$ lspci | grep -i 'eth'`
+ `$ ifconfig -a`
+ `$ ip link show`
+ 但看某个网口详情 `$ ethtool eth0`

##other
1. $ lspci(可能有些系统不支持)
    ```text
    如果想看更详细信息：`$ lspci -v` 或 `$ lspci -vv`
    如想看设备树： `$ lscpi -t`
    ```
+ `$ view bios > dmidecode -t bios`
+ `$ view be less verbose > dmidecode -q`

[linux partitions.分区说明](linuxpartitions.md)

## linux 文件名颜色含义
   1. 绿色：可执行文件，可执行程序。
   + 红色： 压缩文件或包文件
   + 蓝色： 目录
   + 白色： 一般性文件，如文本文件、配置文件、源代码等
   + 浅蓝： 链接文件，主要是使用ln命令建立的文件
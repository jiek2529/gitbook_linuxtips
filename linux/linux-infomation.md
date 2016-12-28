# view linux hardware infomation

1. cpu
  <pre>1. cpu统计信息 > lscpu
  2. 每个cpu信息 > cat /proc/cpuinfo
  </pre>
  
+ memory
  <pre>1. > free -m
  2. 查看内存详细使用 > cat /proc/meminfo
  3. 查看内存硬件信息 > dmidecode -t memory
  </pre>
  
+ Storage
  <pre>1. 查看硬盘和分区分布 > lsblk
  2. 看硬盘和分区详细信息 > fdisk -l
  </pre>
 
+ network 
  <pre>1. 网卡硬件信息 > lspci | grep -i 'eth'
  2. > ifconfig -a
  3. > ip link show
  4. 但看某个网口详情 > ethtool eth0
  </pre>
  
+ other
  <pre>1. > lspci(可能有些系统不支持)
      如果想看更详细信息：lspci -v 或 lspci -vv
      如想看设备树： > lscpi -t
  2. view bios > dmidecode -t bios
  3. view be less verbose > dmidecode -q
  </pre>
  
## [linux partitions.分区说明](linuxpartitions.md)
   
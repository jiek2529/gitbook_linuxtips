# linux command.linux命令 

## 常用命令
1. system info > lsb_release -a 或 > uname -a
+ getconf LONG_BIT #查看系统位数；uname -a也能看出。
+ [linuxInformation](/linux/linux-infomation.md)
+ whoami #查看当前登录用户名
+ env #查看当前环境
+ 一般 man命令查看 manual.  eg: man ls
+ ssh [jiek]@[ip] -p [port]  #ssh连接remote机器
+ useradd -d /home/[jiek] [jiek]  #添加用户
+ passwd [jiek]  #设置修改密码
+ 传输文件 > scp -P (22) tmp.md [jiek]@[ip]/[home/jiek]:/home/jiek/  #把本地文件上传到远程服务器 ；注意 **-P、 ：**
+ ftp 同scp
+ locale #查看系统支持编码清单
+ /etc/sysconfig/i18n 下存编码格式
+ cd - #返回上次的目录
+ ctrl + r #（reverse-i-search）搜索并执行
+ netstat -an | grep 端口号 #查看端口占用情况

oh-my-zsh https://github.com/robbyrussell/oh-my-zsh
一个增强版shell工具

## download 下载模块
+ wget -O {outfilename} {url} #下载url存在指定目录的文件名

+ curl 访问地址的


## 上传
1. scp -v -P (22) tmp.md [jiek]@[ip]/[home/jiek]:/home/jiek/  
```
    把本地tmp.md上传到远程服务器 ；
    注意 1. -P接端口，默认22；2. 远程地址后的冒号，分割地址与目录**
    -v verbose mode 冗长模式
```
    
## install 安装
+ 安装 apt-get：
+ apt-get安装zsh > sudo apt-get install zsh
+ yum安装zsh > yum install zsh
+ brew

## compression 压缩
> tar -cvf a.tar folderOrFiles #把文件或目录打包，不压缩

> tar -zcvf a.tar.gz folderOrFiles #打包并以gzip压缩

> tar -jcvf a.tar.bz2 folderOrFiles #打包并以bzip2压缩

> tar -ztvf a.tar.gz 查看tar.gz包中文件有哪些

> tar -jtvf a.tar.bz2 查看tar.bz2包中文件有哪些

> zip a.zip a.md #把a.md打包进a.zip > zip `-r` f.zip folder

> rar

## decompression 解压
> .tar.gz  > tar -zxvf **.tar.gz

> .tar.bz2 > tar -jxvf **.tar.bz2

> .zip     > unzip **.zip -d a/ # 加-t参数是验证包的完整性

> .rar     > unrar

> .tar.xz  > xz -d a.tar.xz  # 解压为.tar文件，> tar -xvf a.tar
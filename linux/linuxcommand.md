# linux命令 

1. system info > lsb_release -a 或 > uname -a
+ 一般 man命令查看 manual.  eg: man ls
+ ssh [jiek]@[ip] -p [port]  #ssh连接remote机器
+ useradd -d /home/[jiek] [jiek]  #添加用户
+ passwd [jiek]  #设置修改密码
+ scp [jiek]@[ip]/[home/jiek]/temp.md ./temp.md  #把本地文件上传到远程服务器
+ ftp 同scp
+ locale #查看系统支持编码清单
+ /etc/sysconfig/i18n 下存编码格式

oh-my-zsh https://github.com/robbyrussell/oh-my-zsh
一个增强版shell工具

## 下载模块
+ wget -O {outfilename} {url} #下载url存在指定目录的文件名

+ curl



## 安装
+ 安装 apt-get：
+ apt-get安装zsh > sudo apt-get install zsh
+ yum安装zsh > yum install zsh
+ brew
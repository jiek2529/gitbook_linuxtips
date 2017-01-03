# firewall 防火墙 iptables

* /etc/sysconfig/iptables 防火墙规则存放处
* NAT - network Address Translator; 纳特; 网络地址转换(Network Address Translation);

> service iptables (start|stop|status) # 立即生效防火墙开关，**一般使用这个命令**

> chkconfig iptables (on|off) # 重启后生效

> iptables -L # 查看生效结果

## 开关放80端口
    开 > iptables -I INPUT -p TCP --dport 80 -j ACCEPT
    关 > iptables -A OUTPUT -p TCP --dport 80 -j DROP
    以上为临时的，键入即生效。
    如果要持久有效> service iptables save && service iptables restart

## 只允许某个ip访问80端口
> iptables -I INPUT -s 46.166.150.22 -p TCP --dport 80 -j ACCEPT

---
> netstat -ntpl

> telnet (ip) port # 是测试链接端口访问状态

```
~ $ telnet （ip） 443   # **尝试不通时**
Trying (ip)...
Connected to www.jiek.com.
Escape character is '^]'.

^CConnection closed by foreign host.
~ $ telnet (ip) 443   # **检测通时**
Trying (ip)...
Connected to www.jiek.com.
Escape character is '^]'.
Connection closed by foreign host.
```


reference : http://blog.csdn.net/jk0803_wantao/article/details/43668937


---
## iptables 简介与使用
<pre>
iptables共3个tables（filter nat mangle，现在貌似是4个表）5条chains（PREROUTING INPUT FORWARDING OUTPUT POSTROUTING）4个连接跟踪数据包状态（NEW INVALID ESTABLISHED RELATED）.用iptables -t [table] -L查看每个表。五条链的数据包转发流程如下：


基本语法：iptables -t table -命令 -匹配 -j 动作/目标
1. 清除规则
iptables -F
iptables -X
iptables -Z
iptables -F -t nat
iptables -X -t nat
iptables -Z -t nat

2. 设置默认策略
一般策略：filter的INPUT和FORWARD都是DROP然后配置指定的ACCEPT，OUTPUT则是ACCEPT然后配置指定的DROP。
先不要关闭filter的INPUT，配置完关键的22等端口的ACCEPT之后再设置iptables -P INPUT DROP
关闭filter表的FORWARD：iptables -P FORWARD DROP，考虑到如果作为路由器，可以打开FORWARD，后面的对filter的FORWARD则不用再配置。
关闭filter表的OUTPUT：iptables -P OUTPUT DROP，一般是开启OUTPUT:iptables -P OUTPUT ACCEPT
开启nat表的三个链：PREROUTING OUTPUT POSTROUTING，默认都是ACCEPT可以不用设置。
     iptables -t nat -P PREROUTING ACCEPT
     iptables -t nat -P OUTPUT ACCEPT
     iptables -t nat -P POSTROUTING ACCEPT

3. 设置filter表
开启回环地址：iptables -A INPUT -i lo -p all -j ACCEPT
     iptables -A OUTPUT -o lo -p all -j ACCEPT
连接状态设置：iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
丢弃非法链接：iptables -A INPUT -m state --state INVALID -j DROP
     iptables -A OUTPUT -m state --state INVALID -j DROP
     iptables -A FORWARD -m state --state INVALID -j DROP

设置一些常用端口的开启：
     允许访问本机的SSH：
     iptables -A INPUT -p tcp --dport 22 -j ACCEPT
     iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT

     如果自身做了web服务器，则需要开启80端口的INPUT的OUTPUT：
     iptables -A INPUT -p tcp --dport 80 -j ACCEPT
     iptables -A OUTPUT -p tcp --sport 80 -j ACCEPT
     如果自身做了邮件服务器，则开启25,110
     iptables -A INPUT -p tcp --dport 25 -j ACCEPT
     iptables -A INPUT -p tcp --dport 110 -j ACCEPT
     iptables -A INPUT -p udp--dport 110 -j ACCEPT
     如果自身做了FTP服务器，则开启21
     iptables -A INPUT -p tcp --dport 21 -j ACCEPT
     如果自身做了DNS服务器，则开启53
     iptables -A INPUT -p tcp --dport 53-j ACCEPT
     iptables -A INPUT -p udp --dport 53 -j ACCEPT
     使用dnsmasq的DHCP服务还要开启67端口的UDP
     iptables -A INPUT -p udp--dport 67 -j ACCEPT
     
     允许ping
     iptables -A OUTPUT -p icmp -j ACCEPT
     iptables -A INPUT -p icmp -j ACCEPT

    
     设置内网转发：
     iptables -A FORWARD -s 192.168.0.0/16 -j ACCEPT
     iptables -A FORWARD -d 192.168.0.0/16 -j ACCEPT
     
     限制只能转发部分端口：
     访问外界网站则需要80端口转发：
     iptables -A FORWARD -p tcp --dport 80 -j ACCEPT

     设置DNS转发，注意自身的namenode要添加一些DNS？：
     iptables -A FORWARD -p tcp --dport 53 -j ACCEPT
     iptables -A FORWARD -p udp --dport 53 -j ACCEPT

     允许内网主机收发邮件：
     iptables -A FORWARD -p tcp --dport 25 -j ACCPET
     iptables -A FORWARD -p tcp --dport 110 -j ACCEPT
     iptables -A FORWARD -p udp --dport 110 -j ACCEPT
     iptables -A FORWARD -p tcp --dport 143 -j ACCEPT
     iptables -A FORWARD -p udp --dport 143 -j ACCEPT
     iptables -A FORWARD -p tcp --dport 993 -j ACCEPT
     iptables -A FORWARD -p udp --dport 993 -j ACCEPT
     iptables -A FORWARD -p tcp --dport 995 -j ACCEPT
     iptables -A FORWARD -p udp --dport 995 -j ACCEPT
     允许内网主机登录QQ：
     iptables -A FORWARD -p tcp --dport 8000 -j ACCEPT
     iptables -A FORWARD -p udp --dport 8000 -j ACCEPT
     iptables -A FORWARD -p tcp --dport 443 -j ACCEPT
     iptables -A FORWARD -p udp --dport 4000 -j ACCEPT

     当filter的FORWARD设置为DROP时，必须要设置接口转发,eth0连接外网，eth1连接内网：
     iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
     iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT

     丢弃坏的TCP包：
     iptables -A FORWARD -p TCP ! --syn -m state --state NEW -j ACCEPT
     处理IP碎片数量，放置攻击，允许每秒100个
     iptables -A FORWARD -f -m limit --limit 100/s --limit-burst 100 -j ACCEPT
     设置ICMP包过滤，允许每秒1个包，限制触发条件是10个包
     iptables -A FORWARD -p icmp -m limit --limit 1/s --limit-burst 10 -j ACCEPT
         
     
4. 设置nat表
     开启NAT：
     iptables -t nat -A POSTROUTING -o eth0 -s 192.168.0.0/16 -j MASQUERADE
     防止外网用内网IP欺骗：
     iptables -t nat -A PREROUTING -i eth0 -s 10.0.0.0/8 -j DROP
     iptables -t nat -A PREROUTING -i eth0 -s 172.16.0.0/12 -j DROP
     iptables -t nat -A PREROUTING -i eth0 -s 192.168.0.0/16 -j DROP
     转发80端口到内网某台主机的80端口
     iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j DNAT --to-destination 192.168.0.3:80 
     禁止与某个IP的所有连接：
     iptables -t nat -A PREROUTING -d 211.101.46.253 -j DROP
     禁止某个端口：
     iptables -t nat -A PREROUTING -p tcp --dport 21 -j DROP

5. 保存iptables并重启
     iptables-save > /etc/iptables/iptables.rules
     systemctl reload iptables

6. 设置net.ipv4.ip_forward为1
     每次重启都要设置
     echo 1 > /proc/sys/net/ipv4/ip_forward     
     或者：
     sysctl -w net.ipv4.ip_forward=1  
     为了使重启仍然生效：
     /etc/sysctl.d/40-ip-forward.conf
     net.ipv4.ip_forward=1
     ipv6相关的转发？对应的文件是在/proc/sys/net/ipv6/conf/下
     net.ipv6.conf.default.forwarding=1
     net.ipv6.conf.all.forwarding=1</pre>
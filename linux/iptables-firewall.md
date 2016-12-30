# firewall 防火墙 iptables

> service iptables (start|stop|status) # 立即生效防火墙开关，**一般使用这个命令**

> chkconfig iptables (on|off) # 重启后生效

> iptables -L # 查看生效结果

## 开关放80端口
    开 > iptables -I INPUT -p TCP --dport 80 -j ACCEPT
    关 > iptables -A OUTPUT -p TCP--dport 80 -j DROP
    以上为临时的，键入即生效。
    如果要持久有效> service iptables save && service iptables restart

## 只允许某个ip访问80端口
> iptables -I INPUT -s 46.166.150.22 -p TCP --dport 80 -j ACCEPT


reference : http://blog.csdn.net/jk0803_wantao/article/details/43668937
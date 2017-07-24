#VPS搭建 翻*墙

##购买VPS
1.购买一个VPS，具体的话随便搜索一下或者某宝都能买到。
2.线路来说，首选 洛杉矶 的服务器（香港和日本的服务器听闻线路更改了，先转到美帝再转回国内的，所以我就自己买了洛杉矶的。）
3.价格和配置都是五花八门的。 （之前一直用付费的ss，不稳定且线路是多人共享的,价格比现在还贵）
4.系统要求用CentOS （一般都可选，如果不提供的话请联系服务商的管理员；或者可自行重装为CentOS 32或64位）
5.内存要求≥128M （但是我买的比较便宜的配置，64MB内存暂时自己一个人用的话感觉正常，YouTube 1080OP毫无压力）

##配置
1. 购买VPS以后，请进入管理面板，在这里你可以看到你的VPS相关信息
PS：尤其需要注意这里：
这是你VPS的连接端口。我这里是5213，你需要填写你的端口号才能进行后面的连接
2. 连接VPS工具Putty

使用Putty login到服务器
一般以root去连
一键部署VPS（复制下面的代码并按回车。 中途会提示设置端口和密码，如果直接回车使用的是默认配置）
```shell
> wget –no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh  
> chmod +x shadowsocks.sh  
> ./shadowsocks.sh 2>&1 | tee shadowsocks.log  
```

##使用端配置
相关下载给个关键词找
Windows: ShadowsocksR-win32/64
Mac: ShadowsocksX-2.6.3.dmg
Android: shadowsocksR-v2.10.8.4.apk
Ios： **花钱**

![](/assets/20160817182426038.jfif)
细节细研究，需要同自己服务器配置一致

##参考
http://blog.csdn.net/qq_19835843/article/details/52233111
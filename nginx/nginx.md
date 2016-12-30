# nginx

http://nginx.org/download/

https://www.nginx.com/resources/wiki/start/topics/tutorials/commandline/

```
其需要的资源及下载地址
pcre --> http://www.pcre.org/
ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/

zlib --> http://zlib.net
http://zlib.net/zlib-1.2.8.tar.gz

openssl --> https://www.openssl.org/source
去其github上下载

配置官方文档
http://nginx.org/en/docs/configure.html

eg: > ./configure
    --sbin-path=/usr/local/nginx/nginx
    --conf-path=/usr/local/nginx/nginx.conf
    --pid-path=/usr/local/nginx/nginx.pid
    --with-http_ssl_module
    --with-pcre=../pcre-8.39
    --with-zlib=../zlib-1.2.8
    --with-openssl=../openssl
  > sudo make && make install
  注:src/core/ngx_regex.h:24: 错误：expected specifier-qualifier-list before ‘pcre’
  解决办法：
  1. > pcre 可能下载的是pcre2,改成pcre-8.39，应该就可以。
  2. > yum -y install pcre-devel #安装pcre-devel，不确定是否需要这样安装？？？

  > ./nginx # 启动
  > ./nginx -s stop # 停止
```

```
apache的开关： service httpd (start|restart|graceful|graceful-stop|stop)

查看端口占用情况： > lsof -i tcp:80
查看端口：        > netstat -tln   或  netstat -an | grep 80
查看运行中的进程： > ps -ef | grep (apache|nginx)
```
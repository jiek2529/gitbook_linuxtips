# macTerminalTips

1. mac触角功能设置： apple > System Preferences > Destop & screen Saver > Screen Saver > (right bottom)Hot Corners > (left bottom).Start Screen saver

+ Require password after sleep or screen saver:  apple > System preferences > Security & Privacy > General > 5 seconds

+ AirDrop的机器名设置：system preferences > sharing > modify computer name

+ 命令行常用快捷键
  ```
  Ctrl + A 光标跳行最前端
  Ctrl + E 光标跳行最末端
  Ctrl + W 删除光标前一段参数
  Ctrl + U 删除光标前一行
  Ctrl + K 删除光标后的行串
  Shift + CMD + { }切换terminal前后Tab页
  CMD + T 新开Terminal
  option + 方向左或右 光标跳到前一分词位
  FN + 方向上下左右 翻页
  CMD + K 清屏
  Ctrl + R 搜索历史中的命令,并执行（reverse-i-search）
```
~Mac 键盘快捷键- Apple 支持： [support](https://support.apple.com/zh-cn/HT201236)

+ 常用命令
  1. scutil > sudo scutil --set HostName {new_name} #设置命令行机器名
  + scutil --get HostName 获取命令行机器名

+ VIM
  ```
  Shift + 4 行尾  6行首
  ```
+ 
  adsfa

+ openssl
  ```
  Mac上升级Openssl
  默认系统中存在一个0.9.8在/usr/bin/openssl,因权限问题，不可删除
  用户bin目录的PATH有优先顺序，是顺序查询出的
  可通过 >echo $PATH   
  查看其内容的优先顺序，由/User/apple/bin -> /usr/local/bin - > /usr/bin -> /bin这样优先顺序
  把openssl编译安装的命令 ln -s {path} /usr/local/bin/openssl这样来达到升级目的
  通过>openssl version 或 which openssl来检验是否升级成功
  ~~安装方法~~
  > 从https://github.com/openssl/openssl 下载源码或下tar.gz包
  > tar zxvf openssl***.tar.gz
  > cd openssl
  > ./config --prefix=/usr/local/openssl  //编译后的目标目录
  > make && make install
  > 待跑半天后完成时，没错误提示表正常结果
  > cd /usr/local/openssl/bin
  > ls -la | grep openssl   //查看是否有此文件，有则表示安装正常
  > ln -s /usr/local/openssl/bin/openssl /usr/local/bin/openssl
  > openssl version    //查看是否是自己编译生成的openssl的版本
  ```

+ tengine
  ##### install tengine reference :[http://www.tuicool.com/articles/mQnAryz](http://www.tuicool.com/articles/mQnAryz)
  ```
> ./configure --prefix=/Users/jiek/Downloads/tengine --with-pcre=/Users/jiek/Downloads/tengine_install/pcre-8.36 --with-zlib=/Users/jiek/Downloads/tengine\_install/zlib-1.2.8 --with-openssl=/Users/jiek/Downloads/tengine_install/openssl-1.0.2a --with-http_gzip_static_module --with-http_realip_module --with-http_stub_status_module --with-http_concat_module --with-http_footer_filter_module=shared --with-http_limit_req_module=shared
> make && make install
##### 注：pcre：ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre，直接下载解压并放入--with-pcre的目录位置就行.
20161121安装未成功，提示openssl的一堆定义未声明，待研究

  ```
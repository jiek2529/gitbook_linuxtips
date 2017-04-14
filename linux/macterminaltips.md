# macTerminalTips

1. Mac导出机器的所有配置信息方法： `Launchpad > Others > System Information > menu File > Save`就可把机器的信息保存到 {}.spx文件里，可在Mac下直接打开。

+ mac触角功能设置： apple > System Preferences > Destop & screen Saver > Screen Saver > (right bottom)Hot Corners > (left bottom).Start Screen saver

+ Require password after sleep or screen saver:  apple > System preferences > Security & Privacy > General > 5 seconds

+ AirDrop的机器名设置：system preferences > sharing > modify computer name

##命令行常用快捷键
```text
Ctrl + D        删除一个字符，相当于通常的Delete键（命令行若无所有字符，则相当于exit；处理多行标准输入时也表示eof）
Ctrl + H        退格删除一个字符，相当于通常的Backspace键
Ctrl + U        删除光标之前到行首的字符
Ctrl + K        删除光标之前到行尾的字符
Ctrl + C        取消当前行输入的命令，相当于Ctrl + Break
Ctrl + A        光标移动到行首（Ahead of line），相当于通常的Home键
Ctrl + E        光标移动到行尾（End of line）
Ctrl + F        光标向前(Forward)移动一个字符位置
Ctrl + B        光标往回(Backward)移动一个字符位置
Ctrl + L        清屏，相当于执行clear命令
Ctrl + P        调出命令历史中的前一条（Previous）命令，相当于通常的上箭头
Ctrl + N        调出命令历史中的下一条（Next）命令，相当于通常的上箭头
Ctrl + R        显示：号提示，根据用户输入查找相关历史命令（reverse-i-search）
Alt + 方向左右，跳一个参数段
_
次常用快捷键：
Alt + F         光标向前（Forward）移动到下一个单词
Alt + B         光标往回（Backward）移动到前一个单词
Ctrl + W        删除光标前一段参数
Alt + D         删除从光标位置到当前所处单词的末尾
Ctrl + Y        粘贴最后一次被删除的单词  
Alt + 方向左右，跳一个参Ctrl + E 光标跳行最末端
Shift + CMD + { }切换terminal前后Tab页
CMD + T 新开Terminal
option + 方向左或右 光标跳到前一分词位
FN + 方向上下左右 翻页
CMD + K 清屏
Ctrl + R 搜索历史中的命令,并执行（reverse-i-search）
** Finder 中 Ctrl + K 打开远程连接smb
```
~Mac 键盘快捷键- Apple 支持： [support](https://support.apple.com/zh-cn/HT201236)

##常用命令
  
  1. scutil > sudo scutil --set HostName {new_name} #设置命令行机器名
  + scutil --get HostName 获取命令行机器名
  + whoami
  + env
  + sudo su - #切换到root用户
  + mkfile -n 1g ~/empty.log　创建占用空文件（20150908）
    ； 类WINDOW下的管理员执行fsutil file createnew empty.log 1024000

##brew
mac 下使用的下载安装工具

https://github.com/Homebrew/homebrew-core

https://github.com/caskroom/homebrew-cask

[清华开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)

##openssl
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

##tengine
  ##### install tengine reference :[http://www.tuicool.com/articles/mQnAryz](http://www.tuicool.com/articles/mQnAryz)
```cmd
> ./configure --prefix=/Users/jiek/Downloads/tengine --with-pcre=/Users/jiek/Downloads/tengine_install/pcre-8.36 --with-zlib=/Users/jiek/Downloads/tengine\_install/zlib-1.2.8 --with-openssl=/Users/jiek/Downloads/tengine_install/openssl-1.0.2a --with-http_gzip_static_module --with-http_realip_module --with-http_stub_status_module --with-http_concat_module --with-http_footer_filter_module=shared --with-http_limit_req_module=shared
> make && make install

** 注：pcre：ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre，直接下载解压并放入--with-pcre的目录位置就行.
20161121安装未成功，提示openssl的一堆定义未声明，待研究
**
```
  
##取消MAC的iTunes的iphone信认(20161222)
 iphone 设置setting > 通用general > 还原reset > 还原网络设置reset network settings
 
 
##FAQ:
> terminal 显示文件内容为空，但文件确实有内容，原因可能是修改过命令终端的编码格式。（原本是U8，我改成hz gb2312时会必现此现象 20161228）
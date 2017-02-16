# gitbook

[How to install gitbook?](https://www.npmjs.com/package/gitbook-cli)

[install nodejs&npm](/node/installnodejs.md)

https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md

https://toolchain.gitbook.com/syntax/markdown.html

## install gitbook
```shell
> npm install -g gitbook-cli
> gitbook init  # 如果是空项目，可以使用这个方法去创建初始项目
或把自己的markdown项目考进去，也行

运行本机gitbook> gitbook serve & 
必须在book.json的目录去执行此命令
> gitbook --port 5000 serve &   # 即使用5000端口运行程序
> gitbook install               # 即把book.json里添加的plugin的插件全部安装上。
```

https://jiek.icitsoft.com/

https://www.gitbook.com/@jiek


##plugin插件

https://plugins.gitbook.com/

https://libraries.io/

https://ymcatar.gitbooks.io/gitbook-test/content/

```json
在项目的book.json文件中编辑添加插件
{ 
"gitbook","2.0.0",             # 指定版本运行。
"plugin": { 
        "comment",             # ...
        "highlight",           # 高亮
        "search",              # 左导航顶部搜索
        "fontsettings",         # 左上角字体设置
        "expandable-chapters", # 左菜单二级折叠
        "anchors",             # 右边锚点索引 带 回顶部
        "anchor-navigation-ex",# 右边锚点索引 带 回顶部
        "page-footer",         # 页尾
        "splitter",            # 左导航可变宽度
        "editlink",            # 左上角出现编辑按钮
        "disqus",              # disqus.com的论坛插件，中国一般无法使用
        "search-plus",         # 搜索，内容索引
        "spoiler",             # 透视，遮挡，折叠...
        "youtubex",            # youtube视频插件
        "collapsible-menu",    # **它可能会导致界面显示出异常头尾代码**
        "include",             # template模板包含
        
        "facebook",            # facebook develop comment plugin
        "duoshuo",             # 多说
        "comment",             #...
        "disqus",              # disqus.com的论坛插件，中国一般无法使用
        
        "katex",               # KaTex数学表达式
        "maxjax",              # MaxJax数学表达式
        }
  "pluginsConfig": {
        "disqus": {            # 此处的插件配置与插件配套使用，键同上一样。配置方式由插件说明去配置。
              "shortName": "jiek"
        }
  }
}
再在book.json的同级目录运行 > gitbook install ，即能把添加的插件一一安装上。

此目录下的package.json文件是通过这条命令自动生成的。
```

## pulgin version setting

查看使用的插件版本号
指定插件版本号：
{
"plugin: ["ace@0.2.1"]  **//当不带@version时，表示使用最新版本latest**
}

## nginx + gitbook

自搭服务器，安装nginx和gitbook环境
$ gitbook serve --gitbook=2.0.0 &   #运行默认4000的服务;可用--getbook=2.0.0来指定版本运行。默认用最新的版本。

nginx.conf中添加

```json
{
  location /gitbook/ {
    proxy_pass http://localhost:4000;
    # alias /var/www/gitbook/_book/;    # 指向静态路径，此方法可不用启动gitbook serve; 只要gitbook init && gitbook build;
  }
  ...
}
```
虚路径访问方法：http://jiek.domain.com/gitbook/,访问后，点击书中其它页，
如：http://jiek.domain.com/gitbook/first.html后，页面正常显示，但地址会变为：http://jiek.domain.com/first.html，再在页面中访问其它任何页，都会是404不存在的问题（页面无动静）。

解决方案：

1. 我是以root用户去启动的nginx和gitbook serve。
+ gitbook运行使用到的server.js是/root/.gitbook/versions/{3.2.2}/lib/cli/server.js
+ vi /root/.gitbook/versions/3.2.2/lib/cli/server.js
+ /X-Current-Location #定位到这个header参数
+ 3.2.2版本是在 84和91行，把此两行注释掉
+ nginx -s reload
一切正常了，访问自己服务上的gitbook的任何页，不会出来跳不动的显示 ，且response headers中都不会出现 X-Current-Location了。

##默认带有五个插件

```
highlight
search
sharing
font-settings
livereload
除去自带插件，插件前加「-」，如："-search"
```

------

npm install --save gitbook-plugin-toggle-chapters #等同于上这的plugin的『expandable-chapters』

------
## facebook comment

**usage**

To add Facebook comments into your GitBook, you need to first obtain your personal Application ID from Facebook. To do so, you can follow the guide here.

After obtaining the ID, add the following config into your book.json and you should be good to go:
```json
"plugins": [
    "facebook"
    ...
],
"pluginsConfig": {
    "facebook": {
        "appKey": {{YOUR ID SHOULD BE INSERTED HERE}}
    }
    ...
}
```

[GitBook语法.中文](http://xianbai.me/learn-md/article/extension/strikethrougn.html "GitBook语法.中文")

------

## sectionx

```
<!--sec data-title="Introduction" data-id="section0" data-show=true ces-->
Insert markdown content here (you should start with h3 if you use heading).
<!--endsec-->
```
<!--sec data-title="Introduction" data-id="section0" data-show=true ces-->
Insert markdown content here (you should start with h3 if you use heading).
<!--endsec-->


## mcqx

问答题 gitbook-plugin-mcqx

https://github.com/ymcatar/gitbook-plugin-mcqx

```
eg:
{%mcq ans="o1", count=2, random=true%}
{%title%} This is a question?
{%o1%} First option
{%o2%} Second option
{%o3%} Third option
{%o4%} Fourth option
{%hint%} This is a hint.
{%endmcq%}
```
{%mcq ans="o1", count=2, random=true%}
{%title%} This is a question?
{%o1%} First option
{%o2%} Second option
{%o3%} Third option
{%o4%} Fourth option
{%hint%} This is a hint.
{%endmcq%}

## ace

{%ace edit=true, lang='c_cpp'%}
// This is a hello world program for C.
#include <stdio.h>

int main(){
  printf("Hello World!");
  return 1;
}
{%endace%}

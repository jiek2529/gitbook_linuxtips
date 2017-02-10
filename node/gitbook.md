# gitbook

[install nodejs&npm](/node/installnodejs.md)

https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md

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
{ "plugin": { 
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
        ,"disqus"              # disqus.com的论坛插件，中国一般无法使用
        "search-plus",         # 搜索，内容索引
        "spoiler",             # 透视，遮挡，折叠...
        "youtubex",            # youtube视频插件
        "collapsible-menu",    # **它可能会导致界面显示出异常头尾代码**
        
        "facebook",            # facebook develop comment plugin
        "duoshuo",             # 多说
        "comment",             #...
        "disqus",              # disqus.com的论坛插件，中国一般无法使用
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

[语法中文]("http://xianbai.me/learn-md/article/extension/strikethrougn.html" "语法中文")

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

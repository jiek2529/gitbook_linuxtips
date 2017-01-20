# gitbook

[install nodejs&npm](/node/installnodejs.md)
https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md

```
> npm install -g gitbook-cli
> gitbook init  # 如果是空项目，可以使用这个方法去创建初始项目
或把自己的markdown项目考进去，也行

运行本机gitbook> gitbook serve & 
```

https://jiek.icitsoft.com/

https://www.gitbook.com/@jiek


##插件
https://libraries.io/

```
在项目的book.json文件中编辑添加插件
{ "plugin": { 
        "comment",
        "highlight",
        "search",
        "fontsettings"
        ,"splitter"
        ,"expandable-chapters" #左菜单二级折叠
        ,"anchors"
        ,"anchor-navigation-ex"
        ,"page-footer"
        ,"splitter"   # 左导航可变宽度
        }
}
再在book.json的同级目录运行 > gitbook install ，即能把添加的插件一一安装上。

此目录下的package.json文件是通过这条命令自动生成的。
```
------

npm install --save gitbook-plugin-toggle-chapters #等同于上这的plugin的『expandable-chapters』

------
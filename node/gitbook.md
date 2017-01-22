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


##plugin插件
https://libraries.io/

```
在项目的book.json文件中编辑添加插件
{ "plugin": { 
        "comment",             # ...
        "highlight",           # 高亮
        "search",              # 左导航顶部搜索
        "fontsettings"         # 左上角字体设置
        ,"expandable-chapters" # 左菜单二级折叠
        ,"anchors"             # 右边锚点索引 带 回顶部
        ,"anchor-navigation-ex"# 右边锚点索引 带 回顶部
        ,"page-footer"         # 页尾
        ,"splitter"            # 左导航可变宽度
        ,"editlink"            # 左上角出现编辑按钮
        }
}
再在book.json的同级目录运行 > gitbook install ，即能把添加的插件一一安装上。

此目录下的package.json文件是通过这条命令自动生成的。
```
------

npm install --save gitbook-plugin-toggle-chapters #等同于上这的plugin的『expandable-chapters』

------
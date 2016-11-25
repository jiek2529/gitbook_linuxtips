# node markdown 安装与使用

1. 安装 node + npm
+ npm install markdown
+ npm install marked
+ node markdown.js
---
markdown.js
```
var text = "##hello\n"+
 "---\n" +
 "[baidu](http://www.baidu.com)\n" +
 "Hello *World*!";
var markdown = require( "markdown" ).markdown;
console.log( markdown.toHTML( text ) );
```
terminal //去运行看控制台输出结果，markdown效果，不能输出表格
> node markdown.js

^ 参考：http://www.letiantian.me/2014-10-19-node-markdown-marked-convert-markdown/

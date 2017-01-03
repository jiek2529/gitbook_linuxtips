# vim

## command line
<pre>:{linenum}                     跳转到的行数
:set nu                          显示行号，设定之后，会在每一行的前面显示该行的行号
:set nonu                          与set nu相反，为取消行号
:1,$s/keyword1/keyword2/g{c}     文本替换，最后一个参数是询问参数
:n1,n2 w [filename]                 将n1到n2的内容保存为filename 这个文件
:6,9 co 12                       复制第6行到第9行之间的内容到第12行后面。 copy
:6,9 m 12                           剪切第6行到第9行之间的内容到第12行后面。 move
:6(,9) de                        删除一行或多行

</pre>

## shortcut key
<pre>shift + g                      到文件末尾
gg                               到文件开始
yy                                  拷贝
nyy                              yanked n行拷贝
p                                   paste 粘贴

10                                  跳第10行
10|                              跳光标行第10列
0                                   跳行首
$                                行尾
^                                   跳到本行非空格符
H                                光标移动到屏幕最顶行
M                                   光标移动到屏幕中间行
G                                光标移动到屏幕最尾行
</pre>        
  
## 翻屏
<pre>ctrl + f           下翻一屏。
ctrl + b                  上翻一屏。
ctrl + d                下翻半屏。
ctrl + u                  上翻半屏。
ctrl + e                向下滚动一行。
ctrl + y                   向上滚动一行。
n%                      到文件n%的位置。
zz                         将当前行移动到屏幕中央。
zt                      将当前行移动到屏幕顶端。
zb                         将当前行移动到屏幕底端。
</pre>


## reference
1. http://vimdoc.sourceforge.net/htmldoc/help.html
2. http://blog.csdn.net/scaleqiao/article/details/45153379
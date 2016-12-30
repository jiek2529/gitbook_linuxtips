# vim

```
:{linenum}    //跳转到的行数
:set nu                            显示行号，设定之后，会在每一行的前面显示该行的行号
:set nonu                          与set nu相反，为取消行号
:1,$s/keyword1/keyword2/g{c} 文本替换，最后一个参数是询问参数
n1,n2 w [filename]                 将n1到n2的内容保存为filename 这个文件
     shift + g                     到文件末尾
     g + g                          到文件开始
```
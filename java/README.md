# 有关java的运行与环境

1. apktool d *.apk            # 反编译APK
+ dex2jar.sh ./classes.dex   # 反编译dex至jar
+ 

```text
常用命令
/usr/libexec/java_home -V 全系统中版本信息 <=> java -version
jar
javac
java
javap
javah
javadoc
```

##miscellaneous

https://wilsonmar.github.io/java-on-apple-mac-osx/

#openJDK

OpenJDK原是Sun Microsystems公司为Java平台构建的Java开发环境（JDK）的开源版本，完全自由，开放源码。Sun Microsystems公司在2006年的JavaOne大会上称将对Java开放源代码，于2009年4月15日正式发布OpenJDK。甲骨文在2010年收购Sun Microsystem之后接管了这个项目。

http://openjdk.java.net/install/

official github: https://github.com/hgomez/obuildfactory

**默认的Android Studio {preview}版本里都内嵌了openJDK. 使用`{path}/Contents/jre/jdk/Contents/Home/bin/java -v`可看得出**
------

1. [groovy console](/java/groovyconsole.md)
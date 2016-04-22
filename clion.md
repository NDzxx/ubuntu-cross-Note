# 破解CLion
##Gradle 安装
简介
Gradle 是以 Groovy 语言为基础，面向Java应用为主。基于DSL（领域特定语言）语法的自动化构建工具。

现在Android Studio用它来编译APK程序
前提

Ubuntu官方源的Gradle太陈旧了。。。陈旧到不支持Android Studio的 jcenter方法，如果强行编译，会出现如下错误：

Could not find method jcenter() for arguments [] on repository container.

所以，起码到现在(2015-08-20), 不要用$sudo apt-get install gradle来安装 gradle，如果安装了，要用 $ sudo apt-get remove gradle卸载掉  
###安装  
下载  

下载地址为 http://www.gradle.org/downloads  
  
这个地址是distribution的地址：http://services.gradle.org/distributions

截至目前为止，第一个链接不能下载，第二个可以。  
而如果从第一个链接得到地址后替换地址中的https://为http://后就可以下载了。  

按照惯例，如果感觉下载困难，可以从 http://download.csdn.net/detail/stwstw0123/8956303 直接下载来用
###安装配置
安装

复制下载的 gradle-2.6-all.zip 到目 ~ 下
```
$ cd ~
$ sudo unzip gradle-2.6-all.zip -d /opt/gradle/
```
配置
```
 $ sudo vim /etc/profile

 ```

文件末尾添加：  

export GRADLE_HOME=/opt/gradle/gradle-2.6    
export PATH=$GRADLE_HOME/bin:$PATH  

重启

重启机器，然后就可以运行 gradle -v
```
$ sudo reboot  
$ gradle -v  
```
##破解


PhpStorm是我最喜欢的PHP开发工具，也偶尔用下Clion，Idea 等Jetbrains其他产品，但问题来了，需要注册码，如何破解？

好在，有高手已经研究出破解的方法，并将代码开源公布在Github上，破解过程如下：

1、安装Java运行环境（注意：至少 Java 7），安装过程自己百度一下；

2、下载工具 https://github.com/rover12421/JetbrainsPatchKeygen 到本地，解压；

3、切换到解压目录，运行如下命令：

./gradlew fatjar

4、在同级的目录下，会生成一个 build 文件夹，再执行如下代码：

java -jar ./build/libs/JetbrainsPatchKeygen-1.2.1.jar  

// 注意：JetbrainsPatchKeygen 后面的版本号可能跟我的不同，自己调整

5、然后：
```

Jetbrains's Product Patch or Keygen.
Crack by Rover12421.
Http://Www.Rover12421.Com
Please support genuine(https://www.jetbrains.com).

Please select product:
1. RubyMine
2. PyCharm
3. WebStorm
4. PhpStorm
5. AppCode
6. Clion
7. Idea
6
Please enter your username :
Rover12421
Clion need patch
Please enter your Clion install path or clion.jar path :
/Develop/jetbrains/CLion/Clion
Find Key. Patch...
---------------------------------------
Product : Clion
UserName : Rover12421
===== LICENSE BEGIN =====
6097-D69799T
00000fxZErQ6!bLiVKLLPWdjESYOER
vidz!7EtdSji53QcEYk0npwOkl926D
mMXEzJgM3G1M3I"""bSI0Dg8"vXaAj
===== LICENSE END =====
```
把===== LICENSE BEGIN ===== 和 ===== LICENSE END =====一起复制进去



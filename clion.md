# 破解CLion
##Gradle 安装
简介
Gradle 是以 Groovy 语言为基础，面向Java应用为主。基于DSL（领域特定语言）语法的自动化构建工具。

现在Android Studio用它来编译APK程序
前提

Ubuntu官方源的Gradle太陈旧了。。。陈旧到不支持Android Studio的 jcenter方法，如果强行编译，会出现如下错误：

Could not find method jcenter() for arguments [] on repository container.

所以，起码到现在(2015-08-20), 不要用$sudo apt-get install gradle来安装 gradle，如果安装了，要用 $ sudo apt-get remove gradle卸载掉
安装
下载

下载地址为 http://www.gradle.org/downloads

这个地址是distribution的地址：http://services.gradle.org/distributions

截至目前为止，第一个链接不能下载，第二个可以。而如果从第一个链接得到地址后替换地址中的https://为http://后就可以下载了。

按照惯例，如果感觉下载困难，可以从 http://download.csdn.net/detail/stwstw0123/8956303 直接下载来用
安装配置
安装

复制下载的 gradle-2.6-all.zip 到目 ~ 下

$ cd ~
$ sudo unzip gradle-2.6-all.zip -d /opt/gradle/

    1
    2

配置

 $ sudo vim /etc/profile

    1

文件末尾添加：

export GRADLE_HOME=/opt/gradle/gradle-2.6
export PATH=$GRADLE_HOME/bin:$PATH

重启

重启机器，然后就可以运行 gradle -v

$ sudo reboot
$ gradle -v
# 软件安装和配置
1.编译环境

##切换163源  
sudo gedit /etc/apt/sources.list
在gedit打开的文件后复制黏贴以下内容
deb http://mirrors.163.com/ubuntu/ vivid main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ vivid-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ vivid-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ vivid-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ vivid main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ vivid-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ vivid-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ vivid-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ vivid-backports main restricted universe multiverse  
写上软件源后，再刷新一下，注意一定要刷新，运行：  
sudo apt-get update


sudo apt-get build-essential

##cmake
 sudo apt-get install cmake
 
sudo apt-get install cmake-qt-gui  

##更新到g++5
默认安装的g++4.8有一些c++11新特性不支持，需要更新到g++5  
sudo add-apt-repository ppa:ubuntu-toolchain-r/test  
sudo add-apt-repository ppa:ubuntu-toolchain-r/test  
sudo apt-get install gcc-5 g++-5  
sudo updatedb && sudo ldconfig  
locate gcc  
查看版本  gcc -v 如果显示是5.3就对了  
参考:  
[ubuntu升级gcc5](http://www.open-open.com/lib/view/open1454683984651.html)

##IDE
- codeblocks
  ubuntu软件中心搜codeblock,一步安装
- clion
  
sudo mv jdk-8u45-linux-x64.tar.gz /usr/local  
&& cd /usr/local  
&& sudo tar -zxvf  jdk-8u45-linux-x64.tar.gz 

编辑环境脚本：sudo gedit /etc/profile，在文件尾部加入：
```
#cfg
JAVA_HOME=/usr/local/jdk1.8.0_45
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=.:$JAVA_HOME/bin/dt.jar:$JAVA_HOME/lib/tools.jar
export JAVA_HOME
export PATH
export CLASSPATH
```
注销或者重启后，输入java -version测试



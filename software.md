# 软件安装和配置
1.编译环境
##vm11虚拟机开启共享解决
```
cd ~
apt-get install git gcc make linux-headers-$(uname -r)
git clone https://github.com/rasa/vmware-tools-patches.git
cd vmware-tools-patches
./patched-open-vm-tools.sh
```

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

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-5 53 \
 --slave /usr/bin/g++ g++ /usr/bin/g++-5 \
 --slave /usr/bin/gcc-ar gcc-ar /usr/bin/gcc-ar-5 \
 --slave /usr/bin/gcc-nm gcc-nm /usr/bin/gcc-nm-5 \
 --slave /usr/bin/gcc-ranlib gcc-ranlib /usr/bin/gcc-ranlib-5
查看版本  gcc -v 如果显示是5.3就对了  
参考:  
[ubuntu升级gcc5](http://www.open-open.com/lib/view/open1454683984651.html)

##IDE CLion
  
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
解包Clion 进入其中bin目录，运行clion.sh
授权：
help->reg  
http://idea.qinxi1992.cn

clion很吃cpu和内存，使用的话，需要把处理器核心数至少提高到4，最好提高到8





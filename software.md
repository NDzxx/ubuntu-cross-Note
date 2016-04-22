# 软件安装和配置
1.编译环境

切换163源  
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
终于搞定。
sudo apt-get build-essential



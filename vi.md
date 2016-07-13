# vi

首先要进入命令模式(按ESC退出INSERT模式)
然后输入：/单词

cento 7安装
http://blog.csdn.net/weiguolong0306/article/details/50394219
http://www.cnblogs.com/rusking/p/4252774.html
cento 7镜像
http://www.centoscn.com/CentosSoft/iso/2016/0531/7330.html
Tiny Core Linux 7.1
http://www.centoscn.com/CentosSoft/linux/2016/0602/7358.html

https://segmentfault.com/a/1190000000735011
http://nareshv.blogspot.tw/2013/08/installing-dockerio-on-centos-64-64-bit.html
http://cn.soulmachine.me/blog/20131025/


    1、yum安装带aufs模块的3.10内核（或到这里下载kernel手动安装：http://down.51cto.com/data/1903250）
1
2
3
	
cd /etc/yum.repos.d 
wget http://www.hop5.in/yum/el6/hop5.repo
yum install kernel-ml-aufs kernel-ml-aufs-devel
带aufs模块的3.10内核下载后先使用gzip -dv命令解压，然后再使用rpm -ivh命令安装。安装好后，设置/etc/grub.conf里default=0，重启系统



http://www.iyunv.com/thread-126273-1-1.html
rpm -ivh kernel-ml-aufs-devel-3.10.5-3.el6.x86_64.rpm  

rpm -ivh kernel-ml-aufs-3.10.5-3.el6.x86_64.rpm  


http://blog.csdn.net/zhang__jiayu/article/details/43200685

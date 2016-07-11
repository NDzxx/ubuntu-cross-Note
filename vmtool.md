# 虚拟机工具安装
##配置网络  
 vim /etc/sysconfig/network-scripts/ifcfg-eth0   
 ONBOOT=yes　　　　　　　　　　#是否启动时运行   
 service network restart  
 ##安装虚拟机工具  
yum install perl gcc make kernel-headers kernel-devel -y  
cento 7需要安装  
yum install net-tools  

mount /dev/tmp ./tmp

/etc/vmware-tools/services.sh start
http://www.cnblogs.com/xyq/p/4068018.html





居然找不到Kernel header。

Searching for a valid kernel header path...
The path "" is not a valid path to the 3.10.0-229.4.2.el7.x86_64 kernel 
headers.

后来翻阅文档如下解决：

#yum install kernel-devel-3.10.0-229.4.2.el7.x86_64 -y
#cd /usr/src/kernels/
#ll
总用量 4
drwxr-xr-x. 22 root root 4096 6月   8 23:40 3.10.0-229.4.2.el7.x86_64

建立以下链接：

ln /usr/src/kernels/3.10.0-229.4.2.el7.x86_64/include/generated/uapi/linux/version.h  /usr/src/kernels/3.10.0-229.4.2.el7.x86_64/include/linux/version.h

再次安装，终于不报错了。

Searching for a valid kernel header path...
Detected the kernel headers at 
"/lib/modules/3.10.0-229.4.2.el7.x86_64/build/include".
The path "/lib/modules/3.10.0-229.4.2.el7.x86_64/build/include" appears to be a
valid path to the 3.10.0-229.4.2.el7.x86_64 kernel headers.
Would you like to change it? [no]

直接回车顺利完活。

http://blog.csdn.net/hang_zheng/article/details/41520271


# 虚拟机安装

用最小化镜像安装的时候，要选稍后安装操作系统  
安装过程如链接[cento安装](http://www.osyunwei.com/archives/7174.html)

安装中重要的是分区
- swap分区（虚拟内存）一定要设置，一般是设置成和内存大小相同，不然后面编译mysql gcc时候会内存不够而崩溃  
- boot分区200MB就够  
- 其余全部分配为/分区  

安装完毕后重启需要先配置网络  
vi /etc/sysconfig/network-scripts/ifcfg-eth0  
DEVICE=eth0　　　　　　　　　　#对应第一张网卡  
TYPE=Ethernet  
ONBOOT=yes　　　　　　　　　　#**是否启动时运行，注意这里由no改yes  **
NM_CONTROLLED=yes  


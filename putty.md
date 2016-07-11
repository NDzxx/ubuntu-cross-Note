# putty连接

yum install openssh-server  
chkconfig sshd on  
/etc/init.d/iptables stop  关闭防火墙，此处应该根据需要进行配置，虚拟机为求简单直接关闭  
chkconfig iptables off 永久关闭防火墙  


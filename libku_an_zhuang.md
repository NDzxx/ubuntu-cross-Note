# lib库安装
##curl  

yum -y install curl curl-devel  
##openssl  
 yum -y install openssl  
 
 yum -y install openssl-devel  
 
 ##Protobuf
 tar -zxvf protobuf.tar.gz  
 ./autogen.sh  
 ./configure --prefix=/usr    
    make    
    make check    
    make install    
  
 ldconfig  
yum -y install dos2unix yum install unix2dos  

 

##iconv
tar -zxvf libiconv-1.14.tar.gz  
./configure --prefix=/usr  
 make  
 make install  
 ldconfig
 
 ##复制lib库到本地
 安装locate  
 yum -y install mlocate  
 装好后 locate XX.so 查找出对应的路径  
 ls -l XX.so 如果是符号路径，后面会显示真正的文件路径  
 把所有的正确文件路径复制到/mnt/hgfs/share  
 在目标机上执行程序时候打开/etc/ld.so.conf,加入复制路径，然后ldconfig
 
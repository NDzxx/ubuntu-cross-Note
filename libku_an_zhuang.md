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
    
    
 
 


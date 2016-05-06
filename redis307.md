# redis3.0.7配置

tar zxvf redis-3.0.7.tar.gz  

cd redis-3.0.7  

如果不加参数,linux下会报错  
make MALLOC=libc  

make install  


mkdir /usr/redis  

cd redis-3.0.7/src  

cp redis-server  /usr/redis  

cp redis-benchmark /usr/redis  

cp redis-cli  /usr/redis  

mkdir /etc/redis  

cp ../redis.conf /etc/redis  

gedit /etc/redis/redis.conf  

查看bind 127.0.0.1是否被绑定，如果绑定，加个#注释掉
cd /usr/redis


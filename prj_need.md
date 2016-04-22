# 工程需要软件

##Redis
apt-get install redis-server

//修改配置文件
sudo gedit  /etc/redis/redis.conf  
找到bind 127.0.0.1 一行，前面加#  
如 ##bind 127.0.0.1

启动redis
sudo redis-server /etc/redis/redis.conf

关闭redis
redis-cli shutdown

客户端远程连接redis
使用RedisStudio-en-0.1.5 

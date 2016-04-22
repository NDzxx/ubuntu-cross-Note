# 工程需要软件

##Redis
apt-get install redis-server

//修改配置文件
sudo gedit  /etc/redis/redis.conf  
找到bind 127.0.0.1 一行，前面加#  
如 ##bind 127.0.0.1


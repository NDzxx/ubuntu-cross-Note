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

 ##mysql
- 安装

```
sudo apt-get install mysql-server
 
apt-get install mysql-client
 
sudo apt-get install libmysqlclient-dev
```
- 启动
```
sudo /etc/init.d/mysql start
```
- 停止
```
sudo /etc/init.d/mysql stop
```
- 重启
```
sudo /etc/init.d/mysql restart
```
- 查看日志  

```
cat /var/log/mysql.err
 
cat /var/log/mysql/error.log
```
- 远程连接
###授权
```
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'  
IDENTIFIED BY 'root'  WITH GRANT OPTION;
flush privileges;
```
###设置
```
sudo gedit  /etc/mysql/my.cnf
```
打开后注释掉 bind-address		= 127.0.0.1这一行
然后重启即可
- 连接测试
	```
    mysql -h 192.168.228.130 -u root -p root
    ```



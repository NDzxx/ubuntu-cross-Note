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

 ##mysql 5.7.9
 先查看是否有安装旧版mysql  
 mysql --version  
有的话按如下方式卸载  
sudo apt-get autoremove --purge mysql-server  
sudo apt-get remove mysql-server  
sudo apt-get autoremove mysql-server  
sudo apt-get remove mysql-common  
清理残留数据  

dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P  
 
将deb包解压出以下文件：

libmysqlclient20_5.7.9-1ubuntu14.04_amd64.deb

libmysqlclient-dev_5.7.9-1ubuntu14.04_amd64.deb

libmysqld-dev_5.7.9-1ubuntu14.04_amd64.deb  

mysql-community-client_5.7.9-1ubuntu14.04_amd64.deb

mysql-community-server_5.7.9-1ubuntu14.04_amd64.deb      

mysql-community-source_5.7.9-1ubuntu14.04_amd64.deb

mysql-client_5.7.9-1ubuntu14.04_amd64.deb         

mysql-community-test_5.7.9-1ubuntu14.04_amd64.deb

mysql-common_5.7.9-1ubuntu14.04_amd64.deb         

mysql-server_5.7.9-1ubuntu14.04_amd64.deb

mysql-community_5.7.9-1ubuntu14.04_amd64.changes  

mysql-testsuite_5.7.9-1ubuntu14.04_amd64.deb

4,更新设置到最新系统：
apt-get install libaio1
5,然后分别安装以下的包：
sudo dpkg -i mysql-common_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg-preconfigure mysql-community-server_5.7.9-1ubuntu14.04_amd64.deb  

此步需要输入数据的root密码  

sudo dpkg -i libmysqlclient20_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg -i libmysqlclient-dev_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg -i libmysqld-dev_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg -i mysql-community-client_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg -i mysql-client_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg -i mysql-common_5.7.9-1ubuntu14.04_amd64.deb  

sudo apt-get -f install  
5,此步为了安装依赖包 libmecab2  
sudo apt-get install libmecab2  
sudo dpkg -i mysql-community-server_5.7.9-1ubuntu14.04_amd64.deb  
sudo dpkg -i mysql-server_5.7.9-1ubuntu14.04_amd64.deb  

6,这时数据安装完成，并自动启动


这时你会发现 mysql以服务形式自启动
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
GRANT ALL PRIVILEGES ON *.* TO '用户名'@'host'IDENTIFIED BY '密码'  WITH GRANT OPTION;
举个例子
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.224.116' IDENTIFIED BY 'root'  WITH GRANT OPTION;
这时如果出错，输入
ALTER TABLE `user` ADD `Create_tablespace_priv` ENUM('N','Y') NOT NULL DEFAULT 'N' AFTER `Trigger_priv`; 
ALTER TABLE `user` ADD `plugin` CHAR(64) NULL AFTER `max_user_connections`; 
ALTER TABLE `user` ADD `authentication_string` TEXT NULL DEFAULT NULL AFTER `plugin`;
ALTER TABLE `user` ADD `password_expired` ENUM('N','Y') NOT NULL DEFAULT 'N' AFTER `authentication_string`;
#然后再次运行授权
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.224.116' IDENTIFIED BY 'root'  WITH GRANT OPTION;
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
    mysql -h 192.168.228.132 -u root -p root
    ```



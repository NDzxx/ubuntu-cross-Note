# cento下mysql安装
##安装依赖，必须先升级gcc5.3  

yum install -y ncurses-devel libstdc++*  libtool cmake lrzsz libaio-devel

tar -zxvf mysql-5.7.9

cd mysql-5.7.9

mkdir -p /data/mysql

mkdir zxxbuild

cd zxxbuild

cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local/mysql -DMYSQL_DATADIR=/data/mysql -DSYSCONFDIR=/etc -DWITH_INNOBASE_STORAGE_ENGINE=1 -DWITH_PERFSCHEMA_STORAGE_ENGINE=1 -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DMYSQL_UNIX_ADDR=/data/mysql/tmp/mysql.sock -DENABLED_LOCAL_INFILE=ON -DENABLED_PROFILING=ON -DWITH_DEBUG=0 -DENABLE_DTRACE=OFF -DMYSQL_TCP_PORT=3306 -DDOWNLOAD_BOOST=1 -DWITH_BOOST=../boost_1_59_0

make && make install

##配置

groupadd mysql

useradd -r -g mysql mysql

chown -R mysql .
chgrp -R mysql .

cd /usr/local/mysql/bin

 ./mysqld --initialize-insecure --user=mysql --basedir=/usr/local/mysql --datadir=/data/mysql
 
  chown -R root .

cd /usr/local/mysql/support-files  
cp my-default.cnf /etc/my.cnf    
复制完毕后gedit /etc/my.cnf 查看下bind 127.0.0.1前面是否有#，没有补上#
cp /usr/local/mysql/support-files/mysql.server /etc/init.d/mysql   、

chmod 755 /etc/init.d/mysql   

gedit /etc/profile
补充：
```
PATH=/usr/local/mysql/bin:$PATH 

export PATH
```

source /etc/profile

修改root密码
cd /usr/local/mysql/bin  

mysqladmin -u root password "你的密码"  

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
##远程连接
###授权

GRANT ALL PRIVILEGES ON *.* TO '用户名'@'host'IDENTIFIED BY '密码'  WITH GRANT OPTION;  
举个例子  
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.224.116' IDENTIFIED BY 'root'  WITH GRANT OPTION;  
这时如果出错，输入  
ALTER TABLE `user` ADD `Create_tablespace_priv` ENUM('N','Y') NOT NULL DEFAULT 'N' AFTER `Trigger_priv`;   
ALTER TABLE `user` ADD `plugin` CHAR(64) NULL AFTER `max_user_connections`;   
ALTER TABLE `user` ADD `authentication_string` TEXT NULL DEFAULT NULL AFTER `plugin`;  
ALTER TABLE `user` ADD `password_expired` ENUM('N','Y') NOT NULL DEFAULT 'N' AFTER `authentication_string`;  
然后再次运行授权
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.224.116' IDENTIFIED BY 'root'  WITH GRANT OPTION;  
flush privileges;  

##防火墙
/etc/init.d/iptables status

如果得到一系列信息，说明防火墙开着。

/etc/init.d/iptables stop  关闭防火墙，此处应该根据需要进行配置，虚拟机为求简单直接关闭

cp support-files/mysql.server /etc/init.d/mysqld
chkconfig --add mysqld
service mysqld start
chkconfig --level 345 mysqld on 
###设置
```
sudo gedit  /etc/mysql/my.cnf
```
打开后注释掉 bind-address		= 127.0.0.1这一行
然后重启即可
- 连接测试
```
    打开win命令行
    mysql -h 192.168.228.132 -u root -p root
```
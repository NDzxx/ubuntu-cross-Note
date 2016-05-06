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

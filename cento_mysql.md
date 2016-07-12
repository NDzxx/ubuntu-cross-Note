# cento下mysql安装

## 安装依赖，必须先升级gcc5.3

[http:\/\/www.tuicool.com\/articles\/BRzINfA](http://www.tuicool.com/articles/BRzINfA) 

yum install -y ncurses-devel  libtool lrzsz libaio-devel ncurses ncurses-devel
参考链接：[ CentOS7安装MYSQL5.7.9 ](http://wenku.baidu.com/link?url=8QN-xd0Fk0VE4n-jHW8OlWVf6Iydx-cZzkWOEITE7lpr9E1CTcMRUlUNcr_JnW3-cwOXn7GN8EP5KF9MhKAztCHm_BaKqavDNTOgNphUvxm)  
tar -zxvf mysql-5.7.9

cd mysql-5.7.9

mkdir -p \/usr\/local\/mysql
mkdir -p \/usr\/local\/mysql\/data

mkdir zxxbuild

cd zxxbuild

cmake .. -DCMAKE\_INSTALL\_PREFIX=\/usr\/local\/mysql -DMYSQL\_DATADIR=\/usr\/local\/mysql\/data -DSYSCONFDIR=\/etc -DWITH\_INNOBASE\_STORAGE\_ENGINE=1 -DWITH\_PERFSCHEMA\_STORAGE\_ENGINE=1 -DDEFAULT\_CHARSET=utf8 -DDEFAULT\_COLLATION=utf8\_general\_ci -DMYSQL\_UNIX\_ADDR=\/usr\/local\/mysql\/tmp\/mysql.sock -DENABLED\_LOCAL\_INFILE=ON -DENABLED\_PROFILING=ON -DWITH\_DEBUG=0 -DENABLE\_DTRACE=OFF -DMYSQL\_TCP\_PORT=3306 -DDOWNLOAD\_BOOST=1 -DWITH\_BOOST=..\/boost\_1\_59\_0

make && make install

## 配置

groupadd mysql

useradd -r -g mysql mysql

chown -R mysql .  
chgrp -R mysql .

cd \/usr\/local\/mysql\/bin

.\/mysqld --initialize-insecure --user=mysql --basedir=\/usr\/local\/mysql --datadir=\/usr\/local\/mysql\/data

chown -R root .  
  chown -R mysql \/usr\/local\/mysql\/data

cd \/usr\/local\/mysql\/support-files   
mv \/etc\/my.cnf my.cnf.bak   
cp my-default.cnf \/etc\/my.cnf    
复制完毕后gedit \/etc\/my.cnf 查看下bind 127.0.0.1前面是否有\#，没有补上\#
cp \/usr\/local\/mysql\/support-files\/mysql.server \/etc\/init.d\/mysql

chmod 755 \/etc\/init.d\/mysql

chkconfig --add mysql …加入自动启动项

chkconfig --level 345 mysql on …设置MySQL在345等级自动启动

chkconfig --list   
把服务文件放到\/etc\/init.d\/目录下面相当于改为了rpm包安装的服务使用方式。

gedit \/etc\/profile
补充：

```
PATH=/usr/local/mysql/bin:$PATH 

export PATH
```

source \/etc\/profile

## 启动mysql服务

* 启动
  ```
  sudo /etc/init.d/mysql start
  ```

* 停止
  ```
  sudo /etc/init.d/mysql stop
  ```

* 重启
  ```
  sudo /etc/init.d/mysql restart
  ```


修改root密码  
cd \/usr\/local\/mysql\/bin

mysqladmin -u root password "你的密码"

## 远程连接

### 授权

GRANT ALL PRIVILEGES ON _._ TO '用户名'@'host'IDENTIFIED BY '密码'  WITH GRANT OPTION;  
举个例子  
GRANT ALL PRIVILEGES ON _._ TO 'root'@'192.168.224.116' IDENTIFIED BY 'root'  WITH GRANT OPTION;

这时如果出错，输入  
ALTER TABLE `user` ADD `Create_tablespace_priv` ENUM\('N','Y'\) NOT NULL DEFAULT 'N' AFTER `Trigger_priv`;   
ALTER TABLE `user` ADD `plugin` CHAR\(64\) NULL AFTER `max_user_connections`;   
ALTER TABLE `user` ADD `authentication_string` TEXT NULL DEFAULT NULL AFTER `plugin`;  
ALTER TABLE `user` ADD `password_expired` ENUM\('N','Y'\) NOT NULL DEFAULT 'N' AFTER `authentication_string`;  
然后再次运行授权  
GRANT ALL PRIVILEGES ON _._ TO 'root'@'192.168.224.116' IDENTIFIED BY 'root'  WITH GRANT OPTION;  
flush privileges;

## 防火墙

\/etc\/init.d\/iptables status

如果得到一系列信息，说明防火墙开着。

\/etc\/init.d\/iptables stop  关闭防火墙，此处应该根据需要进行配置，虚拟机为求简单直接关闭
chkconfig iptables off 永久关闭防火墙

### 设置

```
sudo gedit  /etc/mysql/my.cnf
```

打开后注释掉 bind-address        = 127.0.0.1这一行
然后重启即可

* 连接测试
  ```
    打开win命令行
    mysql -h 192.168.228.132 -u root -p root
  ```

  ## linux下运行mysql文件

  source 路径\/XX.sql

## mysql Error 1130问题的解决方案

远程连接mysql数据库的时候，报错：出现 ERROR 1130 \(HY000\): Host '117.79.246.\*'is not allowed to connect to this MySQL server提示信息，不能远程连接数据库。

解决方案如下：  
  这个时候只要在localhost的那台电脑，登入mysql后，更改 "mysql" 数据库里的 "user" 表里的 "host" 项，从"localhost"改称"%"

mysql -u root -p  
mysql&gt;use mysql;  
mysql&gt;update user set host = '%' where user = 'root';  
\/\/这个命令执行错误时，可能会报ERROR 1062 \(23000\): Duplicate entry '%-root' for key 1；这个错误，不用管它。  
mysql&gt;flush privileges;  
mysql&gt;select host, user from user;


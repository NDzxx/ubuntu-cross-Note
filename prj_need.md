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


附2：把Redis作为Linux服务开机启动

这里只提供一种最简单的方式，最好的是通过编写开机启动脚本来做。

如果要开机启动redis，我们需要把redis设置为daemon后台启动（如果不设置 为后台启动，则linux启动后图形界面会卡在一个空白的页面），而redis只有1个启动参数，就是redis的配置文件路径。redis的默认配置文 件redis.conf位于redis的安装目录下。我们可以把该文件copy到/etc目录下
Shell代码 收藏代码

    [root@localhost redis- 2.6. 14]# cp redis.conf /etc/  

redis的默认配置文件中daemonize参数的值为no，代表为非后台启动，所以我们需要把该参数的值修改为yes。至于其它的参数在这里就不详细说了，具体可以参见： http://blog.csdn.net/htofly/article/details/7686436

修改完daemonize参数之后，redis就能够通过daemon方式启动了，那么下一步就是把redis加入到linux开机启动服务配置中了，具体步骤如下：

使用VI编辑器打开Linux开机启动服务配置文件/etc/rc.local，并在其中加入下面的一行代码：
Shell代码 收藏代码

/usr/local/redis-2.6.14/src/redis-server /etc/redis.conf

编辑完后保存，然后重启系统就OK了。 

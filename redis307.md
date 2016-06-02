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

开机自启动
```
# chkconfig:   2345 90 10
# description:  Redis is a persistent key-value database
PATH=/usr/local/bin:/sbin:/usr/bin:/bin
REDISPORT=6379
EXEC=/usr/local/bin/redis-server
REDIS_CLI=/usr/local/bin/redis-cli
PIDFILE=/var/run/redis.pid
CONF="/etc/redis.conf"
case "$1" in
start)
if [ -f $PIDFILE ]
then
echo "$PIDFILE exists, process is already running or crashed"
else
echo "Starting Redis server..."
$EXEC $CONF
fi
if [ "$?"="0" ] 
then
echo "Redis is running..."
fi
;;
stop)
if [ ! -f $PIDFILE ]
then
echo "$PIDFILE does not exist, process is not running"
else
PID=$(cat $PIDFILE)
echo "Stopping ..."
$REDIS_CLI -p $REDISPORT SHUTDOWN
while [ -x ${PIDFILE} ]
do
echo "Waiting for Redis to shutdown ..."
sleep 1
done
echo "Redis stopped"
fi
;;
restart|force-reload)
${0} stop
${0} start
;;
*)
echo "Usage: /etc/init.d/redis {start|stop|restart|force-reload}" >&2
exit 1
esac
```
sudo chkconfig redis on
启动redis
sudo redis-server /etc/redis/redis.conf

关闭redis
redis-cli shutdown

客户端远程连接redis
使用RedisStudio-en-0.1.5 


#mysql和redis的使用
##mysql

删除所有容器
docker rm $(docker ps -a -q) 

mysql运行
docker run --name vm_mysql -v /home/zxx/ftp/BoxAcc/mysql_data:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -d docker.io/mysql:latest

连接到mysql
 docker exec -it  vm_mysql  bash 
   
redis运行  

网易蜂巢redis使用( https://c.163.com/hub#/m/repository/?repoId=2973) 


docker run --name redis -d redis redis-server 
dockerfile  
```
FROM docker.io/centos:latest
ADD cs405 /usr/bin
RUN cs405
```

 docker run --name redis -v /home/zxx/ftp/BoxAcc/redisData:/data -p 6379:6379 -d hub.c.163.com/library/redis:latest redis-server --appendonly yes  

##boxacc 连接mysql 和redis
```
 docker run -t -i --name boxacc -v /home/zxx/ftp/BoxAcc/syslog:/usr/BoxAccount0.50/syslog 
-v /home/zxx/ftp/BoxAcc/dump:/usr/BoxAccount0.50/dumps 
--link vm_mysql:mysql  
--link redis:redis
boxacc:latest /bin/bash   
```

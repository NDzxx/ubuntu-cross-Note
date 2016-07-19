#mysql和redis的使用
##mysql

删除所有容器
docker rm $(docker ps -a -q) 


docker run --name mysql -v /home/zxx/ftp/BoxAcc/mysql_data:/var/lib/mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root -d docker.io/mysql:latest
 
dockerfile  
```
FROM docker.io/centos:latest
ADD cs405 /usr/bin
RUN cs405
```

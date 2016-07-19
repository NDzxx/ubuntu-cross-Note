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




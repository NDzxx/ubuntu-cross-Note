#mysql和redis的使用
##mysql

删除所有容器
docker rm $(docker ps -a -q) 

dockerfile  
```
FROM docker.io/centos:latest
ADD cs405 /usr/bin
RUN cs405
```

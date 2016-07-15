##docker相关文档
##安装

ceno7安装docker

yum install -y docker

配置开机启动

systemctl enable docker.service

启动服务

systemctl start docker.service  
##下载镜像

###网易蜂巢加速
 配置镜像加速   

- Ubuntu | Debian | Centos    

``` 
 $ sudo echo "DOCKER_OPTS=\"\$DOCKER_OPTS --registry-mirror=http://hub
-mirror.c.163.com\"" >> /etc/default/docker
 $ service docker restart 
``` 
-  Windows  

启动 Boot2docker Start Shell：  
```
$ sudo "sh -c \"echo EXTRA_ARGS=\'--registry-mirror=http://hub-mirror.c.163.com\' 
>>/var/lib/boot2docker/profile\""

```  
- Mac  

```
$ boot2docker ssh sudo "sh -c \"echo EXTRA_ARGS=\'--registry-mirror=http://hub-
mirror.c.163.com\' >>/var/lib/boot2docker/profile\"" 
$ boot2docker restart
```
###使用
配置完成后，直接  
```
docker pull ubuntu:14.04
```

##管理镜像
- 查看信息  

```
docker images
```
- 删除镜像  
```
docker rm vecId(依赖容器id)
docker rmi imgId(镜像id)
```
- 创建镜像  

在对应应用同一个文件夹下建立dockefile







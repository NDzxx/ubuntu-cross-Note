# docker
##任务分解和测试
1.虚拟机上docker安装  
2.docker加载镜像测试  
3.docker分别加载boxAcc redis mysql三个镜像并连接  
4.可以使用后使用Docker Compose
5.后续发展 kubernetes????

cento 6.5最小化安装  
http://mirrors.163.com/centos/6.5/isos/x86_64/CentOS-6.5-x86_64-minimal.iso
因为docker最少必须cento6.5

CentOS6.5安装Docker
http://www.open-open.com/lib/view/open1418476266886.html  

https://segmentfault.com/a/1190000000735011  
docker运行mysql并连接  
http://www.open-open.com/lib/view/open1464340715630.html  
http://blog.csdn.net/kongxx/article/details/38676917  
国内网易云仓库    
https://c.163.com/hub#/m/home/  
mysql 5.7.11镜像  
https://c.163.com/hub#/m/repository/?repoId=2955  
docker pull hub.c.163.com/library/mysql:5.7.11
Redis  
https://c.163.com/hub#/m/repository/?repoId=2973
docker pull hub.c.163.com/library/redis:3.0.7
cento 6.5镜像
docker pull hub.c.163.com/public/centos:6.5

dockerFile教程
https://segmentfault.com/a/1190000002711357  

http://www.tuicool.com/articles/IruAJnF

可以考虑使用的创新应用  
http://www.pc.nd/index.php?doc-view-39752-docker%2C  
因此我们使用Docker Compose来解决我们所遇到的问题。

1、安装Docker Compose

pip install -U docker-compose==1.4.02、使用docker-compose.yml来定义你的应用。
redis:
  image: redis
  ports:
   - "6379:6379"
elasticsearch:
  image: caofb/elasticsearch
  ports:
   - "9200:9200"

3、运行docker compose

docker-compose up

使用Docker Compose
http://debugo.com/docker-compose/

联网解决方案  
http://cloud.51cto.com/art/201502/465958.htm
docker使用  
https://linux.cn/article-5304-1.html
  
docker容器内应用程序退出  
http://www.tuicool.com/articles/vyyaYv  

僵尸进程？？  
http://www.oschina.net/translate/docker-and-the-pid-1-zombie-reaping-problem
容器使用注意10个事  
http://www.oschina.net/translate/10-things-to-avoid-in-docker-containers
使用supervisor运行多进程Docker容器 可解决僵尸进程  
http://www.tuicool.com/articles/i6fuuyV  
http://blog.liuker.cn/index.php/docker/32.html  
kubernetes1  
https://www.ustack.com/blog/kubernetes1/  
http://www.csdn.net/article/2014-10-31/2822393
docker UI?
http://os.51cto.com/art/201411/456204.htm

# compose安装和使用

## 安装

```shell
 curl -O https://bootstrap.pypa.io/get-pip.py

 python get-pip.py

 pip install -U docker-compose

```

## docker-compose.yml编写

```
mysql:

 image: docker.io/mysql:latest

 ports:

 - "3306:3306"

 volumes:

 - /home/zxx/ftp/BoxAcc/mysql_data:/var/lib/mysql

 environment:

 - /home/zxx/ftp/BoxAcc/mysql_data:/var/lib/mysql

 container_name: vm_mysql

vec_webserver:

 image: bench_webserver:latest

 container_name: bench_webserver

 ports:

 - "6820:6820"

 volumes:

 - /home/zxx/ftp/web/log:/usr/bench_webserver/log

 links:

 - mysql

```


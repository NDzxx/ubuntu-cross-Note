# docker安装

##查看内核和版本
```
[root@localhost ~]# uname -r
2.6.32-431.el6.x86_64

[root@localhost ~]# cat /etc/issue
CentOS release 6.5 (Final)
Kernel \r on an \m
```
##安装  
```
[root@localhost ~]# rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
Retrieving http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
warning: /var/tmp/rpm-tmp.JN76fI: Header V3 RSA/SHA256 Signature, key ID 0608b895: NOKEY
Preparing...                ########################################### [100%]
   1:epel-release           ########################################### [100%]
[root@localhost ~]# rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6

[root@localhost ~]# yum -y install docker-io
[root@localhost ~]# yum upgrade device-mapper-libs
[root@localhost ~]# service docker restart
[root@localhost ~]# chkconfig docker on

```
安装镜像
```
#cento 6.5镜像
docker pull hub.c.163.com/public/centos:6.5
#redis镜像
docker pull hub.c.163.com/library/redis:3.0.7
#mysql 5.7.11镜像  
docker pull hub.c.163.com/library/mysql:5.7.11


http://blog.csdn.net/wuzhilon88/article/details/41621285/

```  




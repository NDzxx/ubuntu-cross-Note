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
```
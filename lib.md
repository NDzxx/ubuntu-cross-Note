# lib
##curl 和openssl
sudo apt-get install curl

sudo apt-get install libcurl4-openssl-dev  



##protobuf

下载源码

首先，从github上下载protobuf的源码，github的地址：https://github.com/google/protobuf

shell>git clone https://github.com/google/protobuf.git
编译异常处理

现在，我们基本上可以按照github上的编译步骤进行操作，但是，有两点需要注意

1.我们现在是使用的源码构建，必须切换到合适的release版本。

[plain] view plain copy

    git tag  
    git checkout v2.6.1  

2.你会发现按照github上面编译，第一步就报错。

查看脚本的内容，它去下载一个google的gtest的东西，因为“众所周知”的原因，下载失败，造成不能生成configure文件。这个时候，可以手动去网络上下载这个zip包，解压，并且重命名为gtest。就可以继续编译了。

我的资源中上传了一个（由于写文章时，尚未审批，无法给出地址），大家可以自行下载，百度也很容易百度到。下面给出操作步骤

[plain] view plain copy
在CODE上查看代码片派生到我的代码片

    unzip gtest-1.7.0.zip  
    mv gtest-1.7.0 gtest  
    ./autogen.sh  

编译安装

经过上面的操作就能生成configure文件了。就可以按照github上面的步骤正常编译了

[plain] view plain copy
在CODE上查看代码片派生到我的代码片

    ./configure --prefix=/usr  
    make  
    make check  
    make install  

这个时候编译安装就已经完成了。
ldconfig
yum -y install dos2unix yum install unix2dos
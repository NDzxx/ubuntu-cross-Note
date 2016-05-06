# Cento安装

su root  
##升级gcc 5  
yum -y install gcc gcc-c++ kernel-devel wget  
配置和编译安装  
tar -jxvf gcc-5.3.0.tar.bz2  

cd gcc-5.3.0

./contrib/download_prerequisites　

mkdir gcc-build-5.3.0

cd gcc-build-5.3.0/

yum -y install glibc-devel.i686 glibc-devel

../configure -enable-checking=release -enable-languages=c,c++ -disable-multilib

make -j4

make install

##升级glibc 2.12到2.19
原因:ubuntu14.04lts 是glibc 2.19，为了兼容两个版本，升级cento glibc

###autoconf的安装
tar -zxvf autoconf-2.69.tar.gz

mkdir build

cd build

../configure --prefix=/usr

make && make install

##更新glibc 2.19
tar -xvf glibc-2.19.tar

cd glibc-2.19

mkdir build

cd build

../configure –prefix=/usr –disable-profile –enable-add-ons –with-headers=/usr/include –with-binutils=/usr/bin

make && make install




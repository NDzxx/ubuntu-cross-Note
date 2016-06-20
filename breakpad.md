# breakPad

下载地址：https://chromium.googlesource.com/breakpad/breakpad   
git clone https://chromium.googlesource.com/breakpad/breakpad

linux下编译
# Configure
./configure
# Build
make
 
win下编译
1.安装python2.x版本(python3.x版本将出现错误)

2.在命令行控制台进入src/tools/gyp目录

3.运行 > gyp.bat "../../client/windows/breakpad_client.gyp"

4.编译上一步生成的解决方案 src/client/windows/breakpad_client.sln

5.OK,完事

参考文章[breapad在c++11下编译错误](http://blog.csdn.net/brook0344/article/details/25308653)

程序减肥
http://blog.chinaunix.net/uid-24774106-id-3526766.html
1.release版本打包-g 然后用strip去除调试信息的版本发布，保留调试信息的版本用来备份，万一有错，可以使用带调试信息的版本查看到行号

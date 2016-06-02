# breakPad

下载地址：https://chromium.googlesource.com/breakpad/breakpad
git clone https://chromium.googlesource.com/breakpad/breakpad

linux下编译
 ./configure
  make
 
win下编译
1.安装python2.x版本(python3.x版本将出现错误)

2.在命令行控制台进入src/tools/gyp目录

3.运行 > gyp.bat "../../client/windows/breakpad_client.gyp"

4.编译上一步生成的解决方案 src/client/windows/breakpad_client.sln

5.OK,完事

参考文章[breapad在c++11下编译错误](http://blog.csdn.net/brook0344/article/details/25308653)

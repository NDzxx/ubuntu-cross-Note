# eclipse

 Linux 平台下用CMake搭建Eclipse CDT工程 2012-07-25 22:46:11

分类： C/C++

1、项目目录规划

    在project_dir下建立build, cmake, src三个目录。


2、编写CMakeLists.txt文件。


3、调用CMake命令为eclipse生成项目文件

点击(此处)折叠或打开

    mkdir -p build/release

    mkdir -p build/debug

    cmake -E chdir build/release cmake -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=release ../../

    cmake -E chdir build/debug cmake -G "Eclipse CDT4 - Unix Makefiles" -DCMAKE_BUILD_TYPE=debug ../../


4、打开eclipse
a. 选择菜单：
File->Import->General->Existing Projects into Workspace
b. 点击 “Next”，在 Select root directory 选择目录为project_dir/build
Eclipse会自动搜索到debug, release两个目录下的项目。
c. 点击“Finish”按钮。eclipse将自动加入项目。

5. 剩下的就是使用Eclipse CDT 调试程序了。

bless all
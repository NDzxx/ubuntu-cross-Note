# breakPad

http://www.cnblogs.com/catch/archive/2013/02/02/2882016.html

google breakpad 是一个开源的跨平台崩溃堆栈日志生成库, google breakpad包含3个组成部分: 

1.集成到程序中,当发生崩溃时生成dmp文件的breakpad client模块;

2.从应用程序中提取符号信息的breakpad symbol dumper模块;

3.利用符号文件和dmp文件解析崩溃堆栈的breadpad minidump processor模块;

为了跨平台, breakpad 对崩溃处理进行了这3个抽象. 但是具体到windows平台, 它所生成的是标准的windows dump文件, 直接双击即可打开用调试器查看.

这里记录一下64位 windows版本的集成步骤, 使用的是Visual Studio 2008 x64开发环境

下载好源码后,首先是建立windows library工程, 包含的源码文件如截图所示 

修改工程配置 
添加头文件包含路径: 路径为解压源码后的src文件夹 
设置预定义宏为: WIN32;NDEBUG;_LIB;_WINDOWS;_HAS_EXCEPTIONS=0;NOMINMAX;_CRT_RAND_S;CERT_CHAIN_PARA_HAS_EXTRA_FIELDS;WIN32_LEAN_AND_MEAN;_SECURE_ATL;_HAS_TR1=0;_CRT_SECURE_NO_DEPRECATE;_CRT_NONSTDC_NO_WARNINGS;_CRT_NONSTDC_NO_DEPRECATE;NO_TCMALLOC;NVALGRIND
编译完成后, 添加到宿主应用程序中 
包含头文件: #include "client/windows/handler/exception_handler.h" 
链接 libbreadpad.lib 
在应用程序入口处执行以下代码: 
google_breakpad::ExceptionHandler *pHandler = new google_breakpad::ExceptionHandler(
  ".\syslog",
  0,
  MinidumpCallback,
  0,
  google_breakpad::ExceptionHandler::HANDLER_ALL,
  MiniDumpNormal,
  L"",
  0 );
其中 MinidumpCallback 是发生崩溃, 生成日志后的回调函数, 定义如下, 可根据项目需要修改:

bool MinidumpCallback(const wchar_t* dump_path, const wchar_t* minidump_id, void* context, EXCEPTION_POINTERS* exinfo, MDRawAssertionInfo* assertion, bool succeeded)
{
 // 获取当前exe路径
 wchar_t szFilePath[MAX_PATH + 1];
 GetModuleFileNameW(NULL, szFilePath, MAX_PATH);
 (wcsrchr(szFilePath, L'\\'))[1] = 0;

 std::wstring file_name = szFilePath;
 file_name += SYS_LOG;
 file_name += minidump_id;
 file_name += L".txt";

 FILE* f = _wfopen(file_name.c_str(), L"w");
 // 写入当前系统时间
 SYSTEMTIME sys;
 GetLocalTime(&sys);
 wsprintf(szFilePath, L"%4d-%02d-%02d %02d:%02d:%02d.%03d",sys.wYear, sys.wMonth, sys.wDay, sys.wHour, sys.wMinute, sys.wSecond, sys.wMilliseconds);
 fwrite((const char*)szFilePath, wcslen(szFilePath), sizeof(wchar_t), f);

 fclose(f);
 return true;
}

注意事项: 在创建ExceptionHandler对象的时候,需要指定崩溃日志生成目录, 这个目录必须预先创建好,否则不会生成崩溃日志. 可以在初始化阶段检查一下要指定的目录,如果不存在则创建一下即可
if((_access(BREAKPAD_DIR, 0)) == -1)
 {
  int saved_errno = errno;
  if (saved_errno == ENOENT)
  {
   if (_mkdir(BREAKPAD_DIR) == -1)
   {
    saved_errno = errno;
    fprintf(stderr, "mkdir error: %s\n", strerror(saved_errno));
    exit(EXIT_FAILURE);
   }
  }
  else
  {
   fprintf(stderr, "_access error: %s\n", strerror(saved_errno));
   exit(EXIT_FAILURE);
  }
 } 
为了便于下载到dmp文件后,可以方便的知道对应崩溃发生的时间,可以在发生崩溃触发回调的时候记录一下时间,参看上面的 MinidumpCallback 代码,传入的minidump_id参数就是当前生成的崩溃日志文件名.

# 调试Release发布版程序的Crash错误(转)

调试minidump

    调试dump文件首先需要pdb文件，因此我们build程序时需要设置 Debug Infomation Format 为 “Program Database（/Zi）”。其次，我们还要确保所用的dump文件与源代码、exe、pdb文件版本是一致的，这要求我们必须维护好程序版本信息。

    调试minidump最方便的环境就是VS了，我们只要将.dmp、.exe、.pdb文件放在一个路径下，保证源代码文件的路径与编译时的路径一致就可以了，剩下的就是VS帮我们完成。双击.dmp文件或者在文件打开工程中选择“dump files”，加载dump文件，然后按F5运行就能直接恢复crash时的现场了，你可以定位crash的代码，可以查看调用堆栈，可以查看线程和模块信息...一切都跟你设置断点调试一样，太强大了！看个截图吧。

  方案六：minidump + email

    我们只需要在异常处理时，先生成minidump信息文件，再用email方式将文件发送到指定邮箱就行了。剩下的就是我们每天查看邮箱，提取dump文件进行调试了。

    1、Email功能

    首先我们来看一下email发送都需要哪些相关信息。

    a、发送端邮箱帐户；

    b、接收端邮箱帐户；

    c、email标题，一般应有软件名称及版本信息；

    d、email正文，一般应有简单的crash信息提示，以区别不同原因造成的crash；

    e、email附件，当然就是我们的dump文件了，还可以加上软件生成的log文件等。

    当然，对于标题应该尽量多加一些信息区别引起crash的原因，比如将crash的地址信息加到标题中；因为当每天有成百上千的crash汇报上来，重复的crash占大多数，把时间都花在区分它们身上有点太浪费。由此看来，前面方案中提到的StackWalker还是有些用处的，我们可以用它来生成一些crash的文字描述信息，写到标题或正文中去。

    dump文件的大小是否适合作为邮件的附件呢？实际上minidump产生的文件一般在几K到几十K之间，作为email的附件没有任何问题。
email的使用
http://blog.sina.com.cn/s/blog_48f93b530100esmg.html
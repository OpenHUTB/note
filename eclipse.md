


（*）Eclipse调试Matlab的mex文件：https://ww2.mathworks.cn/matlabcentral/answers/241291-how-to-debug-mex-file-compiled-with-mingw64-and-g-flags
（*）Eclipse附到Matlab进程上报错： Error message from debugger back end: ptrace: Operation not permitted
原因：不能使用gdb附到到自己的进程上（gdb使用root却可以）
解决：sudo chmod +s /usr/bin/gdb  （为文件加上setuid标志。执行的时候提升权限，比如这个文件是root的，那么一个普通用户执行这个程序的时候它的权限相当于root，这样就可以读写一些只有root才有权限的文件了）
永久解决：echo 0 > /proc/sys/kernel/yama/ptrace_scope
或者将 /etc/sysctl.d/10-ptrace.conf 文件中的ptrace_scope设置为0
PTRACE为0表示更加宽松的模式，为1只是对直接的子进程
https://blog.mellenthin.de/archives/2010/10/18/gdb-attach-fails-with-ptrace-operation-not-permitted/
（*）在断点处不能停止
原因：（1）mex需要加上-g选项；（2）前面调试过一次，需要重新启动Eclipse


安装JDT: 选择所有“可用软件点”->programming languages -> Eclipse Java Development Tools

Q：运行Java程序出现：An internal error occurred during: "Add Deployment". java.lang.NullPointException
A：把项目配置的Java运行版本从1.9降低到1.8


同步本地和远程目录插件：http://rsyncplugin.sourceforge.net/index.html
filesync

Eclipse IDE 项目资源中心：https://www.ibm.com/developerworks/cn/eclipse/index.html

CDT: http://download.eclipse.org/tools/cdt/releases/9.3

用于Wolfram 语言的基于 Eclipse 的集成开发环境： http://www.wolfram.com/workbench/

Q:Remote Systems连接FTP服务器报错：vsftpd 530 Login incorrect
A:用户名默认使用了本地的用户名haidong.wang，右键FTP连接的属性，修改Default User ID为wanghaidong。



技巧****************************************************************************
Eclipse源代码：http://download.eclipse.org/eclipse/downloads
git地址：http://git.eclipse.org/c/platform/
Eclipse-SDK包含源代码

快捷键提示插件MouseFeed

自动补全：Window -> Preferences -> PHP(Java)/Editor/Content Assist，Auto activation delay降低（例如说降低到0或者100ms）
Autocomplete Trigger for Java"配置为：.(abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ

删除注释：Ctrl+F -> Regular expressions
(^\s*\/\*\*)|(^\s*\*.*)     Replace All   /* *
\/\/.*                  // 后面的所有注释
^\s*\n              替换所有空行

打开文件所在文件夹：（ 插件 Eclipse Explorer   4.1.0.201606201109  cn.ieclipse.pde.explorer.feature.feature.group  ieclipse.cn；快捷键Ctrl+`）
先配置一个External Tool
Run--&gt;External Tools--&gt;Open External Tools Dialog... 
新建一个 program 
location 里面填 ：C:\WINDOWS\explorer.exe 
Arguments 里面填: ${container_loc}



快捷键****************************************************************************
Ctrl + shift +g 查找所以光标所在类型出现的位置
Ctrl +f6 编辑器之间切换

快捷键总结
http://blog.csdn.net/zhengqiqiqinqin/article/details/9163969
Auto Activation triggers for java: http://www.cnblogs.com/mq0036/p/4995390.html

跳转到函数定义F3，往回跳alt+left
字体放大缩小：ctrl+shift++ {-}
转至上一个编辑位置：Ctrl+Q
打开结构：Ctrl+F3
下一个编辑器(Next Editor)：Ctrl+F6
下一个透视图(Next Page)：Ctrl+F8
下一个视图(Next Perspective)：Ctrl+F7

插件
数据库客户端：DBeaver
远程登录命令行工具：terminal+OpenSSL for Windows
远程编辑文件：RSE
JDT(Install New Software)，CDT，PDT，Pydev
Remote System Explorer
SQL Development Tools 1.13
Github Blog: LiClipseText

ctrl + 上/下:   滚动屏幕，浏览代码 
ctrl + Q :  跳到最后一次编辑处




ATLAS(AbbreviatedTestLanguageforAllSystems)是一个面向测试的通用语言，这个语言用于描述通常与任何具体测试系统无关的测试过程，并确保可以在自动测试系统ATE(automatictestequipment)上实现。ATLAS语言因其可扩展性、易用性及设备无关性，被广泛应用于军事、工业等领域





自定义快捷键
Ctrl+E, Alt+J   Export Jar File





远程开发：
http://blog.csdn.net/lostaway/article/details/8086056   

Terminal光标相关（http://www.cnblogs.com/tanlujia/p/6406723.html）
Ctrl+u删除光标到行首的字符Ctrl+k删除光标到行尾的字符Ctrl+h删除一个字符(退格删除)Ctrl+c取消当前行输入的命令Ctrl+a光标移到行首 aheadCtrl+e光标移动行尾 endCtrl+l清屏（与clear类似）Ctrl+p调出命令历史中上一条(与↑类似) precedingCtrl+n调出命令历史中下一条(与↓类似) nextCtrl+w删除当前光标前的一个单词Ctrl+y粘贴(Ctrl+w)删除的单词

运行找不到.so
GCC C++ Linker -> Miscellaneous -> Linker flag: -Wl,-rpath=/home/ubuntu/workspace/DFS2/third/ImageMagick/lib
http://blog.sina.com.cn/s/blog_6d09b5750100y7lp.html

终端插件：http://marketplace.eclipse.org/content/terminal-plug

Q: error perf was not found on path
A: sudo apt-get install linux-tools-common 
sudo apt-get install linux-tools
perf -version
sudo apt-get install linux-tools-4.2.0-27-generic


备选插件：
http://www.jb51.net/article/34136.htm
Saros - 分布式结对编程（Distributed Pair Programming）


QA:
eclipse解决push是auth fail的问题
$ git config --global user.name "Gennadiy Zlobin" (your name)
$ git config --global user.email gennad.zlobin@gmail.com (your email)
$ ssh-keygen -C "gennad.zlobin@gmail.com" -t rsa (your email)
Now your generated keys are in C:\Users\username\.ssh (in Windows). 
Next you load the content of your public key to your project on Github 
In Eclipse open Window->Preferences->General->Network->SSH2 and set your ~/.ssh as SSH Home
After that go to Key Management tab and Load existing Key - set here your private key in ~/.ssh.
After that you can push your project to Github (but I set ssh protocol, not git+ssh).
一定要注意是C:\Users\username\.ssh 而不是C:\Users\username\ssh，少一个点就错了
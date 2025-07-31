# 进程
## 使用Process Explorer查看程序加载的dll
[参考](https://blog.csdn.net/qq_45237725/article/details/116358241)

适用`matlab/software/ProcessExplorer/Listdlls.exe`
```commandline
Listdlls viso2pdf
```

## windows系统卸载程序时提示：`请等待当前进程完成卸载或更改`

解决：在任务管理器中结束dllhost.exe进程。


# 网络
## 查看电脑公网IP
```commandline
curl ip.me
```


# 设置
## 权限
[改变文件夹的所有者](https://www.win10com.com/win10jiaocheng/29497.html) 



# 下载
## IDM
[解决IDM弹窗方法](https://blog.csdn.net/double_sweet1/article/details/113761085) 


# 
准备删除
C:\ProgramData中有一个Package Cache文件夹


查看端口占用：
netstat -ano
最后一列为PID
tasklist|findstr "2720"
杀进程
```shell
taskkill /pid 2000 -f
```

Win10打开开机启动目录
shell:startup

office一动就未响应：默认打印机为网络打印机

chrome newtab异常：
删除chrome不需要的插件就好了

游戏录制工具
Win+G键打开录制工具
Win+Alt+R键即可开始录制。若要停止录制，再次按住键盘上的Win+Alt+R键即可
Win+Alt+PrtScr键

录屏：https://www.7down.com/soft/255321.html

（失败）
https://answers.microsoft.com/zh-hans/windows/forum/all/win10%E8%87%AA%E5%B8%A6%E7%9A%84%E7%A7%BB%E5%8A%A8/b0bce725-672a-4b37-a172-a4196ef708c6
start C:\Windows\System32\GroupPolicy\Machine\Scripts\Startup

Adobe Reader "复制到剪贴板时发生错误。出现内部错误。
BeyondCompare监控了系统剪切板

百度云分享HTTP链接：
https://pan.baidu.com/s/1VMabEUHRap54F3QBcuOOsw
https://pan.baidu.com/s/1VMabEUHRap54F3QBcuOOsw/share#list/path=%2Fshare
解码：
https://pan.baidu.com/s/1VMabEUHRap54F3QBcuOOsw/share#list/path=/share
https://pan.baidu.com/s/1VMabEUHRap54F3QBcuOOsw/share#list/path=/share/mexopts.rar

下载Youtube视频（不要安装插件，直接点击下载）
Add "savefrom.net/" or "sfrom.net/" before the URL and press Enter
example: sfrom.net/http://youtube.com/watch?v=u7deClndzQw
允许显示通知才会显示下载链接

vc版本与vs版本对应关系如下所示：
Visual Studio 6 ： vc6 
Visual Studio 2003 ： vc7 
Visual Studio 2005 ： vc8 
Visual Studio 2008 ： vc9 
Visual Studio 2010 ： vc10 
Visual Studio 2012 ： vc11 
Visual Studio 2013 ： vc12 
Visual Studio 2015 ： vc14 
Visual Studio 2017 ： vc15

查看网址对应的ip地址：
nslookup https://hub.docker.com

打开临时目录：资源浏览器中的地址栏输入%tmp%

看局域网内有哪些IP在使用
arp -a

校园网刷新不出登录页面：
执行页面提示修复操作，按照提示进行管理员权限（重置网络），重启。

执行字符串指定的命令并结束
cmd /C call "D:\software\Adobe Acrobat X\Acrobat\Acrobat" C:\Shortcut\script\xl.pdf

取消代理服务器：
1、打开Internet 浏览器
2、在浏览器打开nternet选项
3、在internet 属性 界面的“连接”选卡界面点击“局域网设置”;
4、将“为LAN使用代理服务器(这些设置不用于拨号或VPN连接)”前面的勾去掉，若 【自动检测设置】已勾选则取消勾选，若【自动检测设置】未勾选则将其勾选，然后点击确定;

开机自启目录：C:\Users\DELL\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

本地安全策略：secpol.msc

beyond compare
删除其安装目录下的BCUnrar.dll再试

隐藏文档、图片等文件夹
http://www.360doc.com/content/16/0919/14/2149364_592004004.shtml

Win10去掉3D对象文件夹：
1、按下WIN+R，然后输入regedit 回车；
2、然后找到：
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace\
3、找到3D对象文件夹对应的{0DB7E03F-FC29-4DC6-9020-FF41B59E513A} 项，删除
4、然后们再打开
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Explorer\MyComputer\NameSpace
5、继续删除{0DB7E03F-FC29-4DC6-9020-FF41B59E513A}
6、退出注册表，刷新一下，就会发现3D对象文件夹不见了。


# WSL
[离线安装WSL系统](https://blog.csdn.net/qq_34548424/article/details/127421370) 

## 显卡驱动
```shell
sudo apt install nvidia-cuda-toolkit
```

## 密码不正确
进入powershell
```shell
wsl -u root
```
重置特定用户密码：
```shell
passwd userid
```


# 命令
开机自启目录：win+r
```bat
shell:startup
```

“hiberfil.sys”是系统休眠文件，其大小和物理内存一样大，它可以删除（但不能手动删除）
```
powercfg -h off
```


https://github.com/ishanjain28/burnbitbot

系统属性
```commandline
SystemPropertiesAdvanced
```

进入到Adobe Acrobat的安装目录，一般是C:\Program Files\Adobe\Acrobat 7.0\Acrobat\plug_ins，可以看到该文件夹下有很多文件，
这些东东就是严重影响Acrobat启动速度和阅读体验的插件文件，找到其中的accessibility.api，删除之

win10 Host文件目录
C:\Windows\System32\drivers\etc\hosts

查看端口占用： netstat –ano|findstr 9001
找到进程号对应的进程名称： tasklist|findstr 9001



静态连结：
LIBCMTD.lib（Debug版本）
LIBCMT.lib
使用静态连结时，会直接将程式库的函式定义嵌入执行档之中，
而使用动态连结时，程式库的函式定义则存在于另外的独立档案，通常是 DLL 格式的档案中，然后与程式执行档一同发佈给使用者

动态连结：
MSVCRTD.lib（Debug版本）Run-Time
MSVCRT.lib

MSVCP120D.dll



C++
静态连结：
LIBCPMTD.lib（除错版本）
LIBCPMT.lib

动态连结：
MSVCPRTD.lib（除错版本）：执行档相依于 MSVCP90D.dll
MSVCPRT.lib：执行档相依于 MSVCP90.dll


































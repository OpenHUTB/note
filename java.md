

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer


# java9 安装
1. 安装JDK9
2. 安装Eclipse的Java9插件：Help -> Eclipse Marketplace -> Search -> java9
    需要更新Eclipse的Java9插件：Help -> Eclipse Marketplace -> Installed ->  Java 9 Support for Oxygen 4.7 -> update；不然添加JDK的时候出现：Target is not a JDK root错误
3. 配置Java9(使用Java9不需要使用Java9启动Eclipse，Java9也可以；Java9启动Eclipse会在第二屏幕上所有的字体会变大，原因不明)
    https://wiki.eclipse.org/Configure_Eclipse_for_Java_9
    修改eclipse.ini：
        --launcher.appendVmargs
        -vm
        F:/ProgramFiles/Java/jdk-9/bin/javaw.exe
        -vmargs
        -Dosgi.requiredJavaVersion=1.8
        --add-modules=ALL-SYSTEM
    说明：-vm指定使用的Java虚拟机启动Eclipse: C:/Program Files/Java/jdk1.8.0_65/bin/javaw.exe
    后面的-vmargs 和 -Dosgi.requiredJavaVersion=1.8 需要删除
    

Java9 新特性
1. Modular System - Jigsaw Project
模块之间存储在相互依赖，可以导出一个公共的API，并且隐藏实现的细节（为了减少JVM加载rt.jar的内存开销），模块化可以根据模块的需要加载程序所需要的class。
2. 
3. Process API Enhance
以前通过Process可以获得一些runtime信息，甚至执行当前主机的一些命令，新加入的API可以获得当前Java运行程序的PID。

7. JShell Command Line Tool
Java可以像脚本一样运行, jshell.exe
jshell> "This is my long string. I want a part of it".substring(8,19);
jshell> /save f:\tmp\JShell_hello_world.txt
jshell> /open f:\tmp\JShell_hello_world.txt

11. Publish-Subscribe Framework
消息发布订阅框架，该框架主要由Flow这个类提供；并提供了Reactive编程模式。
FRP(Functional Reactive Programming)是面向异步事件流的编程了，这个异步事件流叫：Observable，一般叫：Stream
Stream就是一个 按时间排序的Events(Ongoing events ordered in time)序列。




修为Eclipse启动使用的虚拟机为Java8
-startup
plugins/org.eclipse.equinox.launcher_1.4.0.v20161219-1356.jar
--launcher.library
plugins/org.eclipse.equinox.launcher.win32.win32.x86_64_1.1.500.v20170531-1133
-product
org.eclipse.epp.package.php.product
-showsplash
org.eclipse.epp.package.common
--launcher.defaultAction
openFile
--launcher.defaultAction
openFile
--launcher.appendVmargs
-vm
C:/Program Files/Java/jdk1.8.0_65/bin/javaw.exe
-vmargs
-Dosgi.requiredJavaVersion=1.8
-Dosgi.instance.area.default=@user.home/eclipse-workspace
-XX:+UseG1GC
-XX:+UseStringDeduplication
-Dosgi.requiredJavaVersion=1.8
-Xms256m
-Xmx1024m




下载Java8：wget -c --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.tar.gz

jcabi 必须是本机的私钥进行登录

Java8视屏
https://pan.baidu.com/s/1nvCt83v
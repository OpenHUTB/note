

# 编译
# libsvm
重新编译，需要先运行“C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\bin\amd64\vcvars64.bat”，
然后再用“VS2015 x64 本机工具命令提示符“运行
```commandline
nmake -f Makefile.win clean all
```

# 
无法解析的外部符号 __imp___malloc_dbg, new delete
改为多线程调试

Vs2015创建C++项目点确定没反应，需要修复
F:\packages\VisualC_D14\VC_ATL.Source
F:\packages\VisualC_D14\VC_ATL.Source

在Arbiter里，用setrlimit解锁内存，用blocked pipe io + detached double fork 解限制时间。

安装包：
https://www.cnblogs.com/dongh/p/6868638.html
https://blog.csdn.net/qq_43026206/article/details/104264194

Release模式
LNK1179: 无效或损坏的文件: 重复的 COMDAT“?XXX@XXXX”
解决方法：项目右击【属性】 - 【C/C++】 - 【优化】 - 【全程序优化改成】   “否”   就解决了。
程序无法启动0X07错误: Dependency Walker分析第一层为红色的dll文件即为缺失的文件，放在exe当前目录

C++代码生成 -> 运行库 -> 多线程 /MT
配置属性->常规->MFC的使用->使用标准windows库

dumpbin /dependents xxxx.exe
> output.txt


cygwin在线安装的镜像
http://mirrors.163.com/cygwin/

/usr/lib/gcc/x86_64-pc-cygwin/9.3.0/../../../../x86_64-pc-cygwin/bin/ld: skipping incompatible lib/Expat_2.2.9/Bin/libexpat.lib when searching for -lexpat
expat库不兼容，可能不是64未编译的。还有可能在windows上是Microsoft Visual Studio >=9.0/2008编译的


检测到“_ITERATOR_DEBUG_LEVEL”的不匹配项: 值“2”不匹配值“0”
则说明是Release模式引用了Debug的库文件
2表示Release, 0 表示Debug

vs2015
要引用相对路径 ，需要把文件放在这个项目名称的文件夹里面
cmake -G"Visual Studio 14 2015" -DCMAKE_BUILD_TYPE=RelWithDebInfo ..

重启Eclipse就能加载库了：System.loadLibrary("CplusImplement");


使用源代码重新再x64上编译，github上只提供了32位的安装版
D:\workspace\homework\1605_java\workspace\libexpat-R_2_2_9\expat\build\Debug


可以32,64位，
release: gurobi_c++md2015.lib
debug
D:\software\Gurobi-6.5.1-win64\win64\bin\gurobi65.dll
gurobi_c++mdd2015.lib


D:\software\cygwin64\home\Administrator\libexpat-R_2_2_9\build\bin\cygexpat-1.dll
gcc编译：libexpat.a
自己编译：（注意使用自己编译的x64 Debug版本，否则启动失败07）dll也要重新拷贝（原来的名字相同）

D:\workspace\homework\1605_java\workspace\vns_cpp\lib\pthread\lib\x64\pthreadVC2.dll
32位
64位

D:\software\cygwin64\bin\cygwin1.dll



先修改为demo数据，才能跑通
khe_soln.c的KHE_SOLN KheSolnCopyPhase1(KHE_SOLN soln)报错
vns_cpp.exe!svnsHMT(khe_soln_rec * soln, khe_instance_rec * instance, Config & config) 行 1367	C++
vns_cpp.exe!KheSolnCopy(khe_soln_rec * soln) 行 1627	C
(SVNS)  Only one design to be multitheread
改为爬山算法
LAHC: for Late Acceptance Hill-Climbing
KHE_SOLN KheSolnCopyPhase1(KHE_SOLN soln)
soln = KheSolnCopy(bestSoln);
soln = lahc(soln, instance, config);

过了ALGORITHM，FORMULATION失败
// -xml=ItalyInstance4.xml -time_limit=1000 -seed=9 -threads=1 -initial_soln=KHE -algorithm=DM -formulation=FIXOPT -alg_timelimit=100 -form_timelimit=50 -formfixopt_nresources=5 -formfixopt_optinarow=5
第一次成功，下降法，no formulation
-xml=ItalyInstance4.xml -time_limit=1000 -seed=9 -threads=1 -initial_soln=KHE -algorithm=DM -formulation=NONE -alg_timelimit=100 -form_timelimit=50 -formfixopt_nresources=5 -formfixopt_optinarow=5
<CostFunction> has obsolete value "Sum"
第一次跑通自己的数据（将Sum改为Leaner）：
vns_cpp.exe -xml=AustraliaTES99.xml -time_limit=1000 -seed=9 -threads=1 -initial_soln=KHE -algorithm=DM -formulation=NONE -alg_timelimit=100 -form_timelimit=50 -formfixopt_nresources=5 -formfixopt_optinarow=5

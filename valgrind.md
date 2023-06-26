
使用Valgrind memcheck工具进行C/C++的内存泄漏检测 
调不尽的内存泄漏，用不完的Valgrind
名字取自北欧神话中英灵殿的入口
北欧人对于寒冬何以会来的解释:奥丁负气离开了“诸神国度”，到地上漫游, 霜巨人们便用寒冰封锁了大地;七个月以后，奥丁回来了。
阿斯神族的末日，是一场被称为“诸神的黄昏”的战役
http://www.eclipse.org/linuxtools/projectPages/valgrind/


Invalid read of size 4
这个错误的发生是因为对一些memcheck猜想不应该访问的内存进行了读写。

Use of uninitialised values
这个错误的发生是因为使用了未初始化的数据。一般情况下有两种情形容易出现这个错误：
程序中的局部变量未初始化；
C语言malloc的内存未初始化；C++中new的对象其成员未被初始化。




Q: qmake:提示could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory
修改：/usr/lib/x86_64-linux-gnu/qt-default/qtchooser/default.conf  文件内容，里面第一行内容为默认的编译器。
/data2/whd/software/Qt5.12.9/5.12.9/gcc_64/bin


IR(intermediate representation)中间字节码
传统编译器的代表(GCC)由于编译前后端耦合度太高，增加一个 前端语言支持 或者一个 后端平台支持 将会变得异常复杂。
相比之下LLVM由于是分离式架构，其组件复用性就很高，增加语言/平台支持也相对容易，增加一个新的编程语言，就增加一个新的前端组件，增加一个新的平台支持，就增加一个新的后端组件。
LLVM编译器不同的前端统一使用相同的中间码


configure交叉编译：处理好编译器和依赖库
对于configure来说，编译器可以通过环境变量CC来设置。
设置依赖库也是和makefile一样的，通过环境变量LDFLAGS。设置对应的头文件则是通过环境变量CFLAGS。
CC=/usr/local/arm11-toolchain/g4.4.2/cross-tools/bin/g-4.4.2 \
LDFLAGS="-L/home/third_party/source/lib -L/home/third_party/library/g-4.4.2/zlib/lib" \
./configure  --build=i686-pc-linux --host=arm-linux --target=i686-linux \
 --enable-shared --prefix=$PREFIX \
 --with-freetype-config=$PREFIX/bin/freetype-config \
 --enable-libxml2 --with-arch=arm \
CFLAGS=-I/home/third_party/library/g-4.4.2/freetype/include-I/home/third_party/library/g-4.4.2/freetype/include/freetype2 \


--build指明的是在什么环境下编译，--host是要编译到哪个环境，--target是在什么环境下运行。
如果你要做交叉编译，这三个选项是一定要写上的，否则configure不知道自己是在进行交叉编译。

readelf -h ./xz


No symbol "i" in current context.(gcc和gdb版本不兼容）
http://ftp.gnu.org/gnu/gdb/gdb-8.1.tar.gz

/usr/local/bin/gdb
/usr/bin/gdb

bt （backtrace)


set args --gpuID=0 --type=1 --vid_path=/home/data/UCF101 --out_path=/home/data/gesture/flow --stride=1

GDB
  ● continue    继续运行程序直到下一个断点（类似于VS里的F5）
  ● next        逐过程步进，不会进入子函数（类似VS里的F10）
  ● setp        逐语句步进，会进入子函数（类似VS里的F11）
  ● until        运行至当前语句块结束
  ● finish    运行至函数结束并跳出，并打印函数的返回值（类似VS的Shift+F11）

backtrace命令（简写为bt）可以查看函数调用的栈帧

info命令（简写为i）查看add_range函数局部变量的值：(gdb) i locals

frame命令（简写为f）选择1号栈帧然后再查看局部变量：(gdb) f 1

print命令（简写为p）打印出变量sum的值：(gdb) p sum

finish命令让程序一直运行到从当前函数返回为止：(gdb) finish

在gdb中马上把sum的初值改为0: set var sum=0

http://www.cnblogs.com/TianFang/archive/2013/01/20/2868889.html
一步步执行：http://www.cnblogs.com/hankers/archive/2012/12/07/2806836.html



如果你的硬件平台增加了一些指令，而普通的编译器并不能产生这些指令怎么办？在GCC后端添加这些指令吧。
如果你觉得C语言用的不太顺手，想给它添加一些功能怎么办？修改GCC的前端吧

autoconf
http://blog.csdn.net/l_serein/article/details/5826787
http://www.cnblogs.com/bugutian/p/5560548.html

./configure --help

/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 16 has invalid symbol index 13
gcc -o 没有main函数，生成不了可执行文件


a label can only be part of a statement and a declaration is not a statement
变量定义在case中，或者使用goto语句有一个label，在这些label后定义一个变量都会报错
在定义变量的地方和使用它之后的地方用大括号括起来就可以了。(需要给他明确指个作用域)


gcc -c 生成.o
-o 生成可执行程序


${CC} -I../client -o DFS DFS.o ${ALL_OBJS} -L../thrid/libfastcommon-1.0.7/lib -lfastcommon -lpthread    # 链接成exe文件
找不到头文件: -I../client
链接其他的.o文件:  直接在后面加上各种需要的.o（有什么未定义就加上什么.o、.so、(-L)-l）
编译的目标:      -o DFS


编译成.so文件
${CC} -c -fPIC -o ${SRC}.o  ${SRC}.c    # compile, PIC(Position Independent Code)
${CC} -shared -o ./lib/lib${SRC}.so ${SRC}.o        # generate share library
-Wl  //指示后面的参数是传递给ld链接器的
-static //指示链接器构建一个完全链接的可执行程序，即链接静态库而不链接动态库


-Wl,-rpath=.        (rpath代表runtime path)不需要设置环境变量。这样做的坏处是，如果库文件移动位置，我们需要重新编译test
(多个的话用:作为目录分隔)
记得-rpath有有个"-"


库文件依赖的顺序：???
${CC} ${DEPENDENCE} DFS.o ${LIB_PATH} -liniparser -Wl,-rpath=./third/libfastcommon-1.0.7/lib -o DFS # 链接成exe文件

写gcc的顺寻 -o .c ${OBJS}
OBJS = -lm -ljpeg -L/home/ubuntu/install/eclipse/workspace/DFS/third/jpeg-9/jpeg/lib misc.o jpegdest.o
$(CC) -o jpegoptim jpegoptim.c ${OBJS}


如果一份文件foo引用了静态库bar.a，那么在链接命令中，bar.a必须放在foo的后面
.a文件其实没什么特别的地方，它不过是将多个.o文件打包成一份文件
.o文件在链接中并不遵循.a文件那样的链接顺序，看来链接器找符号时，一定会搜索命令中的.o文件。


bash: ./configure: /bin/sh^M: 坏的解释器: 没有那个文件或目录
脚本文件在windows下编辑过。windows下，每一行的结尾是\n\r，而在Linux下文件的结尾是\n
用cat -A urfile时你可以看到这个\r字符被显示为^M，这时候只需要删除这个字符就可以了。
可以使用命令sed -i 's/\r$//' urfile （-i ：直接修改读取的文件内容，而不是输出到终端）


/usr/bin/ld: /usr/lib/debug/usr/lib/x86_64-linux-gnu/crt1.o(.debug_info): relocation 4 has invalid symbol index 11
出现很多0x86_64  --> 注释掉编译主函数
-c DFS.o 编译成.o文件


返回指针不对：没有引入头文件，默认函数返回的是一个int 32位的类型，做了一个符号扩展
https://sourceware.org/binutils/docs/as/i386_002dMnemonics.html
cltq: Convert Long To Quad 


/usr/bin/ld: errno: TLS definition in /lib/x86_64-linux-gnu/libc.so.6 section .tbss mismatches non-TLS reference in /tmp/ccw1lBuE.o
在编译时加上 -include /usr/include/errno.h 即可


被多次定义
.o文件被连接了两次


/usr/bin/ld: errno: TLS definition in /lib/x86_64-linux-gnu/libc.so.6 section .tbss mismatches non-TLS reference in 
CFLAGS后边加-include /usr/include/errno.h

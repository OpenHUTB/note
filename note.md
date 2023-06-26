



方案一（11w）：
10台1060（0.5w）+ 4路1080Ti服务器（6w）
方案二（15w）：
10台1080Ti：10*1.5w 


并行算法分析与设计	研究生院楼D312	信息科学与工程学院	A1610020D	并行算法分析与设计	吴帆	第1-16周; 星期五-晚上9,晚上10,晚上11	48	3.00	是


凌坤：



******************************************************************************

line   51:
E319: Sorry, the command is not available in this version: let Tlist_Use_Right_Window = 1
line   52:
E319: Sorry, the command is not available in this version: let Tlist_GainFocus_On_ToggleOpen = 1
line   55:
E319: Sorry, the command is not available in this version: let g:vim_markdown_folding_disabled=1
line   58:
E319: Sorry, the command is not available in this version: let mapleader = ','
Press ENTER or type command to continue
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ gcc -g -O0 -I../client -I../third/iniparser-master/src -I../tools -I../DES ../third/jpegoptim-master/jpegoptim.o ../third/jpegoptim-master/misc.o ../third/jpegoptim-master/jpegdest.o  -lm -ljpeg -L../usr/lib/x86_64-linux-gnu ../client/fdfsClient.o ../client/fdfs_upload_file.o ../client/fdfs_download_file.o ../client/fdfs_delete_file.o ../client/client_global.o ../client/storage_client.o ../client/tracker_client.o ../client/client_func.o ../tracker/fdfs_shared_func.o ../tracker/tracker_proto.o ../common/fdfs_global.o ../common/fdfs_http_shared.o ../common/mime_file_parser.o ../storage/trunk_mgr/trunk_shared.o -L../third/libfastcommon-1.0.7/lib -L../third/iniparser-master -L../tools/lib -lfastcommon -lpthread -liniparser -c DFS.c --verbose --save-temps
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES -imultiarch x86_64-linux-gnu DFS.c -mtune=generic -march=x86-64 -g -fworking-directory -O0 -fpch-preprocess -fstack-protector -Wformat -Wformat-security -o DFS.i
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 ../client
 ../third/iniparser-master/src
 ../tools
 ../DES
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -fpreprocessed DFS.i -quiet -dumpbase DFS.c -mtune=generic -march=x86-64 -auxbase DFS -g -O0 -version -fstack-protector -Wformat -Wformat-security -o DFS.s
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a0a649d344b1ed798e33d30772d46437
DFS.c: In function ‘uploadToFastDFS’:
DFS.c:39:3: warning: passing argument 2 of ‘jpegoptimMain’ from incompatible pointer type [enabled by default]
   unsigned char* tmpP = jpegoptimMain(fileBuffer, &fileSize, quality); // Cannot access memory at address 0xfffffffff7ee9010
   ^
In file included from DFS.c:17:0:
../third/jpegoptim-master/jpegoptim.h:63:16: note: expected ‘long unsigned int *’ but argument is of type ‘int *’
 unsigned char* jpegoptimMain(unsigned char * fileBuffer, unsigned long * compressedFileSize, int quality);
                ^
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 as -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES --64 -o DFS.o DFS.s
GNU汇编版本 2.24 (x86_64-linux-gnu) 使用BFD版本 (GNU Binutils for Ubuntu) 2.24
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
gcc: warning: ../third/jpegoptim-master/jpegoptim.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/misc.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/jpegdest.o: linker input file unused because linking not done
gcc: warning: ../client/fdfsClient.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_upload_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_download_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_delete_file.o: linker input file unused because linking not done
gcc: warning: ../client/client_global.o: linker input file unused because linking not done
gcc: warning: ../client/storage_client.o: linker input file unused because linking not done
gcc: warning: ../client/tracker_client.o: linker input file unused because linking not done
gcc: warning: ../client/client_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/fdfs_shared_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/tracker_proto.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_global.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_http_shared.o: linker input file unused because linking not done
gcc: warning: ../common/mime_file_parser.o: linker input file unused because linking not done
gcc: warning: ../storage/trunk_mgr/trunk_shared.o: linker input file unused because linking not done
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/4.8/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ gcc -g -O0 -I../client -I../third/iniparser-master/src -I../tools -I../DES ../third/jpegoptim-master/jpegoptim.o ../third/jpegoptim-master/misc.o ../third/jpegoptim-master/jpegdest.o  -lm -ljpeg -L../usr/lib/x86_64-linux-gnu ../client/fdfsClient.o ../client/fdfs_upload_file.o ../client/fdfs_download_file.o ../client/fdfs_delete_file.o ../client/client_global.o ../client/storage_client.o ../client/tracker_client.o ../client/client_func.o ../tracker/fdfs_shared_func.o ../tracker/tracker_proto.o ../common/fdfs_global.o ../common/fdfs_http_shared.o ../common/mime_file_parser.o ../storage/trunk_mgr/trunk_shared.o -L../third/libfastcommon-1.0.7/lib -L../third/iniparser-master -L../tools/lib -lfastcommon -lpthread -liniparser -c DFS.c --verbose --save-temps
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES -imultiarch x86_64-linux-gnu DFS.c -mtune=generic -march=x86-64 -g -fworking-directory -O0 -fpch-preprocess -fstack-protector -Wformat -Wformat-security -o DFS.i
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 ../client
 ../third/iniparser-master/src
 ../tools
 ../DES
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -fpreprocessed DFS.i -quiet -dumpbase DFS.c -mtune=generic -march=x86-64 -auxbase DFS -g -O0 -version -fstack-protector -Wformat -Wformat-security -o DFS.s
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a0a649d344b1ed798e33d30772d46437
DFS.c: In function ‘uploadToFastDFS’:
DFS.c:39:25: warning: initialization makes pointer from integer without a cast [enabled by default]
   unsigned char* tmpP = jpegoptimMainXXX(fileBuffer, &fileSize, quality); // Cannot access memory at address 0xfffffffff7ee9010
                         ^
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 as -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES --64 -o DFS.o DFS.s
GNU汇编版本 2.24 (x86_64-linux-gnu) 使用BFD版本 (GNU Binutils for Ubuntu) 2.24
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
gcc: warning: ../third/jpegoptim-master/jpegoptim.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/misc.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/jpegdest.o: linker input file unused because linking not done
gcc: warning: ../client/fdfsClient.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_upload_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_download_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_delete_file.o: linker input file unused because linking not done
gcc: warning: ../client/client_global.o: linker input file unused because linking not done
gcc: warning: ../client/storage_client.o: linker input file unused because linking not done
gcc: warning: ../client/tracker_client.o: linker input file unused because linking not done
gcc: warning: ../client/client_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/fdfs_shared_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/tracker_proto.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_global.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_http_shared.o: linker input file unused because linking not done
gcc: warning: ../common/mime_file_parser.o: linker input file unused because linking not done
gcc: warning: ../storage/trunk_mgr/trunk_shared.o: linker input file unused because linking not done
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ gcc -g -O0 -I../client -I../third/iniparser-master/src -I../tools -I../DES ../third/jpegoptim-master/jpegoptim.o ../third/jpegoptim-master/misc.o ../third/jpegoptim-master/jpegdest.o  -lm -ljpeg -L../usr/lib/x86_64-linux-gnu ../client/fdfsClient.o ../client/fdfs_upload_file.o ../client/fdfs_download_file.o ../client/fdfs_delete_file.o ../client/client_global.o ../client/storage_client.o ../client/tracker_client.o ../client/client_func.o ../tracker/fdfs_shared_func.o ../tracker/tracker_proto.o ../common/fdfs_global.o ../common/fdfs_http_shared.o ../common/mime_file_parser.o ../storage/trunk_mgr/trunk_shared.o -L../third/libfastcommon-1.0.7/lib -L../third/iniparser-master -L../tools/lib -lfastcommon -lpthread -liniparser -c DFS.c --verbose --save-temps
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES -imultiarch x86_64-linux-gnu DFS.c -mtune=generic -march=x86-64 -g -fworking-directory -O0 -fpch-preprocess -fstack-protector -Wformat -Wformat-security -o DFS.i
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 ../client
 ../third/iniparser-master/src
 ../tools
 ../DES
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -fpreprocessed DFS.i -quiet -dumpbase DFS.c -mtune=generic -march=x86-64 -auxbase DFS -g -O0 -version -fstack-protector -Wformat -Wformat-security -o DFS.s
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a0a649d344b1ed798e33d30772d46437
DFS.c: In function ‘uploadToFastDFS’:
DFS.c:39:25: warning: initialization makes pointer from integer without a cast [enabled by default]
   unsigned char* tmpP = jpegoptimMainXXX(fileBuffer, &fileSize, quality); // Cannot access memory at address 0xfffffffff7ee9010
                         ^
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 as -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES --64 -o DFS.o DFS.s
GNU汇编版本 2.24 (x86_64-linux-gnu) 使用BFD版本 (GNU Binutils for Ubuntu) 2.24
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-g' '-O0' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
gcc: warning: ../third/jpegoptim-master/jpegoptim.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/misc.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/jpegdest.o: linker input file unused because linking not done
gcc: warning: ../client/fdfsClient.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_upload_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_download_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_delete_file.o: linker input file unused because linking not done
gcc: warning: ../client/client_global.o: linker input file unused because linking not done
gcc: warning: ../client/storage_client.o: linker input file unused because linking not done
gcc: warning: ../client/tracker_client.o: linker input file unused because linking not done
gcc: warning: ../client/client_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/fdfs_shared_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/tracker_proto.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_global.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_http_shared.o: linker input file unused because linking not done
gcc: warning: ../common/mime_file_parser.o: linker input file unused because linking not done
gcc: warning: ../storage/trunk_mgr/trunk_shared.o: linker input file unused because linking not done
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ gcc -std=c99 -g -O3 -I../client -I../third/iniparser-master/src -I../tools -I../DES ../third/jpegoptim-master/jpegoptim.o ../third/jpegoptim-master/misc.o ../third/jpegoptim-master/jpegdest.o  -lm -ljpeg -L../usr/lib/x86_64-linux-gnu ../client/fdfsClient.o ../client/fdfs_upload_file.o ../client/fdfs_download_file.o ../client/fdfs_delete_file.o ../client/client_global.o ../client/storage_client.o ../client/tracker_client.o ../client/client_func.o ../tracker/fdfs_shared_func.o ../tracker/tracker_proto.o ../common/fdfs_global.o ../common/fdfs_http_shared.o ../common/mime_file_parser.o ../storage/trunk_mgr/trunk_shared.o -L../third/libfastcommon-1.0.7/lib -L../third/iniparser-master -L../tools/lib -lfastcommon -lpthread -liniparser -c DFS.c --verbose --save-temps
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
COLLECT_GCC_OPTIONS='-std=c99' '-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES -imultiarch x86_64-linux-gnu DFS.c -mtune=generic -march=x86-64 -std=c99 -g -fworking-directory -O3 -fpch-preprocess -fstack-protector -Wformat -Wformat-security -o DFS.i
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 ../client
 ../third/iniparser-master/src
 ../tools
 ../DES
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
COLLECT_GCC_OPTIONS='-std=c99' '-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -fpreprocessed DFS.i -quiet -dumpbase DFS.c -mtune=generic -march=x86-64 -auxbase DFS -g -O3 -std=c99 -version -fstack-protector -Wformat -Wformat-security -o DFS.s
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a0a649d344b1ed798e33d30772d46437
DFS.c: In function ‘uploadToFastDFS’:
DFS.c:39:3: warning: implicit declaration of function ‘jpegoptimMainXXX’ [-Wimplicit-function-declaration]
   unsigned char* tmpP = jpegoptimMainXXX(fileBuffer, &fileSize, quality); // Cannot access memory at address 0xfffffffff7ee9010
   ^
DFS.c:39:25: warning: initialization makes pointer from integer without a cast [enabled by default]
   unsigned char* tmpP = jpegoptimMainXXX(fileBuffer, &fileSize, quality); // Cannot access memory at address 0xfffffffff7ee9010
                         ^
DFS.c: In function ‘downloadFromFastDFS’:
DFS.c:85:2: warning: implicit declaration of function ‘strtok_r’ [-Wimplicit-function-declaration]
  decryptedFileID = strtok_r(decryptedFileID, delims, &p);
  ^
DFS.c:85:18: warning: assignment makes pointer from integer without a cast [enabled by default]
  decryptedFileID = strtok_r(decryptedFileID, delims, &p);
                  ^
DFS.c:86:29: warning: initialization makes pointer from integer without a cast [enabled by default]
  char * decryptedUserName = strtok_r(NULL, delims, &p);
                             ^
DFS.c: In function ‘main’:
DFS.c:252:7: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
  fread(fileBuffer, fileSize, sizeof(char), fp); // 读取已经加密的字符串
       ^
COLLECT_GCC_OPTIONS='-std=c99' '-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 as -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES --64 -o DFS.o DFS.s
GNU汇编版本 2.24 (x86_64-linux-gnu) 使用BFD版本 (GNU Binutils for Ubuntu) 2.24
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-std=c99' '-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
gcc: warning: ../third/jpegoptim-master/jpegoptim.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/misc.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/jpegdest.o: linker input file unused because linking not done
gcc: warning: ../client/fdfsClient.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_upload_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_download_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_delete_file.o: linker input file unused because linking not done
gcc: warning: ../client/client_global.o: linker input file unused because linking not done
gcc: warning: ../client/storage_client.o: linker input file unused because linking not done
gcc: warning: ../client/tracker_client.o: linker input file unused because linking not done
gcc: warning: ../client/client_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/fdfs_shared_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/tracker_proto.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_global.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_http_shared.o: linker input file unused because linking not done
gcc: warning: ../common/mime_file_parser.o: linker input file unused because linking not done
gcc: warning: ../storage/trunk_mgr/trunk_shared.o: linker input file unused because linking not done
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ fg
bash: fg: 当前: 无此任务
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ gcc  -g -O3 -I../client -I../third/iniparser-master/src -I../tools -I../DES ../third/jpegoptim-master/jpegoptim.o ../third/jpegoptim-master/misc.o ../third/jpegoptim-master/jpegdest.o  -lm -ljpeg -L../usr/lib/x86_64-linux-gnu ../client/fdfsClient.o ../client/fdfs_upload_file.o ../client/fdfs_download_file.o ../client/fdfs_delete_file.o ../client/client_global.o ../client/storage_client.o ../client/tracker_client.o ../client/client_func.o ../tracker/fdfs_shared_func.o ../tracker/tracker_proto.o ../common/fdfs_global.o ../common/fdfs_http_shared.o ../common/mime_file_parser.o ../storage/trunk_mgr/trunk_shared.o -L../third/libfastcommon-1.0.7/lib -L../third/iniparser-master -L../tools/lib -lfastcommon -lpthread -liniparser -c DFS.c --verbose --save-temps
Using built-in specs.
COLLECT_GCC=gcc
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.8.4-2ubuntu1~14.04.3' --with-bugurl=file:///usr/share/doc/gcc-4.8/README.Bugs --enable-languages=c,c++,java,go,d,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.8 --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.8 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-gnu-unique-object --disable-libmudflap --enable-plugin --with-system-zlib --disable-browser-plugin --enable-java-awt=gtk --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64/jre --enable-java-home --with-jvm-root-dir=/usr/lib/jvm/java-1.5.0-gcj-4.8-amd64 --with-jvm-jar-dir=/usr/lib/jvm-exports/java-1.5.0-gcj-4.8-amd64 --with-arch-directory=amd64 --with-ecj-jar=/usr/share/java/eclipse-ecj.jar --enable-objc-gc --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.8.4 (Ubuntu 4.8.4-2ubuntu1~14.04.3) 
COLLECT_GCC_OPTIONS='-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -E -quiet -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES -imultiarch x86_64-linux-gnu DFS.c -mtune=generic -march=x86-64 -g -fworking-directory -O3 -fpch-preprocess -fstack-protector -Wformat -Wformat-security -o DFS.i
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 ../client
 ../third/iniparser-master/src
 ../tools
 ../DES
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.8/include-fixed
 /usr/include/x86_64-linux-gnu
 /usr/include
End of search list.
COLLECT_GCC_OPTIONS='-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 /usr/lib/gcc/x86_64-linux-gnu/4.8/cc1 -fpreprocessed DFS.i -quiet -dumpbase DFS.c -mtune=generic -march=x86-64 -auxbase DFS -g -O3 -version -fstack-protector -Wformat -Wformat-security -o DFS.s
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
GNU C (Ubuntu 4.8.4-2ubuntu1~14.04.3) version 4.8.4 (x86_64-linux-gnu)
    compiled by GNU C version 4.8.4, GMP version 5.1.3, MPFR version 3.1.2-p3, MPC version 1.0.1
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a0a649d344b1ed798e33d30772d46437
DFS.c: In function ‘uploadToFastDFS’:
DFS.c:39:25: warning: initialization makes pointer from integer without a cast [enabled by default]
   unsigned char* tmpP = jpegoptimMainXXX(fileBuffer, &fileSize, quality); // Cannot access memory at address 0xfffffffff7ee9010
                         ^
DFS.c: In function ‘main’:
DFS.c:252:7: warning: ignoring return value of ‘fread’, declared with attribute warn_unused_result [-Wunused-result]
  fread(fileBuffer, fileSize, sizeof(char), fp); // 读取已经加密的字符串
       ^
COLLECT_GCC_OPTIONS='-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
 as -v -I ../client -I ../third/iniparser-master/src -I ../tools -I ../DES --64 -o DFS.o DFS.s
GNU汇编版本 2.24 (x86_64-linux-gnu) 使用BFD版本 (GNU Binutils for Ubuntu) 2.24
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.8/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../../lib/:/lib/x86_64-linux-gnu/:/lib/../lib/:/usr/lib/x86_64-linux-gnu/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.8/../../../:/lib/:/usr/lib/
COLLECT_GCC_OPTIONS='-g' '-O3' '-I' '../client' '-I' '../third/iniparser-master/src' '-I' '../tools' '-I' '../DES' '-L../usr/lib/x86_64-linux-gnu' '-L../third/libfastcommon-1.0.7/lib' '-L../third/iniparser-master' '-L../tools/lib' '-c' '-v' '-save-temps' '-mtune=generic' '-march=x86-64'
gcc: warning: ../third/jpegoptim-master/jpegoptim.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/misc.o: linker input file unused because linking not done
gcc: warning: ../third/jpegoptim-master/jpegdest.o: linker input file unused because linking not done
gcc: warning: ../client/fdfsClient.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_upload_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_download_file.o: linker input file unused because linking not done
gcc: warning: ../client/fdfs_delete_file.o: linker input file unused because linking not done
gcc: warning: ../client/client_global.o: linker input file unused because linking not done
gcc: warning: ../client/storage_client.o: linker input file unused because linking not done
gcc: warning: ../client/tracker_client.o: linker input file unused because linking not done
gcc: warning: ../client/client_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/fdfs_shared_func.o: linker input file unused because linking not done
gcc: warning: ../tracker/tracker_proto.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_global.o: linker input file unused because linking not done
gcc: warning: ../common/fdfs_http_shared.o: linker input file unused because linking not done
gcc: warning: ../common/mime_file_parser.o: linker input file unused because linking not done
gcc: warning: ../storage/trunk_mgr/trunk_shared.o: linker input file unused because linking not done
ubuntu@ubuntu-ThinkPad-T460:~/install/eclipse/workspace/DFS/middle$ 
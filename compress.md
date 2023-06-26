
jpegoptim -d ./compressed terrain.jpg       压缩的图片将会保存在./compressed目录(以同样的输入文件名)
jpegoptim -d ./compressed -p terrain.jpg    增加-p 压缩后的图片会得到与原始图片相同的日期时间
jpegoptim -n terrain.jpg                    "-n"参数来模拟压缩，然后它会显示出压缩
jpegoptim -d ./compressed -m50 -p terrain.jpg   用50%质量压缩图片，"-m<质量>"选项，质量数范围0到100。(0是最好质量，100是最差质量)

　#一次压缩多张JPEG图像,并拥有与原始文件同样的修改日期
　for i in *.jpg; do jpegoptim -d ./compressed -p "$i"; done



QA:
error while loading shared libraries: libcommonTools.so: cannot open shared object file: No such file or directory
$ldd test       # 用于显示可执行文件所依赖的库
add ./lib to LD_LIBRARY_PATH variable in eclipse run configuration(Environment).
-Wl,-rpath=.        (rpath代表runtime path)不需要设置环境变量。这样做的坏处是，如果库文件移动位置，我们需要重新编译test

Q: warning: incompatible implicit declaration of built-in function ‘execl’ [enabled by default]
A: #include "necessary header file"
#include <unistd.h> --> execl()

Q: restrict
int ar[10];
int * restrict restar = (int *) malloc(10 * sizeof(int));
int * par = ar;
for(n=0; n < 10; n++)
{
par[n] += 5;
restart[n] += 5;
ar[n] *= 2;
par[n] += 3;
restar[n] += 3;
}
知道了restar是访问它所指向数据块的惟一初始方式，编译器就可以用具有同样效果的一条语句来代替包含restar的两个语句：
restar[n] += 8;
然而，将两个包含par的语句精简为一个语句将导致计算错误:
par[n] += 8;

void * memcpy(void * restrict dst, const void * restrict src, size_t n);
void * memmove(void * dst, const void * src, size_t n);
两个函数都从位置src把n个字节复制到dst中。函数memcpy()要求两个位置之间不重叠


Q: cast to pointer from integer of different size [-Wint-to-pointer-cast]
A: (char*)(argNum) --> &argNum
//  char* argList[] = {(char*)(argNum), configFile, fileID}; 需要的是一个char指正，int转char*有问题
char* argList[] = {&argNum, configFile, fileID};
其他：(void*)no，修改成&no



JPEG
http://libjpeg.sourceforge.net/
http://www.ijg.org/files/
Wrong JPEG library version: library is 90, caller expects 80



Usage: jpegoptim [options] <filenames> 

  -d<path>, --dest=<path>
                    specify alternative destination directory for 
                    optimized files (default is to overwrite originals)
  -f, --force       force optimization
  -h, --help        display this help and exit
  -m<quality>, --max=<quality>
                    set maximum image quality factor (disables lossless
                    optimization mode, which is by default on)
                    Valid quality values: 0 - 100
  -n, --noaction    不真正优化文件，仅仅打印优化的结果；don't really optimize files, just print results
  -S<size>, --size=<size>
                    尝试优化成指定大小的文件（KB或者是百分比）；Try to optimize file to given size (disables lossless
                    optimization mode). Target size is specified either in
                    kilo bytes (1 - n) or as percentage (1% - 99%)
  -T<threshold>, --threshold=<threshold>
                    如果低于门限值就保留原文件(百分比)；keep old file if the gain is below a threshold (%)
  -b, --csv         以CSV的格式打印处理信息；print progress info in CSV format
  -o, --overwrite   即使当目标文件存在也覆盖目标文件（只有当使用了-d选项才有效）；overwrite target file even if it exists (meaningful
                    only when used with -d, --dest option)
  -p, --preserve    保留文件的创建时间；preserve file timestamps
  -P, --preserve-perms
                    通过覆盖保留原始文件的访问权限；preserve original file permissions by overwriting it
  -q, --quiet       退出模式；quiet mode
  -t, --totals      处理所有文件之后打印出来；print totals after processing all files
  -v, --verbose     打印出详细信息；enable verbose mode (positively chatty)
  -V, --version     打印程序的版本；print program version

  -s, --strip-all   从输出文件剥离所有标记；strip all markers from output file
  --strip-none      不打任何标记；do not strip any markers
  --strip-com       除去输出文件的注释标记；strip Comment markers from output file
  --strip-exif      除去输出文件的Exif(在JPEG格式头部插入了数码照片的信息)标记；strip Exif markers from output file
  --strip-iptc      除去输出文件的IPTC/Photoshop (APP13)(可以将作者，版权，字幕，细节描述等元数据加入照片信息中)标记；strip IPTC/Photoshop (APP13) markers from output file
  --strip-icc       除去输出文件的ICC信息(某一彩色设备的色彩特性描述的文件)strip ICC profile markers from output file
  --strip-xmp       除去输出文件的XMP（照片编辑记录）信息；strip XMP markers markers from output file

  --all-normal      强制所有的输出文件成为非强制的（正常模式）；force all output files to be non-progressive
  --all-progressive 强制所有的文件成强制模式；force all output files to be progressive
  --stdout          以标准输出的形式发送输出（而不是输出一个文件）；send output to standard output (instead of a file)
  --stdin           以标准输入的形式读入（而不是从一个文件输入）read input from standard input (instead of a file)
  
C语言要求系统为每个程序 提供两个指针,这两个指针分别指向键盘和屏幕,并将这两个指针命名为:stdin和 stdout.
这两个指针就是所谓的标准输入和标准输出.此时,从键盘获取输入,向屏幕输出
stdin,stdout,stderr都是FILE*类型的对象，它们都是常量。分别指向键盘，显示器，显示器。
Ctrl+D结束输入

jpeg_start_compress做好准备后调用它进行图片的压缩（有损压缩）
jpeg_simple_progression 无损压缩


jpeg_read_header(&dinfo, TRUE);                 // 已经经过优化后的图像读不到头








安装OpenCV

sudo apt-get install build-essential cmake libgtk2.0-dev pkg-config python-dev python-numpy libavcodec-dev libavformat-dev libswscale-dev

cd release
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/home/ubuntu/opencv-2.4.9 ..
shell中的特殊变量：
变量名
含义
$0
shell或shell脚本的名字
$*
以一对双引号给出参数列表
$@
将各个参数分别加双引号返回
$#
参数的个数
$_
代表上一个命令的最后一个参数
$$
代表所在命令的PID
显示当前Shell的PID： echo $$
$!
代表最后执行的后台命令的PID
$?
代表上一个命令执行后的退出状态

echo $?
如果返回值是0，就是执行成功；如果是返回值是0以外的值，就是失败。





# 常用操作
查找大文件：
```shell
find . -type f -size +1M
```

并显示查找出来文件的具体大小：
```shell
find . -type f -size +1M  -print0 | xargs -0 du -h
```
将`find`的输出传送给另一个程序，并且正在搜索的文件可能包含换行符，应该考虑使用`-print0`，而不是`-print`。

排除多个目录(./data、./.git/)
```shell
find . ! -path "./.git/*" ! -path "./data/*" -type f -size +1M  -print0 | xargs -0 du -h | sort -nr
```
`sort -n` 根据字符串的数值（--numeric-sort）进行比较；
`sort -r` 反转(reverse)比较的结果（从大到小）。


# shell
$0 这个程式的执行名字
$n 这个程式的第n个参数值，n=1..9
$* 这个程式的所有参数,此选项参数可超过9个。
$# 这个程式的参数个数
$$ 这个程式的PID(脚本运行的当前进程ID号)
$! 执行上一个背景指令的PID(后台运行的最后一个进程的进程ID号)
$? 执行上一个指令的返回值 (显示最后命令的退出状态。0表示没有错误，其他任何值表明有错误)
$- 显示shell使用的当前选项，与set命令功能相同

显示最后修改的文件
ls -ltr | awk '{print $9}' | sed -n '$p'

按扩展名排序
ls -lX
ls --sort=extension

递归列出子目录
ls -R

增加/
ls -p

ls -li 打印每个文件的索引号

以数字的方式列出所有项的所有者和所有者（即UID合GID）
ls -n

只列出目录条目
ls -d */

ls -l --block-size=M

排序文件大小
ls -lhS 

stat ./hdfs.py

man -k logrotate

查看登录的用户：watch -n 1 who

命令行下快捷键
在单词之间跳转，使用Ctrl+左右键
Ctrl+a：把光标移到行首
Ctrl+e：把光标移到行尾
Ctrl+d：从Shell提示中注销并关闭，使用该快捷键就不必键入exit
Ctrl+u：删除光标至行首的所有字符
Ctrl+K：删除从光标到行末所有字符
ctrl+r:搜索之前打过的命令。会有一个提示，根据你输入的关键字进行搜索bash的history
esc+d: 删除光标后的一个词 
esc+f: 往右跳一个词 
esc+b: 往左跳一个词 
esc+t: 交换光标位置前的两个单词

在文件里查找
grep -rlI '\<main' .

快速新建文件：
cat >> filename.txt
按Ctrl+d结束

获得文件所有者
stat -c %U hdfs.py
Access : 文件最近一次被访问的时间
Modify:  文件内容最近一次被修改的时间
Change: 文件属性最近一次被改变的时间
修改Access,Modify
touch -d 1999-01-01 hdfs.py
touch -a hdfs.py    // 只将Access时间改为当前系统时间
touch -m hdfs.py    // 只将Modify时间改为当前系统时间

切割达大的tar.gz文件为几个小文件（每个1M），并还原
split -b 1m ./datasystem-server.tar.gz ./test3/
cat ./* > datasystem-server.tar.gz

列出所有支持的kill信号
kill -l

grep完整的单词
grep -w 'hdfs' hdfs.py
grep -w "hdfs" hdfs.py

得到hdfs.py中5到10行的文本(命令 < 文件"，这是将文件作为命令输入)
< hdfs.py sed -n '5,10p'

找出在./test1/目录中的所有空子目录
find ./test1/ -maxdepth 1 -type d -empty

打印history中最后的cat命令
!watch:p

打开vim并跳转到最后
vi + redis_demo.php

列出10个最大的系统中已打开的文件
lsof / | awk '{if($7 > 1048576) print $7/1048576 "MB "$9}' | sort -n -u | tail

显示所有用户
getent passwd

重复运行命令并显示它
watch ps -ef

history之后，运行指定编号的命令
!1033
运行上一个命令
!!

创建一个文件的备份
cp sql.txt{,.bak}

生成随机16进制数字，n是字符的个数
openssl rand -hex 15

打开ssh调试模式
ssh -vvv dongmin@10.19.19.23

同时创建多个目录
mkdir -p ./{test1,test2,test3}
mkdir {test9,test10}

获取文本的md5值
echo -n "text" | md5sum

用curl获取HTTP头
curl -l http://www.baidu.com
用curl获取HTTP状态值（200）:silent,location(重定向的话继续访问）;-w, --write-out <format>
curl -sL -w "%{http_code}\n" www.baidu.com -o /dev/null

指定行替换
sed -i '2056,2076 s/^/;/g' /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php_test.ini

显示包含某字符串的行号：cat -n php_test.ini | grep xdebug | awk '{print $1}'

连接数目
netstat -nat | grep 10.19.19.23:8200

找到该defunct僵尸进程的父进程，将该进程的父进程杀掉，则此defunct进程将自动消失。
   如何找到defunct僵尸进程的父进程？很简单，一句命令就够了：ps -ef | grep defunct_process_pid。

显示文件的绝对路径：realpath ./xdebug.so

把文件名的后四个字母变为 .wav：
for var in `ls`; do mv -f "$var" `echo "$var" |sed 's/....$/.wav/'`; done
反引号``是命令替换，命令替换是指Shell可以先执行``中的命令，将输出结果暂时保存，在适当的地方输出
....$       把最后四个字符替换成".wav"(以某个字符串开始  是用正则的 ^; 以某个字符串结束  是用正则的 $)

ps aux | grep serverMain | grep -v grep     (-v, --invert-match)

echo $?
如果返回值是0，就是执行成功；如果是返回值是0以外的值，就是失败。
当一个进程执行完毕时，该进程会调用一个名为 _exit 的例程来通知内核它已经做好“消亡”的准备了。该进程会提供一个退出码（一个整数）表明它准备退出的原因。按照惯例，0用来表示正常的或者说“成功”的终止。
$?
代表上一个命令执行后的退出状态
$0
shell或shell脚本的名字
$*
以一对双引号给出参数列表
$@
将各个参数分别加双引号返回
$#
参数的个数
$_
代表上一个命令的最后一个参数
$$
代表所在命令的PID
$!
代表最后执行的后台命令的PID


查看文件包含特定内容的行：more my.cnf | grep datadir

查看当前目录下所有文件的大小：du -h --max-depth=1

拷贝当前目录到系统剪切板：pwd | xsel （有回车）
显示先对路径的绝对路径：pwd ../../softwares/xclip-0.12
依赖：http://www.filewatcher.com/m/libXmu-1.0.1.tar.gz.43-0.html（configure: error: *** X11/Xmu/Atoms.h is missing ***）
/home/ubuntu/ap2/git/datasystem-server/tools/data


安装了ImageMagick
display [the path of your image]

按键Ctrl+V之后，进入Visual Block模式
y -> p

1) ls -lt  时间最近的在前面
2) ls -ltr 时间从前到后

cd -        返回上次操作的目录

awk '{printf "%-8s %-10s\n",$1,$4}' log.txt

查看某个进程文件的启动位置
ps -ef | grep nginx | grep fastdb
cd /proc/26425/
ls -al
exe -> /data/sdb/release/softwares/release/nginx-1.7.9/sbin/nginx



查看系统允许当前用户进程打开的文件数限制
ulimit -n

:1,$s/INSTALL_DIR/DESTDIR/g

查看本机IP地址：hostname -i

tar xvf software_fastdfs.tar
zxf: gzip, extract, fileName
zcf: *,       compress, fileName

grep -rn "debug" .

sed -n '/ruby/p' ab     #查询包括关键字ruby所在所有行
sed -n '/53ac2be3debeb950084f79b3fe7a5905.jpg/p' data_000001.json


统计一个文件的行数：
awk 'BEGIN{i=0} {i++} END {print i}' ./dong
统计输出的行数：末尾加上( wc -l) 

显示删除重复的行（只显示，文件内容不变）： awk '!x[$0]++' ./dong

匹配行首drwxr-xr-x、-rw-rw-r--
统计一个目录下的文件数目：ls -l /bin| grep ^- | wc -l
加递归：                ls -lR /usr | grep ^- | wc -l
统计目录个数（包括当前目录和上一级目录两个）： ls -l /bin | grep "^d" | wc -l
加递归：                ll -lR ./tmp | grep "^d" | wc -l
不包括当前目录和上一级目录： ls ./tmp | grep "^d" | wc -l
ls -R ./tmp | grep "^d" | wc -l

新建文件：cat >> test1
按ctrl+d退出


修改文件时间: touch -t 201801012359.59 log.log

查看服务器类型：
sudo apt-get install apache2-utils
ab https://www.zhihu.com/question/21904672

总核数 = 物理CPU个数 X 每颗物理CPU的核数 
总逻辑CPU数 = 物理CPU个数 X 每颗物理CPU的核数 X 超线程数
物理CPU个数：cat /proc/cpuinfo | grep "physical id"| sort | uniq | wc -l
核数：cat /proc/cpuinfo| grep "cpu cores"| uniq
逻辑CPU个数：cat /proc/cpuinfo| grep "processor" | wc -l

彻底的清空终端屏幕: reset
printf "\033c"      (printf "\x1Bc")

每cd到一个目录下就ls
cdl() {
    cd "${1}";
    ls;
}
alias cd=cdl
将上述内容添加到用户主目录中的.bashrc中即可。


ll -h

top输入u，输入用户名，查看指定用户的进程信息
切换：l(load average第一行), t(task 2,3), m(memory)
%Cpu(s):  0.9 us,  1.4 sy,  0.0 ni, 90.1 id,  7.6 wa,  0.0 hi,  0.0 si,  0.0 st
us: user(运行(未调整优先级的) 用户进程的CPU时间)
sy: system
niced: 运行已调整优先级的用户进程的CPU时间
wa: wait;
hard interrupt
soft interrupt
steal: 这个虚拟机被hypervisor偷去的CPU时间

PR: priority; rt表示这些进程运行在实时态

S(status)
D – 不可中断的睡眠态。
R – 运行态
S – 睡眠态
T – 被跟踪或已停止
Z – 僵尸态(zombie)

TIME+
任务启动后到现在所使用的全部CPU时间，精确到百分之一秒

A’: 切换交替显示模式
1.Def （默认字段组）
2.Job （任务字段组）
3.Mem （内存字段组）
4.Usr （用户字段组）
’a’移到后一个窗口，’w’移到前一个窗口,用’g’命令你可以输入一个数字来选择当前窗口
’d’(delay)或’s’时，你将被提示输入一个值（以秒为单位），它会以设置的值作为刷新间隔
‘f’: 字段管理(fields management)
    'd'选择该条目，'q'退出
R’: 反向排序
'c’(completion): 完整路径
‘i’(idle): 切换显示空闲任务
‘V’: 树视图(view)
z’: 切换彩色显示
n’ 或 ‘#’: 设置最大显示的任务数量
‘k’: 结束任务（默认杀死排在第一个的进程） +信号9
r’: 重新设置优先级(renice)

-b: 批处理模式（全部输出，可用于保存输出到文件中，也是3秒钟输出一次）

默认top启动配置
top -u wanghaidong -i
top -c
top -d  (delay)
top -n 3 (迭代3次退出）
top -p 0 (top自身的PID）




awk:样式扫描和处理语言
对数据分析并生成报告
awk就是把文件逐行的读入，以空格为默认分隔符将每行切片，切开的部分再进行各种分析处理

计算器：echo "obase=16; ibase=2; 111011" | bc
ibase用于设置输入数据的进制
obase用于输出的数据进制
obase=16
ibase=16
1E55F+B0225
CE784
设置精度： scale=4
(3.5+2.5)/3 + (3.55 + 25) / 2
16.2750
内置函数： sqrt(6.6)
定义函数: 
define dummy(x){
return(x * x);
}
dummy(9)

grep -rn "MagickPixelPacket"

du --max-depth=1 -h

apt-get install 下载的.deb安装包位于/var/cache/apt/archives


后台常驻任务： softwares/php-5.6.30/bin/php rawupload.php
crontab -e
*/1 * * * 1 /home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/rawupload.php
crontab -l -u wanghaidong   //列出用户jp的所有调度任务(crontab -l 列出所有)


sudo apt-get install galculator
nohup galculator &

echo "" >log.log
gg             ：光标移动到文件的第一行(常用)


nohup ./start.sh &
supervisor管理服务进程
后台运行： nohup ./serverMain >> /dev/null 2>&1      (no hang up)
/dev/null ：代表空设备文件
>  ：代表重定向到哪里，例如：echo "123" > /home/123.txt
1  ：表示stdout标准输出，系统默认值是1，所以">/dev/null"等同于"1>/dev/null"
2  ：表示stderr标准错误;   0:表示键盘输入(stdin)
&  ：表示等同于的意思，2>&1，表示2的输出重定向等同于1
&1的含义就可以理解为用标准输出的引用
http://blog.csdn.net/ggxiaobai/article/details/53507530


ps -ef|grep sslocal

https://aitanlu.com/ubuntu-shadowsocks-ke-hu-duan-pei-zhi.html
sudo sslocal -c /home/ubuntu/Shadowsocks.json -d start
sslocal -c /home/ubuntu/Shadowsocks.json

帐号信息如下：
server 地址：killwall.hobot.cc
port:808
加密方式：aes-256-cfb
密码：Pirate@139.162.13.77HOHO
linux命令行客户端的配置文件如下：
{
"server":"killwall.hobot.cc",
"server_port":808,
"local_port":1080,
"password":"Pirate@139.162.13.77HOHO",
"timeout":600,
"method":"aes-256-cfb"
}

监视指定进程名的进程
pidof serverMain | xargs top -bp

/proc/31538/cwd

ulimit -a           user limit
ulimit -c unlimited

查看指定文件的权限
ls -l test_upload.sh
ll test_upload.sh


grub>               http://man.linuxde.net/grub

root (hd0, 1)       Linux分区0x83 /boot目录所在的分区                                    内核所在的分区, root指定启动时的位置
kernel /boot/vmlinuz-2.6.15-26-386 ro dev=/dev/hda3(cat /sbin/init, /所在分区)          加载Linux内核  root=指定挂载根分区的位置,即指定根目录
initrd /boot/initrd.img-2.6.16-26-386                                                   INITial Ram Disk 在内存中构造一个“虚拟”的根文件系统
boot

ext的分区ID号：0x83　　　
swap的分区ID号：0x82


sudo blkid
du -s note/         disk usage
df -h                   disk free
lsblk
vmstat
sar -r              内存使用
mpstat              cpu
iostat              io
dmesg               开机信息    diagnostic message
uname -a
arch

计算器：
let a=23**2

查看指定进程名的信息
pgrep java | xargs top -bp

查找文件并归档
ls fileID_fullPath.txt | xargs tar cvzf output.tar.gz

从文本文件中查找指定字符串
cat fileID_fullPath.txt | grep "terrain"

重新进入当前目录(刷新当前目录中的文件) 
cd .

 Cannot find color scheme 'solarized'
 进入~/.vim/bundle
 执行git clone https://github.com/altercation/vim-colors-solarized
 
查看并杀死进程
pgrep server
kill 3200

http://marketplace.eclipse.org/content/shelled

.tar.gz     格式解压为          tar   -zxvf   xx.tar.gz  
.tar.bz2   格式解压为          tar   -jxvf    xx.tar.bz2






linux运维常用命令

1、linux启动过程
开启电源 --> BIOS开机自检 --> 引导程序lilo或grub --> 内核的引导（kernel boot）--> 执行init（rc.sysinit、rc）--> mingetty(建立终端) --> Shell

2、网卡绑定多ip
# ifconfig eth0:1 192.168.1.99 netmask 255.255.255.0

3、设置DNS、网关
# echo "nameserver 202.16.53.68" >> /etc/resolv.conf
# route add default gw 192.168.1.1

4、弹出、收回光驱
# eject
# eject -t

5、用date查询昨天的日期
# date --date=yesterday

6、查询file1里面空行的所在行号
# grep ^$ file

7、查询file1以abc结尾的行
# grep abc$ file1

8、打印出file1文件第1到第三行
# head -3 file1
# sed -n '1,3p' file1

9、清空文件
# > 1.txt
# true > 1.txt
# echo "" > 1.txt
# cat /dev/null > 1.txt

10、删除所有空目录
# find /data -type d -empty -exec rm -rf {} ;

11、linux下批量删除空文件（大小等于0的文件）的方法
# find /data -type f -size 0c -exec rm -rf {} ;
# find /data -type f -size 0c|xargs rm –f

12、删除五天前的文件
# find /data -mtime +5 -type f -exec rm -rf {} ;

13、删除两个文件重复的部份，打印其它
# cat 1.txt 3.txt |sort |uniq

14、攻取远程服务器主机名
# echo `ssh $IP cat /etc/sysconfig/network|awk -F = '/hostname/ {print $2}'`

15、实时监控网卡流量（安装iftop）
# /usr/local/iftop/sbin/iftop -i eth1 -n

16、查看系统版本((Linux Standard Base))
# lsb_release -a

17、强制踢出登陆用户
# pkill -kill -t pts/1

18、tar增理备份、还原
# tar -g king -zcvf kerry_full.tar.gz kerry
# tar -g king -zcvf kerry_diff_1.tar.gz kerry
# tar -g king -zcvf kerry_diff_2.tar.gz kerry
# tar -zxvf kerry_full.tar.gz
# tar -zxvf kerry_diff_1.tar.gz
# tar -zxvf kerry_diff_2.tar.gz

19、将本地80端口的请求转发到8080端口，当前主机外网IP为202.96.85.46
-A PREROUTING -d 202.96.85.46 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.9.10:8080

20、在11月份内，每天的早上6点到12点中，每隔2小时执行一次/usr/bin/httpd.sh
# crontab -e
0 6-12/2 * 11 * /usr/bin/httpd.sh

21、查看占用端口8080的进程
netstat -lnpt | grep 8080   (--listening|-l; program PID and name; tcp)
-l: 仅仅显示正在监听的套接字
-n: numeric 显示数字化的地址，而不是符号主机地址、端口或者用户名
-p, -program
	显示每个套接字所属的程序ID和名字。
-t, --tcp
# netstat -tnlp | grep 8080
lsof -i:8080

22、在Shell环境下,如何查看远程Linux系统运行了多少时间?
# ssh user@被监控主机ip "uptime"

23、查看CPU使用情况的命令
每5秒刷新一次，最右侧有CPU的占用率的数据
# vmstat 5
 
top 然后按Shift+P，按照进程处理器占用率排序
# top

top 然后按Shift+M, 按照进程内存占用率排序
# top

24、查看内存使用情况的命令

用free命令查看内存使用情况
# free -m

 25、查看磁盘i/o
用iostat查看磁盘/dev/sdc3的磁盘i/o情况，每两秒刷新一次
# iostat -d -x /dev/sdc3 2

26、修复文件系统
# fsck –yt ext3 /
-t 指定文件系统
-y 对发现的问题自动回答yes

 27、read 命令5秒后自动退出
# read -t 5 

28、grep -E -P 是什么意思
-E, --extended-regexp 采用扩展正规表达式。
-P，--perl-regexp 采用perl正规表达式

29、vi编辑器(涉及到修改，添加，查找)
插入(insert)模式

i　　　　 光标前插入
I　　　　 光标行首插入
a　　　　 光标后插入
A　　　　 光标行尾插入
o　　　　 光标所在行下插入一行，行首插入
O　　　　 光标所在行上插入一行，行首插入
G　　　　 移至最后一行行首
nG　　　　移至第n行行首
n+　　　　下移n行，行首
n-　　　　上移n行，行首
:/str/　　　　　　　　　　从当前往右移动到有str的地方
:?str?　　　　　　　　　　从当前往左移动到有str的地方
:s/str1/str2/　　　　　 　将找到的第一个str1替换为str2　　
:s/str2/str2/g　　　　　　将当前行找到的所有str1替换为str2
:n1,n2s/str1/str2/g　　　 将从n1行至n2行找到的所有的str1替换为str2
:1,.s/str1/str2/g　　　　 将从第1行至当前行的所有str1替换为str2
:.,$s/str1/str2/g　　　　 将从当前行至最后一行的所有str1替换为str2

30、linux服务器之间相互复制文件
copy 本地文件1.sh到远程192.168.9.10服务器的/data/目录下
# scp /etc/1.sh king@192.168.9.10:/data/ 
copy远程192.168.9.10服务器/data/2.sh文件到本地/data/目录
# scp king@192.168.9.10:/data/2.sh /data/

31、使用sed命令把test.txt文件的第23行的TEST换成TSET.
# sed -i '23s/TEST/TSET/' test.txt
# sed -i '23 s/TEST/TSET/' test.txt

32、使history命令能显示时间
# export HISTTIMEFORMAT="%F %T "

33、如何查看目标主机192.168.0.1开放那些端口
# nmap -ps 192.168.0.1

34、如何查看网络连接
# netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'

35、如何查看当前系统使用了那些库文件
# ldconfig -v

36、如何查看网卡的驱动版本
# ethtool -i eth0

37、使用tcpdump来监视主机192.168.0.1的tcp的80端口
# tcpdump tcp port 80 host 192.168.0.1

38、 如何看其它用户的邮件列表
# mial -u king

39、对大文件进行切割
按每个文件1000行来分割
# split -l 1000 httperr8007.log httperr

按照每个文件5m来分割
# split -b 5m httperr8007.log httperr

40、合并文件
取出两个文件的并集(重复的行只保留一份)
# cat file1 file2 | sort | uniq

取出两个文件的交集(只留下同时存在于两个文件中的文件)
# cat file1 file2 | sort | uniq -d

删除交集，留下其他的行
# cat file1 file2 | sort | uniq –u
41、打印文本模式下运行的服务

# chkconfig --list|awk '$5~/on/{print $1,$5}'
42、删除0字节文件

# find -type f -size 0 -exec rm -rf {} ;
43、查看进程，按内存从大到小排列

# ps -e  -o "%C  : %p : %z : %a"|sort -k5 -nr
44、查看http的并发请求数及其TCP连接状态

# netstat -n | awk '/^tcp/ {++S[$NF]} END {for(a in S) print a, S[a]}'
45、获取IP地址

# ifconfig eth0|sed -n '2p'|awk '{print $2}'|cut -c 6-30

perl实现获取IP地址：
# ifconfig -a | perl -ne 'if ( m/^s*inet (?:addr:)?([d.]+).*?cast/ ) { print qq($1n); exit 0; }'

46、获取内存大小
# free -m |grep "Mem" | awk '{print $2}'

47、查看CPU核心数
# cat /proc/cpuinfo |grep -c processor

48、查看磁盘使用情况
# df -h

49、查看有多少个活动的PHP-cgi进程
# netstat -anp | grep php-cgi | grep ^tcp | wc -l

50、查看硬件制造商
# dmidecode -s system-product-name









命令缩写：
ls：list(列出目录内容)
cd：Change Directory（改变目录）
su:switch user 切换用户
rpm:redhat package manager 红帽子打包管理器
pwd:print work directory 打印当前目录 显示出当前工作目录的绝对路径
ps: process status(进程状态，类似于windows的任务管理器) 常用参数：－auxf
ps -auxf 显示进程状态
df: disk free 其功能是显示磁盘可用空间数目信息及空间结点信息。换句话说，就是报告在任何安装的设备或目录中，还剩多少自由的空间。
rpm： 即RedHat Package Management，是RedHat的发明之一
rmdir：Remove Directory（删除目录）
rm：Remove（删除目录或文件）
cat: concatenate连锁 cat file1 file2>>file3把文件1和文件2的内容联合起来放到file3中
insmod: install module,载入模块
ln -s : link -soft 创建一个软链接，相当于创建一个快捷方式
mkdir：Make Directory(创建目录
touch
man: Manual
pwd：Print working directory
su：Swith user
cd：Change directory
ls：List files
ps：Process Status
mkdir：Make directory
rmdir：Remove directory
mkfs: Make file system
fsck：File system check
cat: Concatenate
uname: Unix name
df: Disk free
du: Disk usage
lsmod: List modules
mv: Move file
rm: Remove file
cp: Copy file
ln: Link files
fg: Foreground
bg: Background
chown: Change owner
chgrp: Change group
chmod: Change mode
umount: Unmount
dd: 本来应根据其功能描述“Convert an copy”命名为“cc”，但“cc”已经被用以代表“C Complier”，所以命名为“dd”
tar：Tape archive
ldd：List dynamic dependencies
insmod：Install module
rmmod：Remove module
lsmod：List module
文件结尾的"rc"（如.bashrc、.xinitrc等）：Resource configuration
Knnxxx / Snnxxx（位于rcx.d目录下）：K（Kill）；S(Service)；nn（执行顺序号）；xxx（服务标识）
.a（扩展名a）：Archive，static library
.so（扩展名so）：Shared object，dynamically linked library
.o（扩展名o）：Object file，complied result of C/C++ source file
RPM：Red hat package manager
dpkg：Debian package manager
apt：Advanced package tool（Debian或基于Debian的发行版中提供）
部分Linux命令缩
bin = BINaries #下面的是一些二进制程序文件
/dev = DEVices  #下面的是一些硬件驱动
/etc = ETCetera #目录存放着各种系统配置文件, 类似于windows下的system
/lib = LIBrary
/proc = PROCesses
/sbin = Superuser BINaries
/tmp = TeMPorary
/usr = Unix Shared Resources 
/var = VARiable ?
/boot=boot #下面的是开机启动文件
FIFO = First In, First Out
GRUB = GRand Unified Bootloader
IFS = Internal Field Seperators
LILO = LInux LOader
MySQL = My是最初作者女儿的名字，SQL = Structured Query Language
PHP = Personal Home Page Tools = PHP Hypertext Preprocessor
PS = Prompt String
Perl = "Pratical Extraction and Report Language" = "Pathologically Eclectic Rubbish Lister"
Python 得名于电视剧Monty Python's Flying Circus
Tcl = Tool Command Language
Tk = ToolKit
VT = Video Terminal
YaST = Yet Another Setup Tool
apache = "a patchy" server
apt = Advanced Packaging Tool
ar = archiver
as = assembler
awk = "Aho Weiberger and Kernighan" 三个作者的姓的第一个字母
bash = Bourne Again SHell
bc = Basic (Better) Calculator
bg = BackGround
biff = 作者Heidi Stettner在U.C.Berkely养的一条狗,喜欢对邮递员汪汪叫。
cal = CALendar
cat = CATenate
cd = Change Directory
chgrp = CHange GRouP
chmod = CHange MODe
chown = CHange OWNer
chsh = CHange SHell
cmp = compare
cobra = Common Object Request Broker Architecture
comm = common
cp = CoPy
cpio = CoPy In and Out
cpp = C Pre Processor
cron = Chronos 希腊文时间
cups = Common Unix Printing System
cvs = Current Version System
daemon = Disk And Execution MONitor
dc = Desk Calculator
dd = Disk Dump
df = Disk Free
diff = DIFFerence
dmesg = diagnostic message
du = Disk Usage
ed = editor
egrep = Extended GREP
elf = Extensible Linking Format
elm = ELectronic Mail
emacs = Editor MACroS
eval = EVALuate
ex = EXtended
exec = EXECute
fd = file descriptors
fg = ForeGround
fgrep = Fixed GREP
fmt = format
fsck = File System ChecK
fstab = FileSystem TABle
fvwm = F*** Virtual Window Manager
gawk = GNU AWK
gpg = GNU Privacy Guard
groff = GNU troff
hal = Hardware Abstraction Layer
joe = Joe's Own Editor
ksh = Korn SHell
lame = Lame Ain't an MP3 Encoder
lex = LEXical analyser
lisp = LISt Processing = Lots of Irritating Superfluous Parentheses
ln = LiNk
lpr = Line PRint
ls = list
lsof = LiSt Open Files
m4 = Macro processor Version 4
man = MANual pages
mawk = Mike Brennan's AWK
mc = Midnight Commander
mkfs = MaKe FileSystem
mknod = MaKe NODe
motd = Message of The Day
mozilla = MOsaic GodZILLa
mtab = Mount TABle
mv = MoVe
nano = Nano's ANOther editor
nawk = New AWK
nl = Number of Lines
nm = names
nohup = No HangUP
nroff = New ROFF
od = Octal Dump
passwd = PASSWorD
pg = pager
pico = PIne's message COmposition editor
pine = "Program for Internet News & Email" = "Pine is not Elm"
ping = 拟声 又 = Packet InterNet Grouper
pirntcap = PRINTer CAPability
popd = POP Directory
pr = pre
printf = PRINT Formatted
ps = Processes Status
pty = pseudo tty
pushd = PUSH Directory
pwd = Print Working Directory
rc = runcom = run command, rc还是plan9的shell
rev = REVerse
rm = ReMove
rn = Read News
roff = RunOFF
rpm = RPM Package Manager = RedHat Package Manager
rsh, rlogin, rvim中的r = Remote
rxvt = ouR XVT
seamoneky = 我
sed = Stream EDitor
seq = SEQuence
shar = SHell ARchive
slrn = S-Lang rn
ssh = Secure SHell
ssl = Secure Sockets Layer
stty = Set TTY
su = Substitute User
svn = SubVersioN
tar = Tape ARchive
tcsh = TENEX C shell
tee = T (T形水管接口)
telnet = TEminaL over Network
termcap = terminal capability
terminfo = terminal information
tex = τέχνη的缩写，希腊文art
tr = traslate
troff = Typesetter new ROFF
tsort = Topological SORT
tty = TeleTypewriter
twm = Tom's Window Manager
tz = TimeZone
udev = Userspace DEV
ulimit = User's LIMIT
umask = User's MASK
uniq = UNIQue
vi = VIsual = Very Inconvenient
vim = Vi IMproved
wall = write all
wc = Word Count
wine = WINE Is Not an Emulator
xargs = eXtended ARGuments
xdm = X Display Manager
xlfd = X Logical Font Description
xmms = X Multimedia System
xrdb = X Resources DataBase
xwd = X Window Dump
yacc = yet another compiler compiler
Fish = the Friendly Interactive SHell
su = Switch User
MIME = Multipurpose Internet Mail Extensions
ECMA = European Computer Manufacturers Association










